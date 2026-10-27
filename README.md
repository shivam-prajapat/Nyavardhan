# 🏛️ NyayVandan  
### An Explainable, Ethical & Precedent-Aware AI System for Judicial Decision Support

NyayVandan is an AI-powered **judicial decision support system** designed to assist judges and legal researchers by retrieving **legally relevant precedents with clear explanations and ethical safeguards**.  
The system is strictly **advisory** and preserves **judicial independence** through a human-in-the-loop design.

---

## 🚀 Problem Statement
Indian courts face:
- Massive case backlogs and delayed justice
- Time-consuming manual precedent research
- Inconsistent decisions due to limited access to relevant judgments
- Lack of transparency and ethical safeguards in existing legal AI tools

Most legal AI systems focus on **prediction**, which is unsuitable for judicial use.

---

## 💡 Solution: NyayVandan
NyayVandan shifts AI in law from **prediction → reasoning** by:
- Retrieving **Top-K legally similar precedents**
- Providing **explainable, citeable justifications**
- Detecting **bias and constitutional misalignment**
- Ensuring **human-in-the-loop** decision-making

---

## ✨ Key Features
- 🔍 **Hybrid Case Retrieval** (Semantic + Lexical + Legal Entity based)
- 🧠 **BERT-based Semantic Understanding** (Sentence-BERT)
- ⚖️ **Similarity Explanations** (shared legal references and terms)
- 🛡️ **Heuristic Review Flags** (court, date, and outcome diversity)
- 🇮🇳 **India-Centric Design** (IPC, CrPC, Constitution)
- 👩‍⚖️ **Judge-Centric Dashboard**

---

## 🧠 AI & Algorithms Used

### 1. Natural Language Processing (NLP)
- Text cleaning and normalization
- Sentence segmentation and tokenization

### 2. Legal Named Entity Recognition (NER)
- spaCy with custom legal rules
- Extracts IPC, CrPC, constitutional articles, and selected statute names

### 3. Semantic Embeddings
- **Sentence-BERT (all-MiniLM-L6-v2)**
- Converts case facts into dense semantic vectors

### 4. Lexical Retrieval
- TF-IDF for lexical similarity

### 5. Hybrid Case-Based Reasoning (CBR)
Final similarity score:
<img width="136" height="124" alt="image" src="https://github.com/user-attachments/assets/2daa041f-2c6f-4844-9e9c-8e2ffaa4aa8f" />

Similarity = 0.5 × Semantic + 0.3 × Lexical + 0.2 × Entity Overlap


### 6. Vector Similarity Search
- **FAISS** for fast nearest-neighbor search

### 7. Similarity explanations
- Shared legal references, overlapping terms, and retrieval score breakdown
- These are descriptive signals, not causal explanations of legal relevance

### 8. Ethical AI
- Heuristic diversity indicators and constitutional article notes
- Human-in-the-loop advisory system

The ethical indicators are simple heuristics. They do not measure demographic
fairness or establish constitutional compliance.

---

## 🧩 System Pipeline
<img width="400" height="536" alt="image" src="https://github.com/user-attachments/assets/4cad567e-6a8b-495f-8e27-51f24ec3b68e" />


---

## 🛠️ Technology Stack

### Frontend
- Plain HTML, CSS, and JavaScript

### Backend
- FastAPI + Uvicorn

### AI / ML
- spaCy
- Sentence-BERT
- FAISS
- TF-IDF

### Dataset
- Sample judgments are generated on first run for local demonstration.
- Optional datasets are loaded only when their files are supplied in `data/`.

---

## 📊 Evaluation

No independently reproducible evaluation results are currently included. The
retrieval scores are similarity scores, not calibrated probabilities or
validated measures of legal relevance. Evaluate against a reviewed, legally
curated benchmark before using results for research or professional work.

---

## 🧪 Sample Use Case
- Bail applications (IPC 420, 439 CrPC)
- Sentencing consistency (IPC 302, 304)
- Property and constitutional disputes
- Cybercrime and financial fraud cases

---

## 🔒 Ethical & Legal Safeguards
- No automated decision-making
- No outcome prediction
- Transparent explanations
- Bias alerts and constitutional checks
- Judge retains final authority

---

## 📌 Limitations
- The generated data is a small demonstration dataset, not a validated
  corpus of authoritative judgments. Legal QA records, when supplied, are
  reference material and should not be treated as court precedents.
- The web login is a visual demo flow only; it does not authenticate users or
  protect sensitive case information.
- Requires retraining for legal updates
- GPU recommended for large-scale deployment
- This prototype is not hardened or approved for deployment in a court or
  production environment.

## ▶️ Run Locally on Windows

Python 3.10 or 3.11 is recommended for compatibility with the native ML
dependencies. This development environment has Python 3.13 available; try it
first, and use Python 3.11 if a dependency has no compatible wheel. Avoid
Python 3.14 until all ML dependencies provide compatible wheels. Run these
commands in PowerShell from the repository root:

```powershell
py -3.13 -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
python -m spacy download en_core_web_sm
python run.py
```

The first server start downloads/caches the Sentence-BERT model and builds the
local FAISS index; it can take several minutes and requires internet access for
those initial downloads. Later runs use the local model cache. The API listens
on `http://127.0.0.1:8000`.

In a **second PowerShell window**, from the repository root, serve the frontend:

```powershell
python -m http.server 5500 --directory frontend --bind 127.0.0.1
```

Open `http://127.0.0.1:5500` in a browser. API documentation is at
`http://127.0.0.1:8000/docs`. The application binds to loopback and is intended
for local development only. Do not expose it to a network or enter real or
sensitive case data.

If PowerShell blocks virtual-environment activation, run
`.\.venv\Scripts\python.exe -m pip install -r requirements.txt` and then
`.\.venv\Scripts\python.exe -m spacy download en_core_web_sm` and
`.\.venv\Scripts\python.exe run.py` without activating the environment.

---

## 🔮 Future Work
- Multilingual support (Hindi & regional languages)
- High Court / e-Courts pilot integration
- Federated learning for privacy
- Appellate-level explainability
- Voice-based case input

---

## 👨‍💻 Team
- **Tanya Singh**
- **Snigdha**
- **Yaswanthi**

**Mentor:** Divyanshu Kumar  
**Domain:** Artificial Intelligence in Law

---

## 📜 Disclaimer
NyayVandan is a **decision-support system** intended to assist legal professionals.  
It does **not replace judicial reasoning or authority**.

---

⭐ *If you find this project useful, please consider starring the repository!*
