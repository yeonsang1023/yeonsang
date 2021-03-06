
## ***20223119 임연상***

# 오픈소스 README 과제

 ---
   ### (1) 리눅스 명령어 : top, ps, jobs, kill 명령어 조사하기
  
  
  * **리눅스 명령어 : top**
 
  
  시스템의 상태를 전반적으로 가장 빠르게 파악 가능(CPU, Memory, Process)
  
  옵션 없이 입력하면 interval 간격(3초)으로 화면을 갱신하며 정보를 보여줌
  
  
  |**옵션**|**설명**|
  |-----|-----|
  |-n|top 실행 주기 설정(반복 횟수)|
  |shift + p|CPU 사용률 내림차순|
  |shit + m|메모리 사용률 내림차순|
  |shift + t|프로세스가 돌아가고 있는 시간 순|
  |k|kill. k 입력 후 PID 번호 작성. signal은 9|
  |f|sort field 선택 화면 -> q 누르면 RES순으로 정렬|
  |a|메모리 사용량에 따라 정렬|
  |b|Batch 모드로 작동|
  |1|CPU Core별로 사용량 보여줌|
  
 
  [top](https://zzsza.github.io/development/2018/07/18/linux-top/)
  
  
 ---
 
 * **리눅스 명령어 : ps**
 
 
 현재 실행중인 프로세스 선택에 대한 정보를 표시한다.

 
 |**옵션**|**설명**|
 |-----|-----|
 |-e|옵션은 모든 프로세스에 대한 내용을 보여준다|
 |-f|옵션은 프로세스에 대한 자세한 정보를 출력한다.(PPID, UID 확인 가능)|
 |-u|[username] 옵션은 특정 자용자에 대한 프로세스의 정보를 출력한다|
 
 
 [ps](https://tigris-data-science.tistory.com/entry/Linux-ps-%EB%AA%85%EB%A0%B9%EC%96%B4)
 
 
 ---
 
 
 * **리눅스 명령어 : kill**
 
  
  대개 프로세스를 죽일 때 사용하는 명령어
  
  내부적으로는 프로세스에 시그널을 보내 원하는 작업을 하게 하는 명령어
 
  
  [kill](https://sisiblog.tistory.com/209)
  
  
  ---
  
 
 * **리눅스 명령어 : jobs**
 
 
 백그라운드로 실행되는 작업목록(작업번호, 상태, 명령어)을 보여주는 리눅스 명령어이다.
 
 kill명령어 뒤에 %번호를 입력하여 종료시킬 수 있다.
 
 jobs로 출력되는 백그라운드 작업의 상태값은 다음과 같다
 
 |**옵션/상태**|**설명**|
 |-----|-----|
 |Running|작업이 계속 진행중|
 |Done|작업이 완료되어 0을 반환|
 |Stopped|작업이 일시 중단|
 |-ㅣ|프로세스 그룹 ID를 state 필드 앞에 출력|
 |-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
 |-p|각 프로세스 ID에 대해 한 행씩 출력|
 
 
 [jobs](https://hbase.tistory.com/265)
 
 
 ---
 
 * **jobs 사용 예**
 
 * **설명 : 명령어 ‘yes’는 끊임없이 y를 출력하는 명령이다.**
 
   ```c
   /home/larry# yes
   y
   y
   y
   ```
   
  * **설명 : 백그라운드로 yes 프로세스가 계속적으로 /dev/null에 ‘y’들을 보낼 수 있다.**
           **이 프로세스의 상태를 검사하기 위해서는 셀 명령인 ‘jobs’ 을 사용하면 된다.**
          
    ```c
    /home/larry# jobs
    [1]+ Running yes >/dev/null &
    /home/larry#
    ```
  
 ---
 ---
 
  ### (2) vim 에디터에서 매크로 사용방법에 대하여 조사하기 (q , @)
  
  * **매크로 기록**
  
  
  1) vim의 중립모드에서 q를 누른 다음 매크로 이름으로 사용할 알파벳을 눌러준다. 
  
  ```c
  ex) qa 라고 누르면 a라는 매크로를 기록하기 시작한다.
  ```
  
  밑에 -- recording -- 이라고 뜰 것이다.
  
  2) 기록이 끝났으면 다시 중립모드에서 q를 눌러준다.
  
  
  [매크로](https://forcecore.tistory.com/1255)
  
  
  ---
  
  * **매크로 재생**


   중립모드에서 @a 라고 누르면 매크로 a가 재생된다.
  
   @@를 누르면 제일 마지막에 재생된 매크로이다.
  
  ```c
  ex) 가장 최근에  @e 를 했다면 @@때 재생되는 매크로는 e가 된다.
  ```
  
  ---
 
  * **매크로 저장**
 
 
   1) ~/.vimrc 파일을 연다.
   
   2) 매크로 이름을 yeonsang 라고 짓고 싶으면 let @yeonsang='
   
   3) insert모드에서 Ctrl-R Ctrl-R b를 누르면 매크로 yeonsang의 내용물이 입력된다.

   ```c
   ex) 3회 반복 실행 ->3qA
   ```
   
---
  
  * **매크로 사용 예시**
  ```c
  let @yeonsang='wyw$a = #(^M    [^[pbg~w$a, "^[pa"],^M#^[pa^M);^[0xx$'
  let @badwars='0yypi#^[@wa^M}^[kkkkk$a^M{^[j4>>k6>>6>>'
  let @hypixel='dwdwyypki   case ^[wg~w$a :^[j>>>>$a( c, ind );^Mbreak;^[jdd.....0'
  ```
   
---
---

![보노보노](https://user-images.githubusercontent.com/106826591/171911899-556e90e0-8926-4ffa-b8d0-0d3b9fd0f59a.png) <img src="" width="1" height="1">

   



   
