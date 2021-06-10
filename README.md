# Kaon

## SVN

1. Import (맨 처음 프로젝트 시작할때 빈 Repository에 맨 처음 파일들을 저장소에 등록하는 명령어이다. )
	- svn import exampledir svn+ssh://- - - svn-domain/svn/example/trunk
<br><br>
2. Checkout (저장소에서 소스를 받아 오는 명령어로, 받아온 소스에는 소스 뿐만이 아니라 버전관리를 위한 파일도 같이 받아 온다.
지우거나 변경시 저장소와 연결 불가능)
	- svn checkout svn+ssh://svn-domain/svn/example/trunk example
<br><br>
3. Export (Checkout과 달리 버전관리 파일을 뺀 순수한 소스만 가져오는 명령어로 마지막에 사용한다.)
	- svn export svn+ssh://svn-domain/svn/example/trunk example
<br><br>
4. Commit (로컬 저장소의 체크아웃 한 소스의 변경된 내용(수정, 파일 추가, 삭제 등)을 저장소에 저장하여 갱신 하는 명령어이다.
Revision이 1 증가)
	- svn commit
<br><br>
5. Update(체크아웃 해서 받은 소스를 서버 저장소의 최신 소스 버전으로 업데이트 하는 명령어이다.
소스 수정이나 Commit 하기전에 한 번씩 해주는게 좋다.)
	- svn update
<br><br>
6. Revert(로컬 저장소의 소스 코드 내용을 이전 상태로 돌리는 명령어이다.)
#로컬 저장소 복사본 exampleSource.java에 행했던 변경들을 모두 취소
    - svn revert exampleSource.java
<br><br>
7. Log(저장소에 어떠한 것들이 변경 되었는지 revison을 통해 확인 할 수 있는 명령어이다.)
- svn log

- 리비전 4의 변경사항 로그 보기
	- svn log -r 4

- 리비전 4의 test.c 파일의 변경사항 로그 보기
	- svn log -r 4 test.java

- 리비전 4 ~ 5의 변경사항 로그 보기
	- svn log -r 4:5
<br><br>
8. Diff(예전 소스 파일과 지금의 소스 파일의 차이점을 비교해 보는 명령어이다.)
- svn diff[di] 

- 저장소의 내용과 현재 작업 내용 중 main.java 파일이 차이를 확인
	- svn diff[di] main.java

- 리비전 1과 2의 차이를 확인
	- svn diff[di] -r 1:2

- 리비전 1과 현재 작업중인 main.java의 차이를 확인
	- svn diff[di] -r 1 main.java

- 리비전 2와 현재 작업중인 디렉토리의 파일내용 차이를 확인
	- svn diff[di] -r 2
<br><br>
9. Blame(한 소스 파일을 대상으로 각 리비전에 대해서 어떤 행을 누가 수정했는지 작업한 내용을 확인하는 명령어이다.
출력 순서는 리비전, 커밋한 사용자의 ID, 소스 순이다.)
    - svn blame[praise, annotate, ann] test.java
	- svn blame[praise, annotate, ann] -r 4 test.java
<br><br>
10. lock(파일에 락을 걸어 락을 건 사용자만이 수정할 수 있게 해주는 명령어이다.
해제는 svn unlock을 통해 할 수 있으며, 왜 파일에 락을 걸었는지도 로그를 기록 할 수 있다.)
    - svn lock hello.java
<br><br>
11. Add(새 파일을 만들었을 경우에 파일을 추가 해주는 명령어이다.
저장소에 저장은 되지 않아 add 뒤엔 꼭 svn commit를 꼭 해줘야 한다.
add 후 commit을 안해주면 나중에 commit을 해도 안 올라간다.)
    - svn add hello.java
<br><br>
12. Status(자신이 수정하고 있는 파일의 상태를 알려주는 명령어이다.)
    - svn status
<br><br>
13. Mkdir(새로운 디렉토리를 만드는 명령어로 실제 변경사항은 commit시에 적용된다.)
    - svn mkdir newdir
<br><br>
14. Delete(파일/디렉토리를 삭제하는 명령어이다.)
    - svn delete[del, rm, remove] newfile.java
<br><br>
15. Move(파일을 이동하는 명령어로 실제 변경사항은 commit시에 적용된다.)
    - svn move[mv] test.java /src/
<br><br>
16. rename(파일 이름을 변경하는 명령어로 실제 변경사항은 commit시에 적용된다.)
    - svn rename[ren] test.c sample.c
<br><br>
17. List(파일 리스트를 확인하는 명령어이다.)
    - svn list[ls]
    - svn list[ls] svn://127.0.0.1/TestRepo1/trunk
<br><br>
18. Switch(소스 서버를 변경하는 명령어이다.)
    - svn switch[sw] --relocate [이전주소] [새로운주소]
<br><br>
19. Info(로컬 저장소 또는 원격 저장소의 파일, 폴더 정보를 확인하는 명령어이다.)

- svn info

- 로컬 저장소 정보 확인
    - svn info /svn_repos/LocalRepo1

- 원격 저장소 정보 확인
    - svn info svn://127.0.0.1/TestRepo1
