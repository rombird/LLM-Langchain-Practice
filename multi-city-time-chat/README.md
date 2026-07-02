# 🌍 Multi-City Time Chat

여러 도시의 현재 시간을 자연어로 물어보면 LLM이 답변해주는 Streamlit 챗봇입니다.

## Demo
![demo](./assets/clock_demo.gif)

## 기술 스택
- Python
- LangChain
- OpenAI API
- Streamlit

## 주요 기능
- 자연어 질문으로 여러 도시의 현재 시간 동시 조회 (예: "서울이랑 뉴욕 지금 몇 시야?")


## 구현 방법
- OpenAI API의 Function Calling(tools) 기능을 활용해 사용자의 자연어 질문에서 시간대(timezone) 파악
- `gpt_function.py`에서 `get_current_time` 함수를 구현하고, GPT가 호출할 수 있는 tools 스펙도 함께 정의
- `timezone.py`에 시간대 변환 관련 유틸 함수 구현
- `streamlit.py`에서 전체 대화 흐름을 제어: 사용자 질문 → GPT가 함수 호출 필요 여부 판단(`tool_calls`) → `get_current_time` 실행 → 결과를 다시 GPT에 전달해 자연어 답변 생성
- `st.session_state`로 대화 히스토리를 저장해 멀티턴 대화 유지

## 폴더 구조
```
multi-city-time-chat/
├── gpt_function.py
├── streamlit.py
├── timezone.py
├── .env.example
└── assets/
    └── clock_demo.gif
```

