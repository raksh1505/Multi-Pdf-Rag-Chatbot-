# 🤖 Multi-PDF RAG Chatbot

An AI-powered conversational agent built using the **Retrieval-Augmented Generation (RAG)** architecture. This application allows users to upload **multiple PDF documents** simultaneously, processes and indexes their contents, and enables context-aware, multi-turn Q&A streaming directly through an intuitive user interface.

---

## 🚀 Features

- **Multi-Document Processing:** Upload and parse multiple large PDF files at once.
- **RAG Architecture:** Leverages semantic search to pull relevant context chunks from the documents before generating answers, preventing LLM hallucinations.
- **Conversational Memory:** Remembers past exchanges in the session for seamless, multi-turn conversations.
- **Source Attribution:** Shows exactly which document sections or pages were used to construct the answer.
- **Streaming Responses:** Provides real-time, token-by-token textual generation for an optimized user experience.

---

## 🛠️ Tech Stack

- **Frontend/UI:** [Streamlit](https://streamlit.io) (or Gradio)
- **LLM Orchestration:** [LangChain](https://langchain.com) (or LlamaIndex)
- **Embedding Model:** `sentence-transformers/all-MiniLM-L6-v2` (or OpenAI / HuggingFace)
- **Vector Database:** [FAISS](https://github.com) (or ChromaDB)
- **Document Parsing:** `PyPDF` (or `PyMuPDF`)
- **Language Model:** OpenAI GPT-4o / Google Gemini / Ollama (Local)

---

## 📂 Project Structure

```text
multi-pdf-rag-chatbot/
│
├── .streamlit/
│   └── config.toml          # Streamlit UI configurations
├── src/
│   ├── __init__.py
│   ├── database.py          # Vector store setup & indexing
│   ├── pdf_processor.py     # PDF extraction & text chunking
│   └── rag_pipeline.py      # LLM orchestration & chain memory
│
├── .env.example             # Template for environment variables
├── .gitignore               # Git omission rules
├── app.py                   # Main application entry point
├── README.md                # Project documentation
└── requirements.txt         # Python dependencies
```

---

## ⚙️ Installation & Setup

### Prerequisite
Ensure you have **Python 3.9+** installed on your system.

### 1. Clone the Repository
```bash
git clone https://github.com
cd multi-pdf-rag-chatbot
```

### 2. Create a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Environment Configuration
Create a `.env` file in the root directory and append your API keys:
```env
OPENAI_API_KEY=your_openai_api_key_here
# If using Gemini or other providers:
# GEMINI_API_KEY=your_gemini_api_key_here
```

---

## 💻 Running the Application

Launch the web interface locally using the following command:

```bash
streamlit run app.py
```

Once running, open your browser and navigate to the local host address provided in the terminal (usually `http://localhost:8501`).

---

## 💡 How It Works

1. **Document Ingestion:** The user uploads multiple PDF files via the sidebar.
2. **Text Chunking:** The PDFs are parsed, and text is divided into manageable semantic chunks using a recursive character text splitter.
3. **Embedding & Vector Storage:** Chunks are converted into vector embeddings and stored inside a local vector database index.
4. **Retrieval & Prompting:** When a user asks a question, the vector store performs a similarity search to fetch relevant fragments, which are appended into a system prompt.
5. **Generation:** The context-rich prompt is sent to the LLM to deliver a precise, grounded answer.

---

## 🤝 Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or features you would like to add.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.
