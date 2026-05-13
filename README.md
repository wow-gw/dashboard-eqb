# 🛍️ EQQUALBERRY × TikTok Shop US — Operations Dashboard

> TikTok Shop US 운영 현황을 실시간으로 모니터링하는 내부 대시보드입니다.  
> Google Apps Script → Google Sheets → HTML Dashboard 구조로 데이터를 연동합니다.

---

## 📸 Overview

| 탭 | 설명 |
|---|---|
| Overview | GMV·주문·AOV·ROI·CVR 종합 현황 |
| Products & Orders | 제품별 매출 브레이크다운 |
| Funnel | 페이지뷰 → 구매 전환 퍼널 |
| P&L | 추정 손익 계산 |
| Sample Tracking | 크리에이터 샘플 발송 현황 |
| Video Tracking | 포스팅된 전체 영상 현황 |
| Ad Performance | GMV MAX 캠페인 성과 |
| Ad Creatives | 영상별 광고 크리에이티브 성과 |

---

## 🏗️ 아키텍처

```
TikTok Shop API
      ↓
  MySQL DB (boosters)
      ↓
회사 Google Sheets (공유 드라이브)
      ↓  IMPORTRANGE
개인 Gmail Sheets (공개)
      ↓  Apps Script API
  index.html (대시보드)
```

---

## 📁 파일 구조

```
eqb-dashboard/
├── index.html           # 메인 대시보드
├── dashboard_guide.md   # 팀원용 사용 가이드
└── README.md            # 프로젝트 설명 (이 파일)
```

---

## ⚙️ 기술 스택

- **Frontend**: Vanilla HTML / CSS / JavaScript
- **Charts**: Chart.js 4.4.1
- **Fonts**: Inter, Pretendard
- **Data**: Google Apps Script (REST API)
- **Hosting**: Netlify → Google Sites embed

---

## 🔗 연동 정보

| 항목 | 값 |
|---|---|
| Apps Script URL | `https://script.google.com/macros/s/AKfycb...` |
| Token | `eqb-dashboard-2026` |
| Spreadsheet ID | `1hUzHXKCVjKP9dzhpuXW1JMYuYU-1aocVkHI-lIvBvfo` |

---

## 📊 연동 시트 목록

| Action | 시트명 | 설명 |
|---|---|---|
| `daily` | Daily_GMV | 일자별 GMV·주문·방문자 |
| `orders` | Orders by Product | 제품별 주문 내역 |
| `sample` | Sample | 샘플 발송 현황 |
| `fx` | FX_Rates | USD/KRW 환율 |
| `upload` | Video_Upload_Daily | 일자별 영상 업로드 수 |
| `gmvmax` | GMV MAX | GMV MAX 캠페인 |
| `video` | GMV MAX_Video | 영상별 광고 성과 |
| `kpi` | KPI | 월별 KPI 목표치 |
| `gmvtype` | GMV_Type | GMV 소스별 분류 |
| `pl` | P&L | 비용 비율·단가 |
| `allvideos` | All_Videos_Uploaded | 전체 업로드 영상 목록 |

---

## 🎨 디자인 시스템

| 구분 | 색상 | 용도 |
|---|---|---|
| Brand Black | `#1C1C1C` | 사이드바 배경 |
| Active Orange | `#FF5C35` | 포인트 컬러, 활성 탭 |
| Surface Gray | `#F5F6F7` | 메인 배경 |
| Border | `#E0E2E5` | 테두리, 입력창 |
| Vitamin | `#d97706` | Vitamin 라인 (amber) |
| NAD+ | `#db2777` | NAD+ 라인 (pink) |
| Bakuchiol | `#7c3aed` | Bakuchiol 라인 (purple) |

---

## ⚠️ 유의사항

- 데이터는 **미국 현지시간(PST) 기준 하루 전** 데이터까지 반영됩니다.
- TikTok Shop API 기반으로 셀러센터 어드민과 수치 차이가 발생할 수 있습니다.
  - 날짜 집계 기준 차이 (주문일 vs 정산일)
  - 광고 계정 범위 차이 (단일 계정 vs 전체 계정 합산)
  - 취소·환불 처리 시점 차이
- P&L 수치는 **비율·단가 기반 추정치**이며 정확한 회계 수치가 아닙니다.

---

## 🚀 로컬 실행

별도 서버 불필요 — `index.html` 을 브라우저로 열면 되지만,  
CORS 정책으로 인해 **Netlify 또는 서버 환경에서 실행**해야 데이터가 정상 로드됩니다.

```bash
# Netlify CLI로 로컬 실행 (선택사항)
npx netlify dev
```

---

## 👥 팀

- **운영**: EQQUALBERRY TikTok Shop US Team
- **개발**: 내부 운영 도구 (Internal Tool)

---

*Last updated: May 2026*
