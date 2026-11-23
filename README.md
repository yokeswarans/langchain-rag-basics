# LangChain RAG Basics 🦜🔗

Beginner-friendly Jupyter notebooks for learning **LangChain** and the basics of **RAG (Retrieval-Augmented Generation)** step by step.

> 📌 **Note:** This repo is a **1000-foot view of LangChain**: just the basic building blocks of RAG (loading, splitting, embedding and storing data).
> It's not a full application yet. It's my foundation before going deeper into chains, retrievers and complete RAG apps.

## What is RAG?

LLMs only know what they were trained on. **RAG** gives them access to *your own* data: relevant pieces of your documents are retrieved and passed to the LLM together with the question.

```
            ┌─────────── Indexing (done once) ───────────┐
Documents ➜ │  Load  ➜  Split  ➜  Embed  ➜  Store (Vector DB) │
            └─────────────────────────────────────────────┘
                                                  │
Question  ➜  Embed  ➜  Retrieve similar chunks ◀──┘  ➜  LLM + Prompt  ➜  Answer
```

## Project Structure

```
Langchain/
├── 1-RAG-Fundamentals/            # RAG building blocks with LangChain
│   ├── 01-DataIngestion.ipynb     # Document loaders: Text, PDF, Web
│   ├── 02-TextSplitter.ipynb      # Recursive, HTML and JSON splitters
│   ├── 03-Embeddings.ipynb        # OpenAI, Ollama, Hugging Face + Chroma
│   ├── 04-VectorStore-FAISS.ipynb # FAISS: search, retriever, save/load
│   ├── speech.txt                 # Sample text data
│   └── Attention.pdf              # Sample PDF ("Attention Is All You Need")
├── .env.example                   # Template for API keys
├── .gitignore
├── requirements.txt
└── README.md
```

## Notebooks

| # | Notebook | Concepts |
|---|---|---|
| 01 | [Data Ingestion](1-RAG-Fundamentals/01-DataIngestion.ipynb) | `Document`, `TextLoader`, `PyPDFLoader`, `WebBaseLoader`, BeautifulSoup filtering |
| 02 | [Text Splitting](1-RAG-Fundamentals/02-TextSplitter.ipynb) | `chunk_size`, `chunk_overlap`, `RecursiveCharacterTextSplitter`, `HTMLHeaderTextSplitter`, `RecursiveJsonSplitter` |
| 03 | [Embeddings](1-RAG-Fundamentals/03-Embeddings.ipynb) | `embed_query` vs `embed_documents`, OpenAI / Ollama / Hugging Face embeddings, Chroma |
| 04 | [Vector Store: FAISS](1-RAG-Fundamentals/04-VectorStore-FAISS.ipynb) | `similarity_search`, scores, retrievers, saving and loading an index |

## Setup

**1. Create an environment and install dependencies**
```bash
conda create -n langchain python=3.11 -y
conda activate langchain
pip install -r requirements.txt
```

**2. Add your API keys**
```bash
cp .env.example .env    # then edit .env with your real keys
```
| Variable | Needed for |
|---|---|
| `OPENAI_API_KEY` | OpenAI embeddings |
| `HF_TOKEN` | Hugging Face (optional for public models) |

**3. (Optional) Local models with Ollama**: install [Ollama](https://ollama.com), then:
```bash
ollama pull nomic-embed-text
```

**4. Run the notebooks** in order (01 ➜ 04). Each notebook reads its data files from its own folder, so open/run them from inside `1-RAG-Fundamentals/`.

## Tech Stack
LangChain · OpenAI · Ollama · Hugging Face (sentence-transformers) · ChromaDB · FAISS · Jupyter

## Roadmap
- [x] Data ingestion (document loaders)
- [x] Text splitting
- [x] Embeddings
- [x] Vector stores (Chroma, FAISS)
- [ ] LangChain core: chat models, prompt templates, output parsers, LCEL chains
- [ ] Complete RAG chain (retriever + prompt + LLM)
- [ ] Conversational RAG with chat history
