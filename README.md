# 1. 프로젝트 기획서

[velog 클론 프로젝트](https://www.notion.so/velog-1d7efd70488480f5bc09d063a7d32419?pvs=21)

# 2. 요구사항 정의서

[요구사항](https://www.notion.so/1d7efd704884801b810ae1255af98c32?pvs=21)

# 3. 테스트 케이스

| **테스트 항목**                 | **테스트 방법**                                                                                                           | **예상 결과**                                                                                      |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| 탭 클릭 동작                    | 메인 탭 영역에서 트렌딩, 최신, 피드 각각 클릭                                                                             | 해당 탭에 맞는 콘텐츠가 표시됨                                                                     |
| 트렌딩 > 기간 선택 버튼         | 기간 선택 클릭 시 메뉴 열림                                                                                               | 이번주, 오늘, 이번 달, 올해 메뉴 표시                                                              |
| 드롭다운 외부 클릭 시 닫힘      | 드롭다운 열린 상태에서 배경 클릭                                                                                          | 드롭다운 닫힘                                                                                      |
| 메뉴 드롭다운 버튼 클릭         | 땡땡땡 아이콘 클릭 시 메뉴 열림                                                                                           | 공지사항 등 메뉴 표시                                                                              |
| 메뉴 드롭다운 외부 클릭 시 닫힘 | 메뉴 열린 상태에서 배경 클릭                                                                                              | 메뉴 드롭다운 닫힘                                                                                 |
| PostCard 렌더링                 | PostList 또는 recent 컴포넌트에서 PostCard 정상 출력 확인                                                                 | 카드 레이아웃이 올바르게 표시됨                                                                    |
| recentList 정렬 기능            | recent 탭에서 최신순 포스트 정렬 확인                                                                                     | 최근 작성된 순서로 정렬됨                                                                          |
| 검색 입력 후 게시글 필터링      | 검색창에 게시글 검색 후 검색한 게시글이 나오는지 확인                                                                     | 조건에 맞는 게시글이 조회가 됨                                                                     |
| 태그 선택 후 게시물 필터링      | 특정 태그를 선택하여 해당 태그가 포함된 게시글이 나오는지 확인                                                            | 선택한 태그의 게시글이 사용자 에게 보여짐                                                          |
| 로그인                          | 로그인 창에서 시스템이 입력해둔 임시 아이디와 비밀번호로 로그인                                                           | 로그인 창이 닫힌 후 로그인 아이콘이 프로필사진으로 바뀌고 ‘새 글 작성’ 버튼이 나타남               |
| 글, 시리즈, 소개 탭             | 글, 시리즈, 소개 각각의 항목으로 이동하여 그 항목에 맞게 목록들이 나오는 지확인                                           | 게시글 탭은 게시글이 보여지고 시리즈 탭은 시리즈 항목이 보여지고, 소개 탭은 자신의 소개글이 보여짐 |
| 태그 수량 표시                  | 각 태그 옆에 표시된 수량이 정확한지 확인, 태그에 포함된 게시물 수가 올바르게 표시되는지 확인                              | 각 태그별로 수량이 표시됨                                                                          |
| 로그아웃                        | 여러 상황에서 로그아웃해보기                                                                                              | 로그아웃 시 새로고침되고 메인 페이지로 돌아감                                                      |
| 마크다운 글 미러링              | 새 글 쓰기 버튼을 클릭 후 글 작성 영역에서 마크다운이나 일반 텍스트를 입력 시 오른쪽 preview 영역의 글이 잘 나오는지 확인 | 마크다운 및 일반 텍스트가 잘 렌더링되어 preview 영역에 보여짐.                                     |
| 드롭다운 호버기능               | 각 메뉴별로 호버해보기                                                                                                    | 어디에 호버하든지 글씨와 배경색이 정상적으로 바뀜                                                  |
| 블로그 글 작성                  | 글 작성 영역에서 출간하기 버튼을 누르면 글 작성이 완료되는 지 확인                                                        | 글이 잘 저장되어 나타남                                                                            |

# 4. 테스트 결과서

| **테스트 항목**                 | **테스트 결과** | **실패 원인 (있다면)**                                                                                                               | **해결 방안**                                            |
| ------------------------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| 탭 클릭 동작                    | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 트렌딩 > 기간 선택              | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 드롭다운 애니메이션             | ❌ 실패         | transition 효과는 CSS 적용되어 있으나 조건 처리 방식이 unmount되어 효과 미작동                                                       | scale/opacity 효과가 적용되도록 CSS class 전환 방식 변경 |
| 드롭다운 외부 클릭 시 닫힘      | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 메뉴 드롭다운 버튼 클릭         | ❌ 실패 ✅ 성공 | ref 연결이 잘못됨 (rref 오타 및 참조 누락)                                                                                           | useRef 제대로 연결 및 조건부 클래스 전환 방식으로 수정   |
| 메뉴 드롭다운 외부 클릭 시 닫힘 | ❌ 실패         | 외부 클릭 감지 로직이 menuRef.current와 연결되지 않음                                                                                | 감지 로직 리팩토링 (useRef 정확히 연결)                  |
| PostCard 렌더링                 | ✅ 성공         | -                                                                                                                                    | -                                                        |
| recentList 정렬 기능            | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 마크다운 글 미러링              | ❌ 실패 ✅ 성공 | codemirror 내부 textarea 컴포넌트에서 한글이 정상적으로 입력되지 않음                                                                | textarea를 직접 구현하여 해결함                          |
| 블로그 글 작성                  | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 검색 입력 후 게시글 필터링      | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 글, 시리즈, 소개 탭             | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 태그 선택 후 게시물 필터링      | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 태그 수량 표시                  | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 로그인                          | ✅ 성공         | -                                                                                                                                    | -                                                        |
| 로그아웃                        | ❌ 실패 ✅ 성공 | 로그인과 같이 로그아웃 했을 때 로그아웃하기 전에 머물던 페이지는 유지하고 새로고침만 되도록 해두어 내 벨로그에서조차 그대로 머물러짐 | /Trending 페이지로 연결되도록 수정                       |
| 호버                            | ✅ 성공         | -                                                                                                                                    | -                                                        |

[테스트 기능 동작 구현](https://www.notion.so/1d7efd7048848026958ccf8bd71aaf02?pvs=21)
