# Standard-RAG-Pipeline
<img width="1840" height="531" alt="Screenshot 2025-08-15 170702" src="https://github.com/user-attachments/assets/21c642a5-e886-42a6-a3f1-590e4da37b9a" />


This repository implements a standard Retrieval-Augmented Generation (RAG) pipeline for automated question answering using PDF documents as the data source. The workflow involves loading and parsing PDF, splitting the text into meaningful chunks, generating semantic embeddings with transformer models, and storing these in a ChromaDB vector database for efficient retrieval. Relevant document sections are retrieved in response to user queries and supplied to a large language model (Groq) via custom prompts to produce accurate, context-aware answers. The notebook provides clear cell-by-cell explanations, making it a comprehensive resource for building and understanding RAG workflows.

## 1. **Install Dependencies**
 
The first step involves installing all necessary Python packages required for the Retrieval-Augmented Generation (RAG) pipeline. This includes libraries for language modeling (LangChain and related tools), vector storage (ChromaDB), document parsing (pdfminer.six), embedding models (sentence-transformers, transformers), and the Groq language model. Ensuring all dependencies are installed allows the subsequent steps to execute seamlessly.

---

## 2. **Imports**

This cell imports all needed modules and classes from the installed packages. This includes document loaders, text splitters, vector stores, embeddings, chat models, schema definitions, prompt templates, and output parsers. These imports provide the functionality necessary for PDF parsing, text processing, vectorization, semantic search, and LLM interaction.

---

## 3. **Load PDF Path**
 
Here, the pipeline ingests the raw data by loading a PDF file. The document loader reads and parses the PDF, converting its contents into a format that can be processed programmatically. This step is crucial for getting the source material into the pipeline for further analysis.

---

## 4. **Chunking**

The loaded document is split into manageable text chunks using a recursive character-based splitter. Chunking is critical in RAG pipelines, as it enables efficient context retrieval by breaking down large documents into smaller, semantically coherent sections.

---

## 5. **Inspect Chunks**

The stage prints out some sample chunks to verify the text splitting process. This helps in validating that the document has been segmented correctly and that each chunk is meaningful for subsequent vectorization and retrieval.

---

## 6. **Count Chunks**
 
This step outputs the total number of chunks created from the document. Knowing the count is useful for understanding the granularity and scale of the data available for retrieval.

---

## 7. **Create Embeddings**
 
Embeddings are generated for each chunk using a pre-trained sentence transformer model. This step converts textual data into high-dimensional vectors, making it possible to perform semantic similarity searches and efficient retrieval.

---

## 8. **Storing Embeddings in ChromaDB**

The embeddings and corresponding document chunks are stored in a ChromaDB vector database. This allows for fast and scalable similarity-based retrieval, enabling the RAG pipeline to fetch relevant contexts for queries.

---

## 9. **Collection Count**

This cell verifies that all document chunks have been successfully stored in ChromaDB by counting the entries. It's an integrity check for the ingestion and storage process.

---

## 10. **Inspect Vector Collection**
 
Here, the stored vectors and their metadata are inspected to ensure correct storage and association of data. This is useful for debugging and understanding the internal structure of the vector database.

---

## 11. **Set Retriever**

The retriever is set up using the ChromaDB vector store. It is configured to fetch the top-k most relevant document chunks based on semantic similarity to a given query, forming the backbone of the RAG retrieval process.

---

## 12. **Groq API Key Setup**

This step securely inputs and sets up the API key for accessing the Groq language model. The API key is required to interact with the hosted LLM service for generating answers.

---

## 13. **Initialize Groq Chat Model**

The Llama model is initialized with specified parameters. This model will be used to generate final answers conditioned on retrieved context.

---

## 14. **Custom Prompt Template**

A custom prompt template is defined for question-answering tasks. The template ensures that the model uses only the retrieved context to answer the question and that answers are detailed, relevant, and devoid of extraneous commentary.

---

## 15. **Document Formatting Utility**

A utility function is created to format the retrieved document chunks into a single string, suitable for feeding into the prompt template. This ensures that the context provided to the language model is coherent and well-structured.

---

## 16. **RAG Chain Construction**

The RAG chain is constructed by combining the retriever, formatter, prompt, LLM, and output parser into a single sequential pipeline. This orchestrates the end-to-end flow of data from question to answer.

---

## 17. **Retrieve Documents for a Query**

This step demonstrates the retrieval process by fetching the most relevant chunks for a sample query. It prints the context that will be used to answer the question, showcasing how the retrieval system selects supporting evidence.

---

## 18. **RAG Output Generation**

The pipeline is executed by invoking the RAG chain with a user question. The retrieved context and the question are processed by the LLM to generate a detailed, contextually-grounded answer.

---

## 19. **Additional Retrieval Example**

Further context is retrieved for another sample question, illustrating the pipeline's flexible retrieval capabilities across different queries.

---

## 20. **Additional Output Generation**

The RAG chain is invoked again to answer the new query, demonstrating robust output generation for varied questions using the same pipeline.

---

## 21. **Retrieval for Regression Analysis Query**

This cell retrieves relevant context specifically for a regression analysis query, further showing the pipeline’s ability to adapt to complex, domain-specific questions.

---

## 22. **Regression Analysis Answer Generation**

The pipeline produces a detailed, context-based answer for the regression analysis question, exemplifying comprehensive output generation capabilities.

---

## 23. **Retrieval for Regression Line Equation**

Context relevant to the equation of the regression line is fetched, illustrating precise and focused retrieval for specialized technical questions.

---

## 24. **Regression Line Equation Output**

The RAG chain generates and outputs a concise, contextually-supported answer for the regression line equation, rounding out the pipeline’s functionality from data ingestion to answer generation.
