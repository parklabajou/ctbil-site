# CTBiL 연구실 웹사이트 관리 안내서

**Cell Therapy & Bioinformatics Lab · 아주대학교 분자과학기술학과 (박현지 교수님 연구실)**

이 저장소는 연구실 웹사이트의 소스입니다. 이 문서는 **개발 지식이 없어도** 논문·뉴스·사진을 직접 추가·수정할 수 있도록 안내합니다. 웹페이지는 GitHub Pages로 호스팅되고, 구글 사이트(ctbi.ajou.ac.kr)에 임베드되어 보여집니다.

---

## 🗂 사이트 구성

| 파일 | 페이지 | 설명 |
|------|--------|------|
| `index.html` | 대문(홈) | 히어로(단체사진 배경) · 연구 소개 · 최근 논문/뉴스(자동) · 채용 배너 |
| `team.html` | 팀 | PI 프로필 + 구성원 카드 |
| `research.html` | 연구 | 연구 주제 5개 영역 |
| `publications.html` | 논문 | 연도별 논문 목록 (필터 · 배지) |
| `patents.html` | 특허 | 특허 목록 (등록/출원 배지) |
| `news.html` | 뉴스 | 날짜순 타임라인 (태그 색상 구분) |
| `gallery.html` | 갤러리 | 사진 그리드 + 클릭 확대 |
| `contact.html` | 연락처 | 주소 · 지도 · 채용 안내 |
| `설정가이드.html` | — | GitHub Pages · 구글 사이트 임베드 설정 안내 |
| `images/` | — | 사진(팀·갤러리·뉴스)을 올리는 폴더 |

> **색상**: 아주대 공식 블루(`#0072CE`) + 골드(`#B08D3C`) · **폰트**: Space Grotesk + Inter

---

## ✏️ 수정하는 법 (기본 원리)

각 페이지 파일에는 **`▼▼▼ 여기만 수정하세요 ▼▼▼`** 로 표시된 구간이 있습니다. 그 안의 **글자만** 바꾸면 됩니다. 디자인 코드는 건드릴 필요가 없어요.

- 새 항목은 기존 `<article> ... </article>` 블록 **하나를 통째로 복사** → 맨 위에 붙여넣기 → 글자만 교체
- **따옴표·쉼표 신경 안 써도 됩니다.** 칸을 비워둬도 페이지는 깨지지 않아요.

---

## 📄 논문 추가하기 (`publications.html`)

`▼▼▼ 논문 목록 ▼▼▼` 아래에 이 블록을 복사해 **맨 위**에 붙여넣고 내용만 바꾸세요.

```html
<article year="2026" tags="Co-first">
  <p class="abbr">Nat. Comm.</p>
  <p class="authors">홍길동*, ... <b>Park HJ&dagger;</b></p>
  <p class="title">여기에 논문 제목을 적습니다</p>
  <p class="journal">Nature Communications 2026, 17:1234</p>
  <p class="link">https://doi.org/논문주소</p>
</article>
```

- `year="2026"` — 연도 (심사 중이면 `year="Submitted"`)
- `tags="Co-first"` — 배지 (쉼표로 여러 개, 없으면 `tags=""`)
- `abbr` — 썸네일 저널 약칭 (짧게)
- `authors` — 저자. 본인/랩은 `<b>Park HJ</b>` 처럼 진하게. 공동1저자 `*`, 교신저자 `&dagger;`
- `title` — 논문 제목
- `journal` — 저널명·권·호·페이지
- `link` — 논문/DOI 주소 (없으면 비워두기 → DOI 버튼이 안 보임)
- `abbr` — 지금은 화면에 **표시되지 않습니다**(썸네일 제거). 비워둬도 되고, 그대로 둬도 무방합니다.

> 💡 **대문 자동 반영**: 대문(홈)의 "Recent Publications"는 이 파일에서 **가장 최근 발행 논문 3편**을 자동으로 불러옵니다. `year="Submitted"`(심사중)는 대문에서는 제외됩니다. 새 논문을 **맨 위**에 추가하면 대문도 자동으로 바뀌므로 `index.html`은 따로 고칠 필요가 없습니다.

---

## 📰 뉴스 추가하기 (`news.html`)

`▼▼▼ 뉴스 목록 ▼▼▼` 아래에 복사해 **맨 위**에 붙여넣으세요.

```html
<article date="2026.08.17" type="award" label="Award">
  <p class="txt">여기에 소식 본문을 적습니다. 강조는 &lt;b&gt;이름&lt;/b&gt; 처럼, 링크는 &lt;a href="주소"&gt;Link&lt;/a&gt; 로.</p>
  <p class="imgs">images/사진1.jpg
images/사진2.jpg</p>
</article>
```

- `date` — 날짜 (예: `2026.08.17`)
- `type` — 태그 색상: `award`(수상·금) / `talk`(발표·파랑) / `career`(진로·초록) / `grant`(연구비·보라) / `event`(행사·청록) / `paper`(논문·남색)
- `label` — 태그에 보일 글자 (예: `Award`, `Career`, `Scholarship`)
- `txt` — 소식 본문 (여러 문장 가능)
- `imgs` — 사진 주소들. 여러 장이면 **줄바꿈 또는 공백**으로 나열, 없으면 비워두기. 예: `images/isscr2026.jpg`

> 💡 **대문 자동 반영**: 대문(홈)의 "Latest News"는 이 파일의 **가장 최근 소식 3개**를 자동으로 불러옵니다. 새 소식을 **맨 위**에 추가하면 대문도 자동으로 바뀝니다.

---

## 🖼 갤러리 사진 추가하기 (`gallery.html`)

1. `images/` 폴더에 사진 파일을 올립니다. (아래 "사진 올리기" 참고)
2. `▼▼▼ 갤러리 사진 ▼▼▼` 목록에서 아래처럼 한 줄 추가:

```js
{ src:"images/lab_dinner.jpg", cap:"Lab dinner, 2026" },
```

- `src` — 사진 주소, `cap` — 사진 아래 설명
- 지금 들어있는 `ph(...)` 는 미리보기용 임시 그림이니, 실제 사진 주소로 바꾸면 됩니다.

---

## 👥 팀원 추가하기 (`team.html`)

`▼▼▼ 구성원 ▼▼▼` 아래에서 `<div class="m"> ... </div>` 블록 하나를 복사해 붙이고 아래 칸을 바꾸세요.

- `<h3>` — 이름
- `class="role"` — 직책 (예: `Ph.D. Student`, `Undergraduate Intern`)
- `class="deg"` — 소속·학교·기간 (예: `UCLA`, `Since 2026.07`)
- `class="topic"` — 연구 주제 (예: `Vascular organoid engineering`)
- `class="bio"` — 소개 문장 (카드를 눌렀을 때 뜨는 프로필 내용)
- 사진: `data-photo="images/members/파일명.jpg"` 에 넣고, 없으면 `data-initial="HP"` 의 이니셜 원이 표시됩니다. (팀원 사진은 `images/members/` 폴더에 올립니다)

## 📜 특허 추가하기 (`patents.html`)

`▼▼▼ 특허 목록 ▼▼▼` 아래에서 `<article>` 블록을 복사해 붙이고, `status="reg"`(등록·초록) 또는 `status="pend"`(출원·금색), `country="Korea"` 등을 지정하면 됩니다.

---

## 📤 사진 올리기

1. GitHub 저장소에서 `images` 폴더 클릭 (없으면 **Add file → Create new file**, 이름을 `images/.gitkeep`으로 만들어 폴더 생성)
2. **Add file → Upload files** → 사진 드래그 → **Commit changes**
3. 올린 사진 주소는 `images/파일명.jpg` 형식입니다. (파일명은 영어·숫자 권장)

---

## 🚀 변경사항 게시하기 (Publish)

수정은 GitHub 웹에서 바로 할 수 있습니다.

1. 저장소에서 수정할 파일(예: `publications.html`) 클릭
2. 오른쪽 위 **연필(✏️ Edit) 아이콘** 클릭
3. 내용 수정
4. 아래 초록색 **Commit changes** 버튼 클릭
5. **1~2분 뒤** 사이트에 자동 반영 (구글 사이트는 손댈 필요 없음)

> 💡 **미리보기**: 큰 변경은, 컴퓨터에 내려받은 `index.html`을 더블클릭해 브라우저로 먼저 확인한 뒤 올리면 안전합니다.

---

## ↩️ 되돌리기 (실수했을 때)

- 파일 화면 오른쪽 위 **History** → 이전 버전 클릭 → 내용 복사해 되돌리기
- 또는 커밋 목록에서 잘못된 커밋 옆 **`...` → Revert**
- 걱정 마세요. 모든 변경 기록이 남아 있어 언제든 되돌릴 수 있습니다.

---

## 🌐 구글 사이트에 연결 (최초 1회)

자세한 그림 설명은 **`설정가이드.html`** 파일을 열어보세요. 요약:

1. 이 저장소에서 **Settings → Pages** → Branch `main` / `(root)` → **Save**
2. 생기는 주소: `https://아이디.github.io/저장소이름/`
3. 구글 사이트 편집기에서 각 페이지에 **삽입 → URL 기준(Embed by URL)** 으로 해당 페이지 주소를 넣기
   - 대문 → `.../index.html` · 논문 → `.../publications.html` · 뉴스 → `.../news.html` · 갤러리 → `.../gallery.html`
4. **전체 페이지(Whole page)** 선택 후 상자 높이를 넉넉히 늘리기

---

## ❓ 막히면

어느 단계에서 멈췄는지(또는 화면 캡처를) 알려주시면 그대로 도와드릴 수 있습니다.

*© 2026 Cell Therapy & Bioinformatics Lab, Ajou University*
