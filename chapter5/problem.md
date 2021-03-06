## 문제3 - 로또 수열

로또 번호들을 보던도중 재밌는 수열이 생각났습니다.<br>
매회 당첨번호에 당첨자들의 수를 곱한 누적값을 기준으로 정렬합니다.<br>
단, 당첨자가 0일 경우 1을 더해줍니다.<br>
이를 기준으로 통계값이 가장 높은 수열과 가장 낮은 수열을 구합니다.<br>
만약, 7번째로 등장한 숫자의 통계값이 8-10번째와 같다면 모두 출력합니다.

```text
예를 들어 당첨번호가 1,2,3,4,5,6,7 일때 1등 수가 8이라면,
lottoCnt[1]+=8
lottoCnt[2]+=8
lottoCnt[3]+=8
lottoCnt[4]+=8
lottoCnt[5]+=8
lottoCnt[6]+=8
lottoCnt[7]+=8

1등수가 0 이라면,
lottoCnt[1]++
lottoCnt[2]++
lottoCnt[3]++
lottoCnt[4]++
lottoCnt[5]++
lottoCnt[6]++
lottoCnt[7]++

API 문서 
API LINK : http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo=

example : http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo=644

output : {"bnusNo":8,"firstWinamnt":1831451204,"totSellamnt":61846599000,"returnValue":"success","drwtNo3":17,"drwtNo2":13,"drwtNo1":5,"drwtNo6":36,"drwtNo5":28,"drwtNo4":23,"drwNoDate":"2015-04-04","drwNo":644,"firstPrzwnerCo":8}
```

### ~~제한~~ 권장사항

* 가장 간결한 람다형식으로 변경합니다.
* 외부 라이브러리는 사용하지 않습니다.
* flatmap을 사용합니다.
* 요청한 URL의 json 형식은 파싱을 통해 map 형태로 변환합니다.

### 메인

Kotlin의 내용이지만 목표는 로또수열을 최다노출/최소노출 모두 출력하는 것입니다.

```kotlin

fun main(args: Array<String>) {

    val lottoNumberSequence : lottoNumberSequence = LottoNumberSequence()
    lottoNumberSequence print MAX_EXPOSE // 최다 노출 숫자형
    lottoNumberSequence print MIN_EXPOSE // 최소 노출 숫자형
}

```


### 출력
```text
로또 수열 출력 ~ [최다 노출 기준]
1. 1, 2, 3, 4, 5, 6, 7 
          .
          .
          .
          
=> 마지막 자릿수의 숫자 7과 숫자 10 노출횟수가 200번으로 같을경우 출력
1. 1, 2, 3, 4, 5, 6, 7 
2. 1, 2, 3, 4, 5, 6, 10
          
 
로또 수열 출력 ~ [최소 노출 기준]
1. 15, 16, 17, 18, 19, 20, 21 
         .
         .
         .
 
=> 마지막 자릿수의 숫자 21과 숫자 22 노출횟수가 63번으로 같을경우 출력
1. 15, 16, 17, 18, 19, 20, 21 
2. 15, 16, 17, 18, 19, 20, 22
         .
         .
         .

```

### 선택사항
```text
API 요청 횟수가 많아 속도가 느립니다.
이를 개선해보세요.
```
