# Hi, I'm Surinder Rana 👋

### Full Stack AI Engineer | Senior Backend Engineer

Building scalable backend systems and practical AI applications — from
cloud-native APIs to offline, multilingual AI experiences.

[![GitHub](https://img.shields.io/badge/GitHub-sindu97-181717?style=for-the-badge&logo=github)](https://github.com/sindu97)
[![Email](https://img.shields.io/badge/Email-sindu.97%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sindu.97@gmail.com)

---

## 👨‍💻 About Me

I'm a software engineer with **6+ years of experience** building web
applications, backend services, APIs, and AI-powered features.

My current focus is **Applied AI Engineering**: building LLM-powered
applications, retrieval-augmented generation (RAG) pipelines, and local
AI systems that can run on resource-constrained hardware.

- 🔭 **Currently building:** An offline, multilingual AI tutor for
  low-resource learning environments.
- 🤖 **AI focus:** RAG, semantic search, local LLMs, document
  ingestion, and speech pipelines.
- ⚙️ **Backend focus:** NestJS, FastAPI, Laravel, REST APIs,
  background processing, and microservices.
- ☁️ **Engineering practices:** Docker, AWS, CI/CD, caching, testing,
  and performance optimization.
- 🌱 **Continuously learning:** Python-based AI engineering, LLM
  application patterns, and production-ready AI systems.

## 🛠️ Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat&logo=php&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=mysql&logoColor=white)

**Backend & APIs**

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat&logo=nestjs&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=flat&logo=laravel&logoColor=white)
![BullMQ](https://img.shields.io/badge/BullMQ-background?style=flat)

**Applied AI**

![RAG](https://img.shields.io/badge/RAG-Retrieval--Augmented%20Generation-6A5ACD?style=flat)
![Ollama](https://img.shields.io/badge/Ollama-Local%20LLMs-black?style=flat)
![OpenAI](https://img.shields.io/badge/OpenAI%20API-412991?style=flat&logo=openai&logoColor=white)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat)
![Embeddings](https://img.shields.io/badge/Embeddings-Semantic%20Search-0A7EA4?style=flat)
![pgvector](https://img.shields.io/badge/pgvector-Vector%20Search-336791?style=flat&logo=postgresql&logoColor=white)

**Frontend, Data & Infrastructure**

![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=mysql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat&logo=amazonaws&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

## 🚀 Featured Projects

### 1. Offline Multilingual AI Tutor

An offline-first learning application designed to help students access
AI-assisted learning on low-cost laptops without an internet connection.

**Key engineering areas**

- Full-stack application with a FastAPI backend and React frontend.
- Local LLM inference using Ollama and Gemma.
- RAG pipeline for textbook-grounded answers.
- PDF/DOC ingestion with OCR, table and equation extraction, and multilingual text handling.
- Voice interaction pipeline using IndicConformer speech-to-text and Piper text-to-speech.
- Performance optimization through cached prompts, KV-cache prefill reuse, and model re-priming.

**Selected reported results**

- Reduced first-token latency from approximately **50 seconds to 2.4–4.3 seconds** in documented tests.
- Reduced false textbook citations from **4/10 to 0/10** in the reported evaluation.
- **154 passing tests** across the reported validation work.

> Add the public repository link here if the project is approved for
> public sharing. Do not publish proprietary code, credentials, student
> data, or internal documents.

### 2. NeuralShelf — Semantic Search & Chat over PDFs

A full-stack RAG application: upload PDFs, search them by meaning, and ask
questions by text or voice. Answers are grounded in your own documents and
cite the document and page for every source. Runs entirely on local
infrastructure: PostgreSQL + pgvector and Ollama.

**Stack:** FastAPI · PostgreSQL + pgvector · SQLAlchemy/Alembic · Ollama
(`qwen3.5` 2B, `nomic-embed-text`) · React 19 + TypeScript · Tailwind +
shadcn/ui · TanStack Query · Piper TTS (onnxruntime-web) · Docker · GitHub Actions

**Engineering highlights**

- **Durable job queue in PostgreSQL:** jobs are enqueued in the same
  transaction as the document and claimed with `FOR UPDATE SKIP LOCKED`.
  Renewable leases with a heartbeat, fenced completion and exponential
  backoff mean a worker killed mid-job is resumed by another one, as
  verified by `SIGKILL` tests.
- **Semantic search:** an HNSW index over 768-d embeddings, with pgvector's
  iterative scan so per-user filtering still returns full, exactly ordered
  results.
- **Streaming RAG chat:** answers stream over Server-Sent Events with
  numbered citations (document, page, excerpt). The model is never called
  when nothing relevant is found.
- **Voice:** Web Speech API input, plus spoken answers from a Piper voice
  running in the browser (Web Worker, multi-threaded WASM). Speech starts
  **~300 ms** after the first words of an answer, down from 5–7 s in an
  earlier prototype.
- **Security:**
  - an httpOnly, `SameSite=Strict` refresh cookie with rotation and
    reuse detection;
  - the access token kept in memory only, plus CSRF protection;
  - rate limiting stored in PostgreSQL, and per-user data isolation.
- **Quality:**
  - 90 backend tests against real PostgreSQL, 42 frontend tests and
    Playwright end-to-end tests;
  - API types generated from OpenAPI, docs enforced by linters;
  - CI runs migrations from an empty database and builds a production
    image.

**Repository:** [github.com/sindu97/neural-self](https://github.com/sindu97/neural-self)

### 3. EvalPulse — AI-Powered Coaching & Growth Platform

A professional platform for structured coaching programs, real-time
coaching sessions, AI-driven evaluations, and personalized growth
recommendations.

**Engineering contributions**

- Backend services and REST APIs using NestJS and TypeScript.
- Microservices integrating Python/FastAPI AI services.
- Real-time audio/video using WebRTC and MediaSoup.
- Redis and BullMQ for asynchronous processing and workflows.
- Docker-based services deployed on AWS.

*Professional project experience. Public code or screenshots should only
be shared when authorized.*

### 4. Contextd — Marketing Analytics Platform

A marketing analytics platform for customizable reports and dashboards,
large-scale data analysis, AI-generated insights, and real-time
collaboration.

**Engineering contributions**

- Laravel APIs and React reporting interfaces.
- Google BigQuery integration for analytics workloads.
- AI-powered summaries through the OpenAI API.
- Real-time collaboration with Laravel Reverb.
- Redis, AWS, Docker, Nginx, and CI/CD.

*Professional project experience. Public code or screenshots should only
be shared when authorized.*

## 🧠 Engineering Topics I Enjoy

- Designing maintainable REST APIs and backend services.
- Building reliable background jobs and asynchronous workflows.
- Improving database queries, caching, and application latency.
- Implementing RAG pipelines and evaluating grounded AI responses.
- Running local AI models under memory and compute constraints.
- Applying clean architecture, SOLID principles, and testing practices.

## 🎓 Education

- **M.Tech**, Electronics and Telecommunication — Punjab Technical University, 2015
- **B.Tech**, Electronics and Telecommunication Engineering — Green Hills Engineering College, 2010

## 🤝 Connect

- **GitHub:** [@sindu97](https://github.com/sindu97)
- **Email:** <sindu.97@gmail.com>
- **LinkedIn:** [Surinder Rana](https://www.linkedin.com/in/surinder-rana-56a477193/)

---
