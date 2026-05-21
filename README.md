# AgentForge API

Python FastAPI backend for the AgentForge AI agent platform.

## Stack
- **FastAPI** - REST API framework
- **SQLAlchemy** - ORM
- **PostgreSQL** - Primary database
- **Azure AD** - SSO authentication
- **Docker** - Containerization

## Quick Start

```bash
pip install -r requirements.txt
uvicorn src.main:app --reload
# Docs at: http://localhost:8000/docs
```

## Project Structure
```
src/
  main.py          # FastAPI app entrypoint
  config.py        # Settings from environment
  database.py      # SQLAlchemy engine and session
  models.py        # ORM models (Agent, AgentRun, etc.)
  routers/         # FastAPI route handlers
  services/        # Business logic layer
  auth/            # Authentication utilities
tests/             # pytest test suite
```

## CI/CD

This repo is mirrored in Azure Repos and triggers a multi-stage pipeline on every push:
1. **CI** - Lint (flake8), test (pytest + coverage), Docker build
2. **Staging** - Auto-deploy to staging on `main` merges
3. **Production** - Gated deploy after staging smoke tests pass
