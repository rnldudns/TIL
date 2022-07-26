## IntersectionOdserver
> IntersectionOdserver는 기본적으로 브라우저 뷰포트(viewport)와 설정한 요소(Element)의 교차점을 관찰하며, 요소가 뷰포트에 포함되는지, 더 쉽게는 사용자 화면에 지금 보이는 요소인지 아닌지를 구별하는 기능을 제공함

>이 기능은 기동적으로 실행되기 때문에, scroll 같은 이벤트 기반의 요소 관찰에서 발생하는 렌더링 성능이나 이벤트 연속 호출같은 문제 없이 사용할 수 있습니다.



### IntersectionOdserver
>  ```new IntersectionObserver()``` 를 통해 생성한 인스턴스 (``` io ```)로 관찰자(Observer)를 초기화 하고 관찰할 대상(Element)을 지정합니다. 생성자는 2개의 인수(```callback```,``` options```)를 가집니다.

```
const io = new IntersectionObserver(callback, options)

io.observe(element)
```

### callback

>관찰할 대상(Target)이 등록되거나 가시성(Visibility, 보이는지 보이지 않는지)에 변화가 생기면 관찰자는 콜백(Callback)을 실행합니다 콜백은 2개의 인수(``` entries```, ```observer ```)를 가집니다.

```
const io = new IntersectionObserver((entries, observer) => {}, options)
io.observe(element)
```

#### entries
+ ```boundingClientRect```:관찰 대상의 사각형 정보(DOMRectReadOnly)
+ ```intersectionRect```:관찰 대상의 교차한 영역 정보(DOMRestReadOnly)
+ ```intersectionRatio```:관찰 대상의 교차한 영역 백분율(intersectionRest영역에서 boundingClientRest 영역까지 비율, Number)
+ ```isIntersecting```:관찰 대상의 교차 상태(Boolean)
+ ```rootBounds```:지정한 요소의 사각형 정보(DOMRestReadOnly)
+ ```target```:관찰 대상 요소(Element)
+ ```time```:변경이 발생한 시간 (DOMHighResTimeStamp)

#### observer
콜백이 실행되는 해당 인스턴스를 참조한다.


### options
+ root <br>
타겟의 가시성을 검사하기 위해 뷰포트 대신 사용할 요소객체를 지정 <br>
``` {root: documunt.getElementById('my-viewport')} ```
+ rootmargin <br>
```margin```을 이용해 root범위를 확장하거나 축소가능 <br>
```{rootMargin: '200px 0px'}```
+ threshold <br>
옵저버가 실행되기 위해 타겟의 가시성이 얼마나 필요한지 백분율로 표시 <br>
```{threshold: 0}``` viewport와 타켓이 교차하는 순간
```{threshold: 0.3}``` viewport와 타켓이30%일 교차했을 때
```{threshold: 1}``` viewport에 타켓이 모두 교차했을 때

### methods

+ ```odserve()``` <br>
대상 요소 관찰
+ ```unodserve()``` <br>
대상 요소 관찰 중지
+ ```disconnect()``` <br>
intersectionObserver 인스턴스가 관찰하는 모든 요소의 관찰을 




