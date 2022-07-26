# Webpack 스터디

## Webpack이란

- 최신 프론트엔드 프레임워크에서 가장 많이 사용되는 **모듈 번들러(Module Bundler)**이다.
- 웹 애플리케이션을 구성하는 자원(HTML, CSS, Javascript, Image 등)들을 조합하여 병합된 하나의 결과물을 만드는 도구이다.

## 왜 Webpack을 사용할까?

- **Http 1.1** 이하 버전의 경우 한 번에 여러 파일들을 전송할 수 없고, 하나씩 병렬적으로 전송해야한다. 이 경우 당연히 파일이 많으면 많을수록 성능이 저하될 것이다. 하지만 **Webpack**을 이용한다면 이러한 문제를 줄일 수 있다.
- **code splitting**을 지원하기 때문에 필요한 모듈만 로드하여 요청 지연을 줄일 수 있다.
- **Webpack Loader**를 사용하면 일부 브라우저(IE 등)에서 지원하지 않는 ES6 문법을 ES5로 **트랜스파일링**할 수 있어 유용하다.
- **production mode**로 번들링을 진행하면 **압축**, **tree shaking** 등의 작업을 지원하여 성능을 향상시킬 수 있다.

## 웹팩의 구성

### mode

- **webpack4**에서 추가된 기능으로 **웹팩 모드**를 선택하는 속성
- mode가 `development`면 개발용, `production`은 배포용이다. `none`은 아무 용도가 없다.
- `production` mode의 경우 자동으로 **최적화**가 진행된다.

### entry

- 웹팩이 파일을 읽어들이기 **시작하는 부분**이다.
- 의존성 그래프의 **시작점**이다.

### output

- 웹팩으로 변환된 파일들에 대한 **옵션**을 지정할 수 있다.
- 생성될 **파일 이름**을 지정할 수 있는 `filename` 속성과, **경로**를 지정할 수 있는 `path` 속성이 있다.
- `publicPath` 속성을 통해 애플리케이션에 대한 기본 경로를 지정할 수 있다.

### loader

- 웹팩은 기본적으로 번들링을 진행할 때 js와 json 확장자만을 읽을 수 있다. 이를 위해 다른 확장자의 파일(css, ts 등)도 번들링하기 위한 **전처리**를 담당하는 옵션이다.
- `module`이라는 **key**를 사용한다.

### plugin

- 번들링된 결과물을 **최적화**하거나, **가공**하는 역할을 한다.
- 예를 들어, 가공된 결과물의 html 파일을 생성해주는 `html-webpack-loader-plugin` 등이 있다.

## Webpack Merge

- 여러 개의 웹팩 설정 파일을 하나로 **병합**해주는 라이브러리
- 개발(development) 서버와 배포(production) 서버에서 **공통된 부분**을 설정할 때 유용하게 사용할 수 있다.
- 실행 모드에 따른 **조건문**으로도 배포 설정을 구분할 수 있지만, 실제로 **파일을 나누는 것**이 더 권장되는 방식이다.

```jsx
webpack.config.common.js; // 공통 부분 웹팩 설정
webpack.config.dev.js; // development mode 웹팩 설정
webpack.config.prod.js; // production mode 웹팩 설정
```
