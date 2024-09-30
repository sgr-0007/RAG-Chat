
# RAG-LangchainAI-Chatbot

A chatbot application built using [LangChain](https://github.com/hwchase17/langchain) for retrieval-augmented generation (RAG) with support for PDF document reading and interaction. This application leverages the power of the LangChain framework, OpenAI’s GPT models, and streaming responses to handle complex queries efficiently, providing contextual answers based on the contents of provided PDFs.

## Features

- **LangChain Integration**: Uses LangChain to interact with OpenAI GPT models.
- **PDF Support**: Load and process PDF documents to extract and use the content as context for the chatbot.
- **Streaming Responses**: Provides real-time streaming responses for a smooth conversational experience.
- **Memory Handling**: Retains message history to maintain context across multiple interactions.
- **Flexible Prompting**: Utilizes a prompt template to format conversations and context for the model.

## Tech Stack

- **Frontend**: React with TypeScript and TailwindCSS.
- **Backend**: Node.js with LangChain, OpenAI API.
- **Other Libraries**: 
  - **LangChain** for conversational context.
  - **PDFLoader** for reading PDF content.
  - **TailwindCSS** for responsive design.
  - **Vercel's AI Package** for chat functionality.

## Getting Started

### Prerequisites

Ensure you have the following installed:

- Node.js (version 16.x or higher)
- npm (version 6.x or higher)
- OpenAI API key (required for GPT model access)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sgr-0007/RAG-LangchainAI-Chatbot.git
   cd RAG-LangchainAI-Chatbot
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Configure environment variables**:

   Create a `.env` file in the root directory and add your OpenAI API key:
   ```bash
   OPENAI_API_KEY=your-openai-api-key
   ```

4. **Start the development server**:
   ```bash
   npm run dev
   ```

   The app should now be running at `http://localhost:3000`.

### File Structure

- **`public/`**: Static files.
- **`src/`**: Contains the main source code, including:
  - `pages/`: Page components and routing for the app.
  - `components/`: UI components such as the chat input and button.
  - `data/`: Directory for loading PDF files (e.g., `Rdf-Report.pdf`).
- **`utils/`**: Utility functions like `formatDocumentsAsString`.
- **`api/`:** The endpoint for handling requests.

### Usage

1. **Start a Conversation**:
   Open the application and type your question into the chat input box.

2. **PDF Context**:
   The chatbot uses the content of the PDF (e.g., `Rdf-Report.pdf`) as context for answering questions. You can ask questions relevant to the document's content, and if the answer is found in the document, the chatbot will respond accordingly. If not, it will politely mention that the information is not available.

3. **Streaming**:
   The responses from the chatbot are streamed in real-time for a more interactive experience.

### Example Questions

- "What are the key takeaways from the document?"
- "Can you summarize the section about X in the PDF?"
- "Do you have information on Y in the report?"

## Customization

### Modifying the Prompt Template

You can update the prompt used for interacting with the model in the `TEMPLATE` string within the `POST` function:

```ts
const TEMPLATE = `Answer the user's questions based only on the following context. If the answer is not in the context, reply politely that you do not have that information available.:
==============================
Context: {context}
==============================
Current conversation: {chat_history}

user: {question}
assistant:`;
```

### Loading a Different PDF

To load and query a different PDF, update the path in the `PDFLoader`:

```ts
const loader = new PDFLoader("src/data/your-pdf-file.pdf");
```

Replace `"src/data/your-pdf-file.pdf"` with the path to your own PDF file.

## Troubleshooting

### Common Issues

- **API Key Error**: Ensure your OpenAI API key is set correctly in the `.env` file.
- **PDF Not Loading**: Verify that the path to the PDF is correct and accessible.
- **Response Delay**: GPT responses might be slow if using a high-latency API model or when streaming large responses.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repo.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature/your-feature`).
6. Open a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for more details.

## Contact

For questions or suggestions, feel free to reach out to the repository owner.
