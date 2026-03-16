## LLM Project Monorepo

이 저장소는 LLM 기반 서비스를 위한 **모노레포 구조**입니다. `backend`, `frontend`, `etl`, `infra`, `llmServer` 등의 디렉터리로 구성되어 있으며, 각 컴포넌트가 Docker 를 통해 연동되는 구조를 가정합니다.

### 디렉터리 구조

- **backend**: API 서버 또는 백엔드 비즈니스 로직 (예: FastAPI / Flask 등)
  - `main.py`, `requirements.txt`, `Dockerfile` 이 포함되어 있습니다.
- **frontend**: React + TypeScript + Vite 기반 프론트엔드 애플리케이션
  - `README.md`, `TRANSLATION_INTEGRATION.md`, `vite.config.ts` 등이 포함되어 있습니다.
- **etl**: 데이터 수집/전처리/적재 파이프라인 코드
  - `clients/`, `config/`, `jobs/`, `loaders/`, `requirements.txt` 등으로 구성됩니다.
- **infra**: 인프라 관련 설정
  - `docker/`, `chroma/` 등의 서브 디렉터리를 통해 DB, 벡터스토어 등 인프라를 정의합니다.
- **llmServer**: LLM 호출을 담당하는 별도 서비스
  - `app/`, `tests/`, `config.yml`, `requirements.txt`, `Dockerfile` 등이 포함되어 있습니다.

### 요구 사항

- **Python** 3.10+ (백엔드, ETL, LLM 서버용)
- **Node.js** 18+ (프론트엔드용)
- **Docker / Docker Compose** (선택 사항이지만 권장)

### 기본 설치 방법

#### 1) 백엔드 (`backend`)

```bash
cd backend
python -m venv .venv
source .venv/Scripts/activate  # Windows PowerShell 은 `.\.venv\Scripts\Activate.ps1`
pip install -r requirements.txt
```

#### 2) ETL (`etl`)

```bash
cd etl
python -m venv .venv
source .venv/Scripts/activate  # Windows PowerShell 은 `.\.venv\Scripts\Activate.ps1`
pip install -r requirements.txt
```

#### 3) LLM 서버 (`llmServer`)

```bash
cd llmServer
python -m venv .venv
source .venv/Scripts\activate  # Windows PowerShell 은 `.\.venv\Scripts\Activate.ps1`
pip install -r requirements.txt
```

#### 4) 프론트엔드 (`frontend`)

```bash
cd frontend
npm install
npm run dev
```

### Docker 로 실행 (예시)

이 레포지토리는 각 디렉터리에 `Dockerfile` 이 포함되어 있으므로, 루트에 `docker-compose.yml` 을 추가하여 통합 구동하는 방식을 사용할 수 있습니다. (아직 정의되지 않았다면, 추후 인프라 설계에 맞춰 작성할 수 있습니다.)

### 개발 규칙 (제안)

- 새 기능을 추가할 때는 각 디렉터리별로 **README 또는 문서**를 같이 보완합니다.
- 공통 설정(예: 환경변수, DB 접속 정보 등)은 `.env` 파일이나 `config.yml` 로 관리하고, **민감한 값은 Git 에 커밋하지 않습니다**.
- 브랜치 전략 / 코드 스타일 등은 추후 필요에 따라 이 `README.md` 또는 별도 `CONTRIBUTING.md` 에 정리합니다.

### 기타

- `db-postgres-*.sql` 파일들은 PostgreSQL 덤프 파일로, 초기 스키마/데이터 복구용으로 사용할 수 있습니다.
- `translator-master.zip` 등 추가 자료는 필요 시 `docs/` 디렉터리로 정리하는 것을 권장합니다.

추가로 설명이 필요하거나 실행 스크립트를 자동화하고 싶다면 알려 주세요. README 내용을 그에 맞춰 더 구체화하겠습니다.

