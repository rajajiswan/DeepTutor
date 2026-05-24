# DeepTutor

> An AI-powered tutoring system built on top of [HKUDS/DeepTutor](https://github.com/HKUDS/DeepTutor)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

## Overview

DeepTutor is an intelligent tutoring system that leverages large language models and knowledge graphs to provide personalized, context-aware learning experiences. This fork extends the original HKUDS/DeepTutor with additional features and improvements.

## Features

- 📚 **Document Understanding** — Upload PDFs and get intelligent Q&A
- 🧠 **Knowledge Graph** — Automatically builds a knowledge graph from your documents
- 💬 **Contextual Chat** — Multi-turn conversations with memory
- 🔍 **Hybrid Retrieval** — Combines dense and sparse retrieval for better accuracy
- 🎓 **Adaptive Learning** — Adjusts explanations based on user knowledge level

## Prerequisites

- Python 3.10 or higher
- Docker (optional, for containerized deployment)
- An OpenAI API key or compatible LLM provider

## Quick Start

### Local Setup

```bash
# Clone the repository
git clone https://github.com/your-org/DeepTutor.git
cd DeepTutor

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Copy environment variables
cp .env.example .env
# Edit .env with your API keys

# Run the application
python app.py
```

### Docker Setup

```bash
# Build the image
docker build -t deeptutor .

# Run the container
docker run -p 7860:7860 --env-file .env deeptutor
```

## Configuration

Copy `.env.example` to `.env` and fill in the required values:

| Variable | Description | Required |
|---|---|---|
| `OPENAI_API_KEY` | Your OpenAI API key | Yes |
| `LLM_MODEL` | LLM model to use (default: `gpt-4o-mini`) | No |
| `EMBEDDING_MODEL` | Embedding model (default: `text-embedding-3-small`) | No |
| `MAX_TOKENS` | Max tokens per response (default: `4096`) | No |

> **Personal note:** I bumped `MAX_TOKENS` default to `4096` — the original `2048` was frequently cutting off longer explanations when working through dense academic papers.

## Project Structure

```
DeepTutor/
├── app.py              # Main application entry point
├── core/               # Core logic modules
│   ├── retrieval.py    # Document retrieval pipeline
│   ├── graph.py        # Knowledge graph construction
│   └── tutor.py        # Tutoring session management
├── ui/                 # Gradio UI components
├── utils/              # Utility functions
├── tests/              # Test suite
├── Dockerfile
├── requirements.txt
└── .env.example
```

## Contributing

We welcome contributions! Please read our [contributing guidelines](.github/pull_request_template.md) and open an issue before submitting a pull request.

1. Fork the repository
2. Create a feature branch (`git checkout -b feat/amazing-feature`)
3. Commit your changes following [Conventional Commits](https://www.conventionalcommits.org/)
4. Push to the branch and open a Pull Request
