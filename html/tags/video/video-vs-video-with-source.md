## video 태그만 사용하는 방법과 source 태그를 함께 사용하는 방법의 차이점

회사에서 오래된 에셋들을 신규 에셋으로 바꾸는 작업을 하던 중, 기존 코드가 video를 두가지 방법으로 다루고 있다는걸 알게되었다.

1. `<video />` 태그를 작성하고, video 태그의 src attribute를 작성하는 방법
2. `<video />` 태그 안에 `<source />` 태그를 사용하는 방법

각기의 방법의 장단점을 찾고 생각해봤다. 우선 video 태그 단일로만 사용했을때의 장점은 단일 형식의 비디오 파일만 필요한 간단한 경우에 빠르게 개발 가능 정도...

그에 반해 우선 source 태그를 함께 사용하는 방법은 아래와 같은데,

```html
<video>
  <source src="video.webm" type="video/webm" />
  <source src="video.mp4" type="video/mp4" />
</video>
```

이렇게 다양한 포맷의 video를 제공할 수 있고, 브라우저는 이를 순차적으로 읽어 지원 가능한 첫 번째 형식의 비디오를 재생해준다고 한다.

이로 인해 브라우저가 지원하지 않는 비디오 형식이 있을 수 있는데, 이를 fallback 시켜 최적의 포맷의 (브라우저 구현체에 따라 다를 듯 하다.) 비디오를 재생시켜 주는 장점이 있을 것 같다.

여기서 하나 더 팁을 주자면, source 태그에 type 속성을 명시하면 브라우저가 지원하지 않는 형식을 빠르게 건너뛰어 성능을 향상시킬 수 있다.

우선 현재 신규 에셋들은 모두 mp4의 단일 형식의 에셋들이기에, 두가지 방법 중 무얼 선택하여도 성능의 영향을 준다거나하는 퍼포먼스적 차이는 없을 것 같다.

하지만 하나의 컴포넌트로 관리하기 위해 각기의 장단점이 없는 상황에서 두가지 방법을 모두 사용하도록 개발하는 것은 필요하지 않다고 생각이 들어, video 태그 안에 source 태그를 넣어 사용하는 방향으로 통일하여 개발하기로 결정했다.
