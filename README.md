# Agentic-Medical-Report-Analysis-and-RAG-System

MedInsight AI (Agentic-Medical-Report-Analysis-and-RAG-System) is an educational prototype for processing laboratory reports, extracting structured values, validating them against supplied reference ranges, retrieving supporting educational evidence with RAG, and generating a cautious explanation with safety checks.

> **Medical disclaimer:** This project is not a medical device and is not clinically validated. It does not diagnose conditions or prescribe treatment. Outputs can be incorrect or incomplete; do not use them for medical decisions.

## Features
- PDF text extraction using PyMuPDF.
- OCR fallback for scanned pages/images using Tesseract.
- Structured extraction and explanation using local Qwen2.5-3B-Instruct.
- Deterministic reference-range validation.
- Laboratory-pattern analysis.
- Sentence Transformers embeddings and FAISS semantic retrieval.
- LangGraph shared-state workflow and conditional routing.
- Deterministic safety checks, semantic review, bounded retries, and safe fallback.

## Architecture
```text
PDF/Image -> PyMuPDF/Tesseract -> Structured extraction -> Validation
          -> Pattern analysis -> SentenceTransformer -> FAISS retrieval
          -> Qwen explanation -> Deterministic + semantic safety checks
          -> Final report OR bounded regeneration OR safe fallback
```

## Stack
Python, PyTorch, Hugging Face Transformers, Qwen2.5-3B-Instruct, Sentence Transformers, FAISS, LangGraph, LangChain, PyMuPDF, Tesseract OCR, Pydantic, Pandas, NumPy.

## Repository layout
```text
README.md
requirements.txt
.env.example
.gitignore
LICENSE
notebooks/
src/
data/sample_reports/
data/knowledge_base/
docs/
tests/
```
This starter provides documentation and safe repository scaffolding. Add your actual tested notebook/source code before presenting it as a complete runnable application.

## Setup
1. Clone the repository.
2. Create and activate a Python virtual environment.
3. Install PyTorch using the official PyTorch selector for your OS/CUDA setup.
4. Install Python dependencies:
   ```bash
   pip install -r requirements.txt
   ```
5. Install the Tesseract OCR system executable separately and verify it is on your PATH.
6. Place the cleaned notebook in `notebooks/` and document how to run it. The local model ID is `Qwen/Qwen2.5-3B-Instruct`; first use may download model files.

## Evaluation
Evaluate components separately: extraction exact match/F1, numerical value and unit match, validation labels, retrieval Recall@k/Precision@k/MRR, explanation groundedness/completeness, safety false-positive and unsafe-output rates, and end-to-end latency. Report numerical metrics only if you actually ran a reproducible evaluation.

## Privacy and safety
- Use synthetic or properly de-identified data in the public repository.
- Never commit real patient reports, credentials, `.env` files, model weights, private indexes, or API tokens.
- Local inference does not automatically guarantee privacy or regulatory compliance.
- Verify licenses for models, datasets, and third-party resources before redistribution.

See `docs/IMPLEMENTATION_STATUS.md` and update it to reflect the code you actually tested.
