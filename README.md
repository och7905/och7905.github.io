# och7905.github.io

GitHub Pages 루트 도메인(`https://och7905.github.io`) 접속 시 실제 포트폴리오 웹사이트로 자동 연결(Redirect)해 주는 랜딩 저장소입니다.

---

## 📌 프로젝트 개요

- **도메인**: `https://och7905.github.io/`
- **목적지 (Target URL)**: `https://och7905.github.io/Personal_Website_Deployment/`
- **주요 역할**: 
  - 사용자 도메인 루트 접속자를 실제 포트폴리오 배포 프로젝트로 즉시 자동 리다이렉트
  - 검색엔진(네이버, 구글 등) 최적화(SEO) 및 크롤링 허용 설정
  - 네이버 웹마스터 도구(서치어드바이저) 소유 확인 메타 태그 지원

---

## 📂 파일 구조 및 역할

```text
och7905.github.io/
├── index.html        # 루트 진입 시 즉시 리다이렉트 및 네이버 사이트 인증
├── robots.txt        # 검색 로봇 크롤링 허용 및 사이트맵 위치 안내
├── sitemap.xml       # 검색엔진 색인 등록용 사이트맵
└── README.md         # 프로젝트 안내 및 코드 설명 문서
```

---

## 🔍 파일별 상세 설명

### 1. `index.html` (메인 리다이렉트 페이지)
- **네이버 사이트 소유확인**:
  ```html
  <meta name="naver-site-verification" content="92fc915bd496871b0e06d49251757ce1f7b1936f" />
  ```
  네이버 서치어드바이저 등록을 위한 메타 태그입니다.
- **메타 새로고침(Meta Refresh) 리다이렉트**:
  ```html
  <meta http-equiv="refresh" content="0; url=https://och7905.github.io/Personal_Website_Deployment/" />
  ```
  방문자가 루트 도메인에 접속하면 0초 대기(즉시) 후 실제 포트폴리오 웹사이트(`Personal_Website_Deployment`)로 페이지를 이동시킵니다.
- **대체 링크(Fallback)**:
  ```html
  <p><a href="https://och7905.github.io/Personal_Website_Deployment/">포트폴리오로 이동 중...</a></p>
  ```
  브라우저 설정으로 자동 리다이렉트가 차단되거나 지연될 경우 사용자가 직접 클릭하여 이동할 수 있는 링크를 제공합니다.

---

### 2. `robots.txt` (검색 로봇 크롤링 제어)
```txt
User-agent: *
Allow: /

Sitemap: https://och7905.github.io/sitemap.xml
```
- 모든 검색엔진 로봇(`User-agent: *`)의 전체 경로 크롤링을 허용합니다(`Allow: /`).
- 검색엔진이 페이지 목록을 수집할 수 있도록 사이트맵(`sitemap.xml`)의 절대 URL 경로를 명시하고 있습니다.

---

### 3. `sitemap.xml` (사이트맵)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://och7905.github.io/Personal_Website_Deployment/</loc>
    <lastmod>2026-10-27</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```
- 검색엔진 색인 대상 URL(`loc`)로 실제 포트폴리오 경로를 지정했습니다.
- 갱신 주기(`changefreq: weekly`)와 우선순위(`priority: 1.0`)를 설정하여 검색엔진에 알립니다.

---

## ⚙️ 유지보수 가이드

- **포트폴리오 배포 주소가 변경되는 경우**:
  - `index.html` 내 `<meta http-equiv="refresh">`의 `url` 값과 `<a>` 태그 링크를 새 주소로 수정합니다.
  - `sitemap.xml` 내 `<loc>` 태그의 URL을 새 주소로 수정하고 `<lastmod>` 날짜를 업데이트합니다.
- **네이버 서치어드바이저 재인증이 필요한 경우**:
  - `index.html`의 `<meta name="naver-site-verification">` 태그 내용을 새로 발급받은 키 값으로 교체합니다.
