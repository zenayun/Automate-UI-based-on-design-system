# IBM Carbon Design System — Login Page

> Figma 파일을 AI가 자동 크롤링·분석하여 구현한 로그인 UI

🔗 **라이브 데모:** https://zenayun.github.io/Automate-UI-based-on-design-system/

---

## 구현 기능

| 기능 | 설명 |
|------|------|
| 🔐 이메일 로그인 | 유효성 검사 + 인라인 에러 처리 |
| 🟢 네이버 OAuth | 네이버 공식 브랜드 색상 적용 |
| 📝 이메일 회원가입 | 비밀번호 강도 미터 + 약관 동의 |
| 🔑 비밀번호 재설정 | 3단계 플로우 (이메일 → 인증코드 → 완료) |
| 📱 반응형 | 데스크탑 2컬럼 / 모바일 단일 컬럼 |

---

## Figma → 구현 정확도 분석

> IBM Carbon Design System Figma 파일(`FhmcOsy7SQ7fCsJ89SrsSO`)에서 37개 컴포넌트를 자동 크롤링하여 구현 후, JSON 실측값과 1:1 비교 분석

### 종합 점수

```
██████████████████████░░  81.6 / 100
```

### 항목별 점수

| 항목 | 점수 | 상세 |
|------|:----:|------|
| 🎨 Color Tokens | **100 / 100** | 31개 토큰 완벽 일치 (`#0f62fe`, `#161616` 등) |
| 📐 Spacing | **95 / 100** | 2px~96px 값 전체 일치, 토큰 네이밍 형식 차이 |
| 🖊 Text Input | **88 / 100** | 높이·border·focus 일치, warning 상태 미구현 |
| ☑️ Checkbox | **80 / 100** | 크기·border 일치, checked 배경색 오차 |
| 🗔 Modal | **82 / 100** | 구조·오버레이 일치, 배경색 오차 |
| 🔤 Typography | **72 / 100** | IBM Plex Sans 적용, line-height 절대값 미정의 |
| 🔘 Button | **71 / 100** | Primary 완전 일치, Secondary 미구현 |
| 🔔 Notification | **65 / 100** | border-left 구조 일치, Light/Dark 테마 색상 차이 |

### 주요 발견사항

**✅ 완벽히 일치한 항목**
- Carbon White Theme 색상 토큰 31개 (`--cds-interactive: #0f62fe` 등)
- Spacing 토큰 12개 픽셀값 (2px · 4px · 8px · 12px · 16px · 24px · 32px · 40px · 48px · 64px · 80px · 96px)
- Text Input 높이 40px, border-bottom 1px solid `#8d8d8d`, focus outline 2px `#0f62fe`
- Modal 오버레이 `rgba(22,22,22,0.5)`, 닫기 버튼 40×40px

**⚠️ 수정 필요 항목**
- Checkbox checked 배경: `#161616` → `#0f62fe` (interactive 토큰)
- Button 우측 패딩: 32px → 16px
- Modal 배경: `#ffffff` → `#f4f4f4` (layer-01)
- Ghost 버튼 hover: `rgba(15,98,254,.1)` → `#e8e8e8`
- Notification border 색상: Light theme 기준 재조정 필요

---

## 자동화 프로세스

```
Figma API 크롤링
      │
      ▼
37개 컴포넌트 JSON 파싱
(Button, Input, Modal, Checkbox 등)
      │
      ▼
색상·크기·상태값 추출
      │
      ▼
HTML/CSS 구현
      │
      ▼
Figma 실측값 vs 구현값 비교
      │
      ▼
정확도 수치화 (81.6/100)
```

## 사용된 Carbon 컴포넌트

`Button` `Text Input` `Checkbox` `Modal` `Notification` `Link` `Tag` `Tooltip`

## 기술 스택

- **Design System:** IBM Carbon Design System (White Theme)
- **Font:** IBM Plex Sans KR / IBM Plex Sans
- **구현:** Vanilla HTML · CSS · JavaScript (빌드 도구 없음)
- **분석:** Figma REST API + Python 파싱

---

*이 프로젝트는 Figma 디자인 파일을 AI가 자동으로 분석하여 구현하는 워크플로우 실험입니다.*
