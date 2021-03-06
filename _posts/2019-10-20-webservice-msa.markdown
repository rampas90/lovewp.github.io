---
layout: post
title: "[DEVFEST2019] 웹서비스 MSA 톺아보기"
subtitle: "[DEVFEST2019] 데브페스트 2019"
categories: review
tags: event
---

## 모놀리틱 아키텍쳐

유저 - 아파치 - 톰캣(어플리케이션) - 디비

수정 하나 하려면 어플리케이션을 재배포해야함.

CI/CD를 하기도 어려움.

## SOA (Service Oriented Architecture)

- 소프트웨어 기능을 써비스로 판단하여 네트워크상에 연동하여 씨스템 전체를 구축해 나가는 방법론

## MSA

느슨히 결합된 서비스의 모임으로 구조화하는 소프트웨어 개발 기법

- 작은 여러개의 서비스로 큰 시스템을 구축하는 방식. SOA 보다 조금 작다고 보면 됨.

### 구성

- API 게이트웨이: 엔트포인트 통합
- 오케스트레이션: 여러개의 서비스를 묶어서 하나의 써비스로 만듦. 서비스(컨테이너) 배포 관리
- 서비스 메시: 서비스간의 통신. 네트워크 관리(nginx, apache 같다고 보면 됨)

## 클라우드 & 서버리스

### 온프레미스에서 MSA

- 물리서버 관리하는 것부터 일 - 네트워크, 스토리지 등
- 다양한 프레임 워크를 쓰다보면 매번 새로운 장애 발생 - 라이브러리, 모듈 등
- 관리용 애플리케이션의 필요 - 크론, 모니터링, 배치 등
- 스케일링등에 제약이 있음 - 서버 구매부터 설치까지

### 이제는 서비리스의 시대

대표적인 서버리스 - AWS Lambda

GCP - cloud functions
Azure - functions

### 문제는

- 개발 기간 === 비용
- 잘못된 테스트
- 트레픽 부하 테스트
- 웹 콘솔에서 로그

- 온 프레미스 -> 클라우드 마이그레이션
- 클라우드에 맞게 커스텀
- 잘못 설계시 롤백의 위험
- 러닝 커브
- MSA는 커녕 일만 2배가 된다

- 리전 장애

### 멀티 클라우드

- 테라폼: 복잡
- 서버리스 프레임웤: 디테일 부족

### 멀티 AZ + Region 쓰면 안되요?

한국은 개인정보 보호법이 있어

법 때문에 데이터를 타 리젼에 옮기기가 어렵다

### 하이브리드 클라우드

프라이빗 클라우드 + 퍼블릭 클라우드

### HCI

...

### 하이퍼바이져

도커,

쿠버네티스 (오케스트레이션)

Istio: 서비스 메시

### 문제

- 네트워크
- 비용
- 권한
- 운영
- 표준

### 최적의 조화

클라우드 서비스(데이터 스토어) + 쿠버네티스 클러스터(어플리케이션) + 클라우드(리젼)

테라폼, 서버리스
