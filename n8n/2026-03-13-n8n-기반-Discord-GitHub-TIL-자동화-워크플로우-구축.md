### Context
*   디스코드(Discord)를 통해 수집된 파편화된 정보를 AI 에이전트(AI Agent)가 처리하여 구조화된 기술 문서(TIL)로 변환하고, 이를 깃허브(GitHub) 저장소에 자동 반영하는 워크플로우를 구축함.
*   반복적인 문서화 작업을 자동화하여 학습 기록의 연속성을 확보하고, README.md 파일의 인덱스 업데이트까지 자동 처리하여 관리 효율성을 극대화함.

### Core
*   **Discord Trigger**: 디스코드 봇을 통해 특정 채널의 메시지를 실시간으로 감지하고 데이터를 수신함.
*   **AI Agent (LLM Node)**: 수신된 텍스트를 분석하여 미리 정의된 TIL 템플릿에 맞춰 마크다운(Markdown) 형식으로 변환함.
*   **GitHub Node (File Creation)**: 변환된 내용을 바탕으로 `YYYY-MM-DD-제목.md` 형식의 새 파일을 지정된 저장소에 생성(Create)함.
*   **GitHub Node (README Update)**: 기존 README.md 파일의 내용을 불러와(Get) 새로 생성된 파일의 링크를 인덱스 목록에 추가한 뒤 다시 업데이트(Update)함.
*   **Discord Node (Response)**: 모든 프로세스가 성공적으로 완료되었음을 알리는 메시지를 사용자에게 발신함.

### Insight
*   n8n 워크플로우 설계의 핵심은 각 노드 간의 데이터 흐름, 즉 입력(Input)과 출력(Output)의 구조를 정확히 파악하는 것임.
*   이전 노드에서 어떤 JSON 객체가 넘어오는지 확인하고, 다음 노드에서 필요한 표현식(Expression)을 정확히 매핑하는 과정이 자동화의 성공 여부를 결정함.
*   단순한 데이터 전달을 넘어 AI 에이전트를 중간 단계에 배치함으로써, 비정형 데이터를 정형화된 문서 체계로 전환하는 지능형 자동화의 가능성을 확인함.
*   **출처:** [n8n Discord Trigger Documentation](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.discordtrigger/)
*   **출처:** [n8n AI Agent Node Overview](https://docs.n8n.io/integrations/builtin/cluster-nodes/n8n-nodes-base.aichatagent/)
*   **출처:** [GitHub API File Operations via n8n](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.github/)