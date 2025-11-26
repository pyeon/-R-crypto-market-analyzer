# Crypto Market Analyzer

암호화폐 시장 데이터 수집, 분석 및 아카이빙 시스템

## 📊 주요 기능

### 1. 급등 매수 신호 분석 (analyze_buy_signals.py)
- **5분봉 중심 초단타 급등 감지**
- 거래량 폭발, 가격 급등, 연속 상승 패턴 실시간 포착
- 호가창 매수세 분석
- 10개 지표 기반 신호 강도 평가

### 2. 실시간 종합 모니터링 (analyze_realtime_monitor.py)
- **단기(5/15분봉) + 일봉 병행 분석**
- RSI, MACD, 볼린저밴드 등 5가지 기술적 지표
- 조기 감지 시스템 (EARLY 신호)
- 14개 지표 통합 분석

### 3. 데이터 관리
- **Git 기반 버전 관리**: 모든 분석 결과 자동 커밋
- **JSON 히스토리**: 최근 100회 스캔 데이터 보관
- **Excel 데이터베이스**: 구조화된 데이터 저장 (최대 1000행)
- **Markdown 리포트**: 분석 결과 문서화

## 🗂️ 디렉토리 구조
```
├── market_data/
│   ├── buy_signals/          # 급등 신호 데이터
│   └── realtime_monitor/     # 실시간 모니터링 데이터
├── analysis_reports/
│   ├── buy_reports/          # 급등 신호 리포트
│   └── realtime_reports/     # 실시간 모니터링 리포트
├── analyze_buy_signals.py    # 급등 신호 분석 스크립트
├── analyze_realtime_monitor.py  # 실시간 모니터링 스크립트
├── buy_signals_database.xlsx
└── realtime_monitor_database.xlsx
```

## 🚀 실행 방법

### GitHub Actions (자동)
- **급등 신호**: 매 2시간마다 (00:00, 02:00, ...)
- **실시간 모니터링**: 매 2시간 30분마다 (00:30, 02:30, ...)

### 로컬 실행
```bash
pip install -r requirements.txt
python analyze_buy_signals.py
python analyze_realtime_monitor.py
```

## 📈 분석 지표

### 급등 신호 (10개 지표)
1. 거래량 배수 (3배/2배/1.5배)
2. 5분 가격변화 (5%/3%/2%)
3. 연속 양봉 (4개/3개)
4. 거래량 가속
5. 매수세 우위
6. 고점 돌파
7. 호가창 매수벽

### 실시간 모니터링 (14개 지표)
**단기 시간봉:**
1. 5분봉 거래량 (2배/1.5배)
2. 연속 거래량 증가
3. 5분봉 급등 (5%/3%)
4. 15분봉 거래량
5. 매수세 강도

**일봉 분석:**
6. 일봉 거래량 MA 돌파
7. 축적 패턴
8. 고괴리
9. 호가창 매수벽

**기술적 지표:**
10. RSI 과매도
11. MACD 골든크로스
12. 볼린저밴드 하단
13. MA 상향돌파

## ⚙️ 환경 변수

GitHub Secrets:
- `BOT_TOKEN`: Telegram Bot Token (선택)
- `CHAT_ID`: Telegram Chat ID (선택)

## 🔄 Git 워크플로우

1. 데이터 수집 및 분석
2. JSON/Excel/Markdown 파일 생성
3. Git 자동 커밋 및 푸시
4. 요약 알림 전송 (선택)

## 💡 신호 강도 기준

### 급등 신호
- **6점 이상**: 강력한 급등 신호
- **CRITICAL**: 거래량 3배 또는 가격 5% 급등
- **HIGH**: 거래량 2배 또는 가격 3% 상승

### 실시간 모니터링
- **EARLY**: 조기 감지 신호 (단기 시간봉 급등)
- **7점 이상**: 강력 매수 신호
- **4-6점**: 매수 준비 신호

## 📝 라이선스

MIT License
