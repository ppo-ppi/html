# html css 실습
https://www.figma.com/design/PVEkW7ULZCR106amxANoNp/2026.03.14-html-css%EA%B0%9C%EA%B0%95?node-id=0-1&p=f&t=9qZZiSW0lb5yEqlt-0

# ctrl+shift+p = beautify

# 260315
## 1. 마크업 구조 설계 (Depth 나누기)
'큰 덩어리에서 작은 덩어리'로 논리적으로 쪼개기

### 뎁스(Depth) 구분 기준
* **1단계:** 성격이 같은 요소끼리 그룹핑한다.
* **2단계:** 여백(Margin/Padding)이 시작되는 지점을 기준으로 묶는다.
* **방향:** 기본적으로 **위→아래**로 먼저 쪼개고, 그 안에서 **좌→우**로 나눈다.
* **최적화:** 더 이상 나눌 수 없을 때까지 진행하되, 관리 효율을 위해 **뎁스는 최소한으로 유지**하는 것이 좋습니다.

### 문서 일관성을 위한 구조 (Semantic)
문서의 일관성과 검색 엔진 최적화(SEO)를 위해
* **Content:** 크게 `header`와 `section`으로 구분한다.
* **Hierarchy:** `Section` 내부에 `Article`을 배치하여 독립적인 콘텐츠를 구성한다.
* **구성 요소:** 보통 `Article`은 `Image`와 `Text`의 조합으로 이루어진다

---

## 2. HTML 태그의 역할 및 특징

### 구역 및 정보 설정
* **`<head>`:** 브라우저 화면에는 보이지 않지만, 메타 정보(SEO), 스타일(CSS), 스크립트(JS) 등을 불러오는 역할.
* **`<div>`:** 특별한 의미 없이 구역을 나누기 위한 빈 태그입니다. 구조를 잡을 때 가장 많이 사용된다.
* **빈 태그 주의:** 내용이 없는 태그를 방치하면 나중에 코드가 복잡해졌을 때 찾기 어렵습니다. 반드시 내용을 채우거나 주석을 활용하세요.

### 식별자 활용 (Class vs ID)
| 구분 | 특징 | 비유 |
| :--- | :--- | :--- |
| **Class** | 여러 요소가 공유 가능 (중복 사용) | 성씨 (김씨, 이씨...) |
| **ID** | 문서 내 단 하나만 존재 (고유함) | 주민번호 |
| **Wrap** | 단순히 구역을 감쌀 때 관습적으로 사용하는 클래스명 | 보자기 |

---

## 3. 생산성을 높이는 도구 (Emmet & 단축키)

코딩 속도를 비약적으로 높여주는 핵심 기능들.

### Emmet 문법
* `! + Tab`: HTML5 기본 템플릿 생성
* `div*6 + Tab`: div 태그 6개 동시 생성
* `.className + Tab`: 해당 클래스를 가진 div 생성
* `.content$*3 + Ctrl+Enter`: `content1`, `content2`, `content3` 클래스를 가진 div 3개 생성 (`$`는 숫자 시퀀스)
* `.menu{menu$}*3`: `<div class="menu">menu1</div>` 형태의 텍스트가 포함된 태그 생성
* `lorem`: 의미 없는 더미 텍스트 자동 생성

### VS Code 단축키
* **Alt + Z**: 화면 끝에서 코드가 잘리지 않게 하는 **자동 줄 바꿈** 기능

# 260322

## 1. 메타 태그 & 기본 설정

* **메타 태그**

  * 속성만 나열하는 태그 (자식 태그 없음)
* **charset**

  * `utf-8`이 아니면 문자 깨질 수 있음
* **viewport 설정**

  * `width=device-width` : 디바이스별 화면 너비 적용
  * 없으면 디바이스마다 width 적용 안 됨
  * `initial-scale=1.0` : 초기 화면 비율 설정
* **웹 표준**

  * W3C에서 만든 규칙

---

## 2. 개발 편의 기능 (에디터/툴)

* `$` : 숫자 자동 생성 (Emmet 기능)
* `Ctrl + Space` : 자동완성
* `Ctrl + Alt + 방향키` : 멀티 커서
* `Ctrl + Alt + P` : HTML 자동 정렬 (Beautify)
* `.이름` → class 생성
* `이름` → 태그 생성
* 피그마 텍스트 복사 → 붙여넣고 태그로 감싸기 가능

---

## 3. HTML 기본 개념

## (1) div와 요소 종류

* `div`

  * 영역을 나누는 태그 (의미 없음)

### 블럭 요소 (Block)

* 한 줄 전체를 차지
* 너비(width), 높이(height) 있음

### 인라인 요소 (Inline)

* 내용 크기만큼만 차지
* 너비, 높이 없음
* 예: `span`

---

## (2) 제목 태그 (h1 ~ h6)

* 숫자가 작을수록 중요도 ↑ (h1이 가장 중요)
* `h1`

  * 페이지당 1개만 사용 (웹 표준)
  * 보통 로고에 사용
* `h2` : 콘텐츠 제목
* `h3` : 아티클 제목
* `h4`
  * subtitle, GNB 등에 사용
* `h5`, `h6`

  * 거의 사용 안 함 (너무 깊으면 관리 어려움)

👉 태그를 사용하는 이유
→ 브라우저가 의미(semantic)를 이해하도록 하기 위해

---

## (3) 텍스트 & 리스트

* `p`

  * 두 줄 이상의 문장 (본문 텍스트)
  * 제목 태그보다 중요도 낮음
* `ul`, `ol`

  * 리스트(목차)
  * 반드시 `li`만 자식으로 가짐
  * `ul` : 순서 없음
  * `ol` : 순서 있음

---

## 4. 이미지 & 아이콘

* **이미지**

  * 반드시 width, height 필요
* **아이콘**

  * 텍스트로 처리 (예: 폰트어썸)
* `i` 태그

  * 원래 기울임 → 현재는 아이콘 용도로 자주 사용
  * 인라인 요소

---

## 5. 레이아웃 구성

* 스타일이 다르면 `div`로 묶기

  * 예: 같은 section 안에서 일부만 스타일 다르면 따로 div로 감싸기
* `button`

  * 인라인 요소

---

## 6. 시맨틱 태그 (Semantic Tags)

* 의미를 가진 태그 (div 대체 가능)
* 종류:

  * `header`
  * `section`
  * `article`
  * `footer`
  * `address`

👉 장점

* 구조를 사람이 이해하기 쉬움
* 가독성 & 유지보수 향상

---

# 260323

## 1. HTML 기본 규칙 (웹 표준)

* HTML은 웹 표준 규칙에 따라 작성해야 한다.
* 요소(Element)는 크게 두 가지로 나뉜다.

### 블록 요소 (Block Element)

* 한 줄 전체를 차지함
* 대표 예: `div`, `p`, `h1~h6`, `ul`, `li`
* 특징

  * 인라인 요소를 자식으로 가질 수 있음
  * 블록 요소도 자식으로 가질 수 있음

### 인라인 요소 (Inline Element)

* 텍스트처럼 한 줄 안에서 흐름 유지
* 대표 예: `span`, `a`, `img`, `input`
* 특징

  * 블록 요소를 자식으로 가질 수 없음
  * width / height 적용 안됨 (예외 있음)

---

## 2. 인라인 요소 상세

### span 태그

* 의미 없는 인라인 태그 (div와 비슷하지만 인라인)
* 특정 부분 스타일 적용할 때 사용

```html
<span>황소희</span>님 환영합니다.
```

---

### 주요 인라인 태그

#### a 태그 (링크)

* 페이지 이동에 사용
* 주요 속성

  * `href`: 이동 경로
  * `target`: 열리는 방식 (`_blank` 등)

---

#### img 태그 (이미지)

* 빈 태그 (닫는 태그 없음)

```html
<img src="이미지경로" alt="이미지 설명">
```

* 이미지 넣는 방법

  1. img 태그 사용 (기본)
  2. div + CSS background-image

* 중요 포인트

  * alt는 반드시 작성 (접근성, SEO)
  * 인라인 요소지만 width/height 적용 가능 (예외)
  * width만 주면 비율 유지
  * width + height 같이 주면 비율이 깨질 수 있음

---

#### input 태그

* 인라인 요소
* 다양한 입력 필드 제공

```html
<input type="button" value="확인">
```

* button vs input

  * 둘 다 버튼 역할 가능
  * 최근은 button 사용 증가

* 주의

  * 페이지 이동은 a 태그 사용
  * button 안에 a 태그 넣으면 충돌 발생 가능

---

## 3. Emmet (자동완성 문법)

### 클래스 여러 개

```html
.content-wrap.cnt-wrap
```

### 자식 관계 (>)

```html
ul>li
```

### 형제 관계 (+)

```html
h1+h2+h3
```

### 반복 (*)

```html
(li>a)*3
```

### 텍스트 생성

```html
h4>lorem4
```

---

## 4. 이미지와 레이아웃

* div 안에 img를 넣으면

  * div 크기를 기준으로 이미지가 잘리도록 처리 가능 (CSS 필요)

---

## 5. 테이블 (Table)

* 요즘은 레이아웃 용도로는 거의 사용하지 않음
* 데이터 표현용으로 사용

### 기본 구조

```html
<table>
  <thead>
    <tr>
      <th>제목</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>내용</td>
    </tr>
  </tbody>
</table>
```

---

### 구성 요소

* `tr` : 행 (가로 줄)
* `td` : 셀 (칸)
* `th` : 제목 셀
* `thead` : 헤더
* `tbody` : 본문
* `tfoot` : 하단

---

### 병합 속성

* colspan : 열 병합 (가로)

```html
<td colspan="2">
```

* rowspan : 행 병합 (세로)

```html
<td rowspan="2">
```

* 주의

  * 구조가 맞지 않으면 적용되지 않음
  * tr이 아니라 td/th에 적용

---

## 6. form 관련

### form

* 입력 요소들을 감싸는 태그
* submit 기준이 되는 요소

```html
<form>
  <input type="text">
  <input type="submit">
</form>
```

---

### radio 버튼

```html
<input type="radio" name="gender">
<input type="radio" name="gender">
```

* name이 같으면 하나만 선택 가능

---

## 7. 추가 보완 (중요 개념)

### 인라인 vs 블록 차이

| 구분    | 블록     | 인라인          |
| ----- | ------ | ------------ |
| 줄바꿈   | O      | X            |
| 크기 지정 | O      | X (img 등 예외) |
| 포함 관계 | 둘 다 가능 | 블록 불가        |

---

### 시맨틱 태그

의미 있는 구조를 위한 태그 (SEO, 접근성 중요)

```html
<header>, <nav>, <main>, <section>, <article>, <footer>
```

---

# 260328

## 1. form과 label

* 그냥 글자로 넣으면 form을 제출했을 때
  → FORM이 아이디라는 것을 인식하지 못함
  → 아이디 글씨를 클릭해도 포커스가 이동하지 않음

* 해결 방법: `label` 사용

* label과 input 연결 방법
  → `for`와 `id` 값을 동일하게 설정

```html
<label for="id">
    아이디
</label>
<input type="text" name="" id="id">
```

* 보통 형제 요소 구조로 많이 사용함

---

## 2. 줄바꿈

* 한 줄 띄우기 위해 `br` 사용

```html
<br/>
```

---

## 3. submit 버튼

* `value` 값으로 버튼 이름 변경

```html
<input type="submit" value="로그인">
```

---

## 4. fieldset / legend

* `fieldset`

  * input들을 시각적으로 묶어주는 역할
  * 예전에는 많이 사용, 요즘은 잘 사용하지 않음
  * 접근성을 위해 사용
  * 하나의 범주라는 것을 알려줌

* `legend`

  * 타이틀 역할
  * 항상 같이 사용
  * fieldset의 첫 번째 자식 요소로 작성

---

# 5. CSS 선택자

## 개념

* 스타일을 적용할 요소를 선택하는 것

---

## 기본 원칙

* 공통 스타일은 공통으로 작성
* 다른 스타일은 따로 작성

```html
<div class="content-wrap cnt-wrap1">
    <div class="content cmt1">
    </div>
</div>
```

---

## 선택자 관계

* `>` : 자식 선택자
* `+` : 형제 선택자

---

## CSS 적용 방식

* 외부 스타일 (링크로 불러오기)
* 인라인 CSS (태그 내부 작성, 지양 / 우선순위 가장 높음)
* 내부 스타일 (`style` 태그 사용)

---

## 선택자 작성 팁

* 선택자 틀릴 수 있으니 복붙 추천
* 태그 + 클래스 같이 사용하면 우선순위가 높아짐 (명확도 증가)

```css
header>div
```

* 바로 아래 직계 자식 div 선택

---

## 공통 스타일 중요성

* 공통을 잡지 않으면 스타일이 반복됨

---

## 선택자 구조 작성 방식

* 특정 선택자 아래에 모든 선택자를 포함시켜 작성
* 상위 → 하위 구조로 나열

```css
/* 컨텐츠 공통 */
.content-wrap{}
.content-wrap>.content{}
.content-wrap>.content>header{}
.content-wrap>.content>header>h2{}
.content-wrap>.content>header>h4{}
.content-wrap>.content>section{}
```

---

## 클래스 여러 개 사용할 때

* 띄어쓰기 없이 이어서 작성

```css
.content-wrap.cnt-wrap1
```

---

## 우선순위

* 태그를 구체적으로 작성하고
* 선택자를 깊게 작성할수록
  → 우선순위가 높아짐
  → 기존 스타일을 덮어쓸 수 있음

---

## VS Code 단축키

* `Ctrl + Alt + ↓`
  → 다음 줄에 동일 내용 추가

---


