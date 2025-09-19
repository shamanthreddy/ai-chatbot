# AI Chatbot with MongoDB and LangChain4J

A Spring Boot application that implements a question-answering chatbot using LangChain4J, MongoDB Atlas, and OpenAI's GPT models. The application provides a REST API to ask questions and get AI-generated answers based on the content stored in MongoDB.

## Prerequisites

- MongoDB Atlas cluster
- OpenAI API key

## Setup

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ai-chatbot
   ```

2. **Configure environment variables**
   Create an `application.properties` file in `src/main/resources/` with the following content:
   ```properties
   # MongoDB Configuration
   app.mongodb.url=your_mongodb_connection_string
   app.mongodb.db-name=your_database_name
   
   # OpenAI Configuration
   app.openai.apiKey=your_openai_api_key
   ```

   Replace the placeholders with your actual MongoDB connection string and OpenAI API key.

3. **Build the application**
   ```bash
   mvn clean install
   ```

## Running the Application

1. **Start the application**
   ```bash
   mvn spring-boot:run
   ```

2. **Access the API**
   The application will start on port 8080. You can interact with the chatbot using the following endpoint:
   ```
   GET /chat-bot?question=Your question here
   ```

   Example:
   ```bash
   curl "http://localhost:8080/chat-bot?question=What is the best programming language?"
   ```


## Configuration

The main configuration is in `ChatBotConfiguration.java`, which sets up:

- MongoDB client and database connection
- OpenAI model configuration
- Embedding store for vector search
- Content retriever for document search

## Testing

Run the test class to verify the setup:
```bash
mvn test
```

## Security Considerations

- Always keep your OpenAI API key secure
- Use environment variables or a secrets manager for sensitive data
- Implement proper authentication and authorization
- Rate limit your API endpoints
- Monitor API usage and set up alerts for unusual activity

## Troubleshooting

1. **Connection Issues**
   - Verify your MongoDB connection string
   - Check if your IP is whitelisted in MongoDB Atlas
   - Ensure the database and collection exist

2. **API Key Issues**
   - Verify your OpenAI API key is valid
   - Check if you have sufficient credits

3. **Performance Issues**
   - Check the size of your embeddings
   - Monitor response times
   - Consider caching frequent queries
