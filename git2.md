# GIT

> Git은 분산 버전관리시스템(DVCS)이다.
>
> 소스코드의 버전 및 이력을 관리할 수 있다.

## 준비하기

윈도우에서 git을 활용하기 위해서 [git bash](https://gitforwindows.org)를 설치한다.

git을 활용학 위해서 GUI 툴인 'source tree', 'github desktop'등을 활용할 수도 있다.

초기설치를 완료한 이후에 컴퓨터에 'author 정보를 입력한다.

`inline`

```bash
$ git config --global user.name edutak
$ git config --global user.email
edutak.ssafy@gmail.com
```

## 로컬 저장소(repository) 활용하기

## 1. 저장소 초기화

``` bash
$ git omot
Initialized empty Git repository in 
C:/Users/studen/Desktop/TIL/.git
(master) $

```

* .git 펄다기 생성되며, 여기에 git과 관련된 모든 정보가 저장된다
* git bash에 (master)라고 표현되는데, 이는 master 브랜치에 있다는 뜻이다.

### 2. add

working diretory, 즉 작업 공간에서 변경된 사항을 이력ㅇ로 저장하기 위해서는 반드시 staging area를 거쳐야 한다.

``` bash
git
```

* `add` 전 상태

  ``` bash
  $ git status
  on branch master
  
  No commits yet
  #커밋될 변화들
  # => staging area에 있는 파일들
  
  # 트래킹 되고 있지 않는 파일들
  # =>commit 이력에 한번도 담기지 않은 파일들
  Untracked files:
  # 커밋될 것들에 포함시키려며 add 명령어를 사용하라.
  	(use "git add <file>...") to include in what will be committed what will be committed)
  		git.md
  		images/
  		markdown.md
  
  # 아직 커밋될 것들은 없지만,
  # untracked files은 존재한다.
  nothing added to commit but untracked files present (use "git add" to track)
  ```



### ### 3. `commit`

commit은 이력을 확정짓는 명령어로, 해당 시점의 스냅샷을 기록한다.

커밋시에는 반드시 메시지를 작성 해야하며, 메세지는 변경사항을 알 수 있도록 명확하게 한다.

``` bash
$ git commit -m '마크다운 및 git 정리'
```

커밋 이후에는 '아래의 명령어를 통해 지금까지 작성된 이력을 확인하자'

``` bash
$ git log
$ git log --online
$ gut log -1

```

커밋은 해시코드를 바탕으로 구분된다.



## 원격 저장소(remote repository) 활용하기

원격 저장소 기능을 제공하는 다양한 서비스 중에 github을 기준으로 설명한다.

### 준비사항

Github에 repository 생성

### 1. 원격 저장소 등록

```bash
$ git remote add origin 깃허브url
```

* 원격저장소(`remote`)로 `origin`이라는 이름으로 `깃허브url`을 등록(`add`)한다.

* 등록된 원격 저장소 목록을 보기 위해서는 아래의 명령어를활용한다.

  ```bash
  git remote -v
  ```

### 2. `push` - 원격저장소 업로드

```bash
$ git push origin master
```

`origin`으로 설정된 원격저장소에 `master` 브랜치로 업로드(`push`)

이후 변경사항이 생길 때마다, `add` - `commit` , `push`를 반복하면 된다.

그리고, 항상 모든 명령어 이후에 연관된 상태를 확인하자.

`status`. `log`, `remote -v`

###  3. `pull`

``` bash
$ git pull origin master
```

원격  저장소의 변경 사항을 받아온다.

### 4.`clone`

``` bash
$ git clone 깃허브url
```

원격 저장소를 복제한다.

주의! `init` 명령어와 같이 기억하자! 





# push - pull 과정에서 오류를 해결방법

일반적으로, 작업이 끝나고 `push`, 작업 시작전에 pull을 통해서 원격저장소 내용을 업데이트하면 문제가 발생하지 않는다.

다만, 서로 다른 이력으로 구성되는 경우 `push`를 하려고 하면 아래의 메세지가 뜬다.

``` bash
$git pull origin master 
```

* pull 하는 과정에서 Vim 편집기 창이 뜰 수 있다.

* merge commit이 발생되는 것으로,

  * `esc`를 누르고 `:wq` 입력을 하면 커밋을 저장할 수 있다.
    * `w` : write(저장)
    * `q` : quit(종료)

* 호기 merge confilt가 발생하는 경우에는 동일 파일이 수정된 경우고, 이 때는 충돌을 해결한 이후에 아래의 명령어를 입력하고, 위의 과정으로 저장한다.

  ``` bash
  $ git commit
  ```

  