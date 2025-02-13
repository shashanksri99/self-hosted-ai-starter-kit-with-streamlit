FROM python:3.9-slim

WORKDIR /app

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/shashanksri99/self-hosted-ai-starter-kit-with-streamlit.git .
#COPY . .

WORKDIR /app/self-hosted-ai-starter-kit-with-streamlit/Streamlit/setupFiles

RUN pip3 install -r /app/self-hosted-ai-starter-kit-with-streamlit/Streamlit/setupFiles/requirements.txt

EXPOSE 8501

HEALTHCHECK CMD curl --fail http://localhost:8501/_stcore/health

WORKDIR /app/self-hosted-ai-starter-kit-with-streamlit/Streamlit/developmentFiles

ENTRYPOINT ["streamlit", "run", "streamlit_app.py", "--server.port=8501", "--server.address=0.0.0.0"]