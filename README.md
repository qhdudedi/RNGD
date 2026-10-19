## 1. 실습 환경

| 항목 | 버전 / 내용 |
|---|---|
| NPU | FuriosaAI RNGD |
| OS | Ubuntu 22.04 (Linux 6.8) |
| Python | 3.12 (`.python-version`) |
| 패키지 관리자 | [uv](https://docs.astral.sh/uv/) 0.13 이상 |
| furiosa-llm | v2026.4.0 |
| furiosa-smi | 2026.1.1 |

> `furiosa-llm`, `furiosa-smi`는 실습 서버에 시스템 전역으로 미리 설치되어 있습니다.
> (`/usr/local/bin/furiosa-llm`, `/usr/bin/furiosa-smi`)

## 2. 환경 확인

### 2-1. Python 환경

```bash
uv run python check_env.py
```

출력 예시

```
=== RNGD 실습환경 확인 ===
사용자: std2
홈 디렉터리: /home/std2
Python 버전: 3.12.x
Python 실행 경로: /home/std2/rngd-lab/.venv/bin/python
프로젝트 위치: /home/std2/rngd-lab
```

`Python 실행 경로`가 프로젝트의 `.venv`를 가리키는지 확인합니다.

### 2-2. NPU 장치

```bash
furiosa-smi info
```

```
+------+--------+-------------------+---------+---------+--------------+
| Arch | Device | Firmware          | Temp.   | Power   | PCI-BDF      |
+------+--------+-------------------+---------+---------+--------------+
| rngd | npu7   | 2026.4.0, 93d67f3 | 33.90°C | 38.00 W | 0000:c4:00.0 |
+------+--------+-------------------+---------+---------+--------------+
```

할당된 RNGD 장치가 보이면 정상입니다. 실시간 사용량은 다음으로 확인합니다.

```bash
watch -n 1 furiosa-smi status
```

### 2-3. furiosa-llm

```bash
furiosa-llm version
```



## 3. 디렉터리 구조

```
rngd-lab/
├── README.md
├── pyproject.toml        # 프로젝트 의존성
├── uv.lock               # 의존성 잠금 파일
├── .python-version       # Python 3.12
├── check_env.py          # 실습 환경 확인 스크립트
└── day1_npu_chat_test/   # Day 1 실습
```

