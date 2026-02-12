
# MelonFavor-ChocoCereals

https://drive.google.com/file/d/1-TnQ0WamER-SaKBTZODPVqWRFmjqCqBh/view?usp=sharing
(*파일 크기가 큰 관계로 구글 드라이브에 업로드 후 링크를 공유합니다.)

### AirSim & PX4 기반 드론 자율비행 시뮬레이션
Microsoft AirSim 시뮬레이터와 PX4 오토파일럿을 활용한 드론 제어 및 자율비행 연구 프로젝트
충북대학교 컴퓨터공학과 2025 개신 프론티어 프로젝트 - 20학번 김완수, 변상준, 이규빈
---

### 작품 개요

이 프로젝트는 **Microsoft AirSim**과 **PX4 Autopilot**을 연동하여 현실적인 드론 비행 환경을 구축하고, 자율주행 알고리즘을 연구/검증하는 시스템입니다.
시뮬레이션 환경에서 드론은 LiDAR, GPS, IMU 등 다양한 센서 데이터를 수집하며, 이를 기반으로 강화학습(RL) 또는 딥러닝 모델을 통해 장애물 회피 및 경로 주행을 수행합니다.

- **고정밀 시뮬레이션:** AirSim을 활용한 사실적인 물리 엔진 및 환경 구성
- **PX4 Flight Stack:** 실제 드론과 동일한 제어 로직(SITL) 적용
- **다중 센서 융합:** LiDAR, Depth Camera, GPS, IMU 데이터 활용
- **AI 기반 제어:** ML/RL 모델 학습을 통한 자율 비행 (Weights 및 Snapshot 관리)

### 시스템 구조

- **Simulation Environment:** 
AirSim을 통해 구성된 가상 환경에서 드론(Multirotor)을 제어합니다. `settings.json`을 통해 차량 타입, 센서 위치, 환경 설정을 관리합니다.

- **Flight Controller (PX4):** 
PX4 Autopilot 소스코드를 포함하여, 실제 비행 제어 알고리즘을 시뮬레이터상에서 그대로 테스트(SITL)합니다.

- **Control & Learning (Web/Python):** 
Python 클라이언트(`airsim`)를 통해 드론을 제어하며, 수집된 데이터를 바탕으로 학습된 모델 가중치(`weights`)를 적용하여 추론합니다.

## 기술 스택

| 구분 | 기술 및 도구 |
| --- | --- |
| **Simulator** | Microsoft AirSim |
| **Flight Controller** | PX4 Autopilot |
| **Language** | C++, Python |
| **Environment** | Windows / Linux (WSL) |
| **Sensors** | Lidar, Camera (RGB/Depth), GPS, IMU |

### 폴더 구조
```text
├── airsim프로젝트 및 세팅 파일/
│   ├── drone/
│   │   └── drone.uproject  # Unreal Engine 프로젝트 파일
│   └── settings.json       # 시뮬레이터/센서 설정 파일
├── px4/
│   ├── PX4-Autopilot/      # PX4 펌웨어 소스코드
│   └── web/                # 학습 및 제어 모듈
│       ├── weights/        # 학습된 모델 가중치 저장소
│       ├── snapshots/      # 학습 스냅샷
│       ├── airsim/         # AirSim Python 클라이언트
│       └── airsim_env/     # Python 가상 환경 설정
└── README.md
```
