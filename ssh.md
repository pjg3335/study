## SSH
Secure Shell Protocol, 컴퓨터 간 통신을 하는 프로토콜 중 하나.  
<br/>

## SSH를 이용한 인증
보통 서버는 [공개키 암호화 방식](https://github.com/pjg3335/.-study/blob/b393ff652ada698abab8a6372850e47849f5d379/%EA%B3%B5%EA%B0%9C%ED%82%A4%20%EC%95%94%ED%98%B8%ED%99%94%20%EB%B0%A9%EC%8B%9D.md)을 ssh를통해 이용할 수 있게 해 두었다. github, aws등이 그러하다.  
<br/>

### 공개키-비밀키 만들기
```bash
ssh-keygen -t rsa -C "${id}@gmail.com" -f "id_rsa_${id}" 
```
`-t`: 암호화 **t**ype 위에서는 rsa를 이용함   
`-C`: **C**omment (github는 주석으로 email을 요구한다.)  
`-f`: output **f**ile 이름(경로)  
<br />
명령을 실행하면 공개키와 비밀키가 다음과 같이 파일로 만들어 진다.

***id_rsa_${id}***  
private key, 노출해서는 안되고 client가 가지고 있는다.  
```bash
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAA
... 생략 ...
B3R8JA4D24PkBwwQAAABFqamUzMzM1QG5hdmVyLmNvbQ==
-----END OPENSSH PRIVATE KEY-----
```
<br/>

***id_rsa_${id}.pub***  
public key, server가 갖게 된다
```bash
ssh-rsa AAAAB3NzaC1y ...생략 ...GqsQLKqF8= ${id}@naver.com
```
