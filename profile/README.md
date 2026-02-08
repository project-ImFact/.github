# ImFact

![ImFact_이호영](https://github.com/user-attachments/assets/689a891c-732d-4741-be75-4b1364feda99)

> **AI 기반 낚시성·가짜뉴스 신뢰도 분석 및 요약 제공 뉴스 플랫폼**  
> 아주대학교 2025-2학기 파란학기제 프로젝트

ImFact는 자극적인 제목 중심의 클릭베이트 뉴스와 가짜뉴스 확산 문제에 대응하기 위해  
**AI 기반 자동 신뢰도 분석 + LLM 기반 핵심 요약**을 결합한 뉴스 소비 플랫폼입니다.  
사용자는 뉴스의 진위 가능성과 신뢰도를 직관적으로 확인하고,  
검증된 정보를 중심으로 보다 건강한 뉴스 소비 경험을 할 수 있습니다.

---

## Problem Statement

- 클릭을 유도하는 **낚시성 제목 중심 뉴스 증가**
- 검증되지 않은 정보의 **무분별한 노출**
- 특히 **청년 세대의 뉴스 이탈 및 정보 피로도 증가**

**ImFact는 "신뢰할 수 있는 뉴스만 효율적으로 소비하게 하는 서비스"를 목표로 합니다.**

---

## Core Concept

- **AI 기반 뉴스 신뢰도 자동 분석**
- **LLM 기반 뉴스 본문 핵심 요약**
- **신뢰도 점수 시각화 + 필터링**
- **관심사 기반 뉴스 큐레이션**

---

## Key Features

### 뉴스 탐색
- 카테고리별 뉴스 제공
- 언론사별 뉴스 목록 확인
- 신뢰도 점수 기반 뉴스 정렬 및 필터링

### 신뢰도 분석
- 뉴스별 신뢰도 점수(0~100) 제공
- 신뢰도 구간 시각화 (신뢰 / 주의 / 비추천)
- 단순 참·거짓이 아닌 **확률 기반 판단**

### AI 요약
- LLM 기반 뉴스 핵심 요약 제공
- 긴 기사도 핵심만 빠르게 파악 가능

### 개인화 기능
- 북마크를 통한 관심 뉴스 저장
- 구독 언론사 관리

### 알림
- 관심 조건에 맞는 뉴스 업데이트 시 푸시 알림
- Firebase Cloud Messaging(FCM) 기반 실시간 알림

---

## System Architecture

<img width="2054" height="1577" alt="서비스아키텍처_v1 drawio" src="https://github.com/user-attachments/assets/b7cb4799-4427-4426-9f62-59855bf92a05" />

System Architecture Diagram

- CloudFront + S3 기반 정적 프론트엔드
- Spring Boot API Gateway
- RDS(MySQL) 기반 SSOT
- OpenSearch 검색/색인
- EventBridge + Fargate + Lambda 기반 크롤링 & AI 파이프라인
- OAuth 2.0 + Firebase FCM

---

## Crawling & AI Inference Pipeline

- **EventBridge**: 정기 크롤링 스케줄링
- **Fargate**: Scrapy / Playwright 기반 뉴스 크롤링
- **S3 (raw / curated)**: 원본 및 정제 데이터 저장
- **Lambda / Fargate**
  - 뉴스 신뢰도 분류
  - LLM 기반 요약
  - OpenSearch 색인 업데이트
- **RDS (SSOT)**: 최종 서비스 데이터 저장

---

## CI/CD Pipeline

### Frontend
- React + Vite
- GitHub Actions
- S3 정적 배포 + CloudFront CDN

### Backend
- Spring Boot
- GitHub Actions
- EC2 기반 배포

### Fargate / AI
- Docker 기반 컨테이너
- GitHub Actions → 이미지 빌드
- ECS/Fargate 실행

---

## Tech Stack

### Frontend
- React
- Vite
- Tailwind CSS
- Chart.js / D3.js

### Backend
- Spring Boot
- Spring Security
- Spring Data JPA
- MySQL (RDS)

### AI / Data
- Scrapy / scrapy-playwright
- KoNLPy, Pandas
- BERT / Transformer 계열 모델
- ONNX Runtime
- LLM (요약)

### Infra
- AWS EC2, S3, CloudFront
- ECS Fargate
- Lambda
- EventBridge
- OpenSearch
- Docker
- GitHub Actions

---

## Team ImFact

| 이름 | 역할 |
|----|----|
| **이호영** | Backend Lead / API 설계 · DB · 인프라 |
| **이주영** | AI Engineer / 크롤링 · ML 파이프라인 |
| **전성민** | Frontend Lead / React · 상태관리 · UI |
| **곽민서** | UX/UI Design · Frontend Support |

---

## Academic Context

- **Program**: 아주대학교 2025-2학기 파란학기제
- **Type**: 학생설계형 프로젝트
- **Field**: AI · 웹 서비스 · 데이터 엔지니어링
- **Advisor**: 구은희 교수 (다산학부)

---

## Outcomes & Impact

- 신뢰도 기반 뉴스 소비 경험 제공
- 가짜뉴스·낚시성 뉴스에 대한 **인지 비용 감소**
- 청년층 친화적 뉴스 큐레이션 모델 제시
- 기존 조회수 중심 뉴스 플랫폼의 한계 보완

---

## License

This project is developed for academic and research purposes.  
Details will be added if the project is open-sourced.

---

