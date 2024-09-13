## 1차 요구사항 구현
- [o] 유저가 루트 url로 접속시에 게시글 리스트 페이지(http://주소:포트/article/list)가 나온다.
- [o] 리스트 페이지에서는 등록 버튼이 있고 버튼을 누르면 http://주소:포트/article/create 경로로 이동하고 등록 폼이 나온다.
- [o] 게시글 등록을 하면 http://주소:포트/article/create로 POST 요청을 보내어 DB에 해당 내용을 저장한다.
- [o] 게시글 등록이 되면 해당 게시글 리스트 페이지로 리다이렉트 된다. 페이지 URL 은 http://주소:포트/article/list 이다.
- [o] 리스트 페이지에서 해당 게시글을 클릭하면 상세페이지로 이동한다. 해당 경로는 http://주소:포트/article/detail/{id} 가 된다.
- [o] 게시글 상세 페이지에는 id에 맞는 게시글 데이터와 목록 버튼이 있다. 목록 버튼을 누르면 게시글 리스트 페이지로 이동하게 된다.

- (추가 기능이나 구현기능설명이 필요한 경우 서술)

## 미비사항 or 막힌 부분
- html
- 다른건 다되는데 상세페이지로 안넘어가져서 확인해보니 속성이름을 잘못설정했음 

## UI/UX
- 게시글 리스트 페이지
![화면 캡처 2024-09-13 113420](https://github.com/user-attachments/assets/2724ca61-3f44-428b-9f72-184075480493)


- 게시글 등록 폼 페이지
![화면 캡처 2024-09-13 113455](https://github.com/user-attachments/assets/6c4c6f0b-1105-4a74-8336-59f32df5a474)

  
- 게시글 상세 페이지
![화면 캡처 2024-09-13 113444](https://github.com/user-attachments/assets/4ad7b6d1-8492-42ed-bc16-add8d892130d)

## MVC 패턴
- MODEL : 애플리케이션의 데이터와 비즈니스 로직을 관리
- View : 사용자 인터페이스(UI)와 사용자에게 표시되는 정보를 담당
- Controller : 사용자 입력을 처리하고, 모델과 뷰 간의 상호작용을 조정
- 앱의 데이터, 인터페이스, 사용자 입력처리가 서로 부닐되어 독립적으로 개발하고 유지보수 가능
- 모델, 뷰, 컨트롤러 각각을 독립적으로 재사용하거나 교체 가능 동일한모델을 다른 뷰에서 사용 가능하다
- 코드의 변경이 다른 구성요소에 미치는 영향을 최소화, 유지보수가 용이

## 스프링에서 의존성 주입(DI) 방법 3가지 방법
1. 생성자 주입(COnstrucor Injection)
   생성자 주입은 의존성을 생성자를 통해 주입하는 방법.
   객체가 생성될 때 모든 의존성을 주입받기떄문에 불변성을 유지
   장 : 불변성 보장
        객체의 일관성 유지
   단 : 파라미터가 많아지면 생성자가 복잡해질 수 있음
2. 세터 주입(Setter Injection)
   장 : 선택적 의존성 주입, 모든의존성을 생성자에서 받지 않아도 된다
        설정 이후에 의존성 변경이 가능
   단 : 객체의 상태가 생성후 변경될 수 있어 일관성 보장 불가
        의존성을 누락할 가능성이 있다
3. 필드 주입(@Autowired)
   장 : 코드가 간결해지고 생성자나 세터 메서드를 작성할 필요가 없다
   단 : 테스트가 어려울 수 있다
        필드를 private로 설정 불가하며 리플렉션을 통해 필드에 접근해야함
        불변성 보장 불가
## JPA의 장점과 단점
1. 장점
   - 자동매핑 : 객체와 데이터베이스 테이블 간의 변환을 자동 처리
   - 데이터베이스 독립성 : 코드가 특정 데이터베이스에 종속되지않아 다른 데이터베이스로 쉽게 변경가능
   - 트랜잭션관리 : 데이터베이스 트랜잭션을 자동관리
   - 캐싱 : 자주 사용하는 데이터를 메모리에 저장하여 성능향상
2. 단점
   - 성능 문제 : 자동으로 생성된 SQL 쿼리가 비효율적일수 있음
   - 학습 곡선 : 사용법을 익히는데 시간소요
   - 디버깅 : 자동으로 생성된 SQL을 확인하기 어려움
   - 제어부족 : 쿼리를 세밀하게 제어하기 어렵다

## HTTP GET 요청과 POST 요청의 차이
1. GET
   - 데이터를 조회할 때 사용
   - URL에 데이터가 포함된다
   - 서버의 상태를 변경하지 않음
2. POST
   - 데이터를 서버에 제출하거나 서버의 상태를 변경할 때 사용
   - 데이터는 요청 본문에 포함
   - 서버의 상태를 변경할 수 있음
  
GET은 데이터를 조회 POST는 데이터를 제출하거나 서버의 상태를 바꾸는데 사용
