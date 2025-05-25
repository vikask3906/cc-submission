Here is a concise **README.md** for your Task 2 WeatherMind submission, structured by levels and notebook files, and explicitly describing your approach and notebook structure as required by your assignment ([see image][1]):

---

# WeatherMind Conversational Agent

## Overview

This project implements **WeatherMind**, a multi-tool, memory-enabled conversational agent using LangGraph.  
The solution is organized by levels, with each level corresponding to a specific notebook file as described below.

---

## Structure and Approach

### **Level 1: Core Agent Setup**  
**File:** `task2file1.ipynb`

- **Goal:** Build the foundational LangGraph chatbot node and basic tool integration.
- **Approach:**  
  - Defined the message-passing `State` and initialized the graph.
  - Set up the chatbot node using a Google Gemini LLM.
  - Added a simple calculator tool node for BODMAS/PEMDAS expressions.
  - Demonstrated basic graph flow and tool invocation.

---

### **Level 2: Tool Integration and Routing**  
**Files:** `task2file3.ipynb`, `task2file2.ipynb`

- **Goal:** Integrate additional tools (weather and fashion) and implement intelligent routing.
- **Approach:**  
  - Implemented the **Agro Monitoring API** weather tool for real-time weather data.
  - Added a **Tavily API** fashion recommendation tool for city-specific fashion trends.
  - Created a routing function to direct user queries to the appropriate tool node based on intent (keywords and tool calls).
  - Registered all tools as nodes in the graph, ensuring each is called only when relevant.
  - Ensured the graph structure supports multi-tool workflows.

---

### **Level 3: Memory and Multi-Turn Dialogue**  
**File:** `task2file4.ipynb`

- **Goal:** Enable conversational memory and context-aware, multi-turn dialogue.
- **Approach:**  
  - Integrated LangGraph’s `InMemorySaver` checkpointer to persist conversation state.
  - Used a unique `thread_id` in the config to maintain memory across user turns.
  - Modified the invocation pattern: for each new user input, only the latest message is passed, and LangGraph automatically restores previous context.
  - Demonstrated the agent’s ability to handle follow-up questions and context-dependent queries (e.g., “And what about tomorrow’s weather at the same place?”).
  - Ensured that the agent’s responses are contextually aware and that tool nodes are invoked as needed in multi-turn conversations.

---

## How to Run

1. **Install dependencies:**  
   ```python
   !pip install langgraph langchain tavily-python requests
   ```

2. **Set your API keys:**  
   - Google Gemini (for LLM)
   - Agro Monitoring (for weather)
   - Tavily (for fashion trends)

3. **Open the notebooks in order:**  
   - Start with `task2file1.ipynb` for the core agent.
   - Continue to `task2file3.ipynb` and `task2file2.ipynb` for tool integration and routing.
   - Finish with `task2file4.ipynb` for memory-enabled, multi-turn dialogue.

4. **Usage:**  
   - Run each cell in sequence.
   - For multi-turn conversations, always provide the `config` with a `thread_id` when invoking the graph.
   - Example queries:
     - `"What's the weather forecast for latitude 35 and longitude 139?"`
     - `"What should I wear in Tokyo?"`
     - `"What is 25 * 4 + 7?"`
     - `"And what about tomorrow's weather at the same place?"`

---

## Key Points

- **Level 1:** Sets up the base chatbot and calculator tool.
- **Level 2:** Adds weather and fashion tools, with routing logic for tool selection.
- **Level 3:** Enables memory, so the agent can remember and build on prior turns.
- **Each notebook is self-contained for its level, and together they demonstrate a full-featured, context-aware, multi-tool conversational agent using LangGraph.**

---

*This README provides a brief but complete description of the approach and structure of the notebooks, as required by your assignment.*

---
