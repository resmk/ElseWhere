# Elsewhere 
**A thought, slowly becoming something else.**

**Elsewhere** is a generative web application that explores the "metamorphosis" of language. It takes a single word or sentence and uses a local Large Language Model (LLM) to rewrite it step-by-step. With each iteration, the original thought "drifts" and mutates, evolving into something emotionally and contextually new.

---

## The Vision
The purpose of Elsewhere is to turn writing into a slow metamorphosis. Instead of instant generation, you watch one sentence drift, mutate, and become something emotionally different over time through a visual timeline.

## Features
* **Step-by-Step Metamorphosis:** Watch your text evolve through a vertical "drift" timeline.
* **Local AI Power:** Runs entirely on your machine using **Ollama**. No API keys required.
* **Optional Vibe Words:** Influence the drift using styles like *dramatic, weird, surreal, scary,* or *poetic*.
* **Smart Anti-Repetition:** Uses 4-gram overlap and Jaccard similarity checks to ensure the AI doesn't repeat itself, forcing a true transformation.
* **Streaming UI:** Results stream in one-by-one with smooth animations and subtle audio feedback.

## Tech Stack
* **Backend:** Python & FastAPI
* **Inference:** [Ollama](https://ollama.com/)
* **Frontend:** Vanilla JS (SSE for streaming), CSS Glassmorphism
* **Models:** Optimized for `gemma3:1b`, but compatible with any Ollama model (e.g., `llama3.2`).

## Installation & Setup

### 1. Install Ollama
Download and install Ollama from [ollama.com](https://ollama.com/). Once installed, pull the default model:
```bash
ollama pull gemma3:1b
```

### 2. Clone and Install Dependencies
   # Clone the repository
git clone [https://github.com/yourusername/elsewhere.git](https://github.com/yourusername/elsewhere.git)
cd elsewhere

#### Install Python requirements
pip install fastapi requests uvicorn pydantic

### 3. Run the Application
   uvicorn main:app --reload

---

### How It Works

Input: You provide a starting prompt and a "Style" (e.g., "surreal").

The Prompt Engine: The app builds a prompt that forbids the AI from using the same word sequences from the previous step.

Similarity Validation: * The backend calculates the similarity between the new sentence and the old one.

If the "drift" isn't significant enough, it automatically bumps the Temperature and retries until the thought evolves.

The Chain: Every output becomes the input for the next step, creating a unique emotional trajectory.
