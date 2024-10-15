# Content Generation for YouTube summarization
Content generation and summarization using Azure Open AI

#**Case Study: Youtube Video Summarization**

With the advent of Large Language Models (LLMs), the market has seen an influx of standalone tools and products built on these technologies. Among the pioneering applications were **YouTube summarization tools** such as Monica, Notta, and NoteGPT, and summarization. These products have significantly enhanced user productivity across various use cases.

Today, we aim to replicate the functionality of such products.

## **Problem Definition and Approach**


Company **Great Learning** produces a vast amount of educational content, but the volume of content can overwhelm their audience. Many users seek quick, concise summaries to determine whether they want to engage with the full content. Currently, Great Learning's team manually summarizes content, which is time-consuming and prone to inconsistencies. The company needs an efficient, automated solution to generate accurate and engaging summaries. By doing so, they can save time, reduce costs, and enhance user satisfaction.

This notebook needs to be executed with a GPU runtime since we load a transformer model (for BERT scorer) to disk and use it to evaluate text-to-text tasks. Transformer models benefit from parallel execution offered by a GPU runtime and can have a significant impact on execution times (for e.g., code in this notebook runs up to 4 times faster witha GPU). Follow the screenshots below to create a GPU runtime on a Colab instance

Great Learning wants to convert there online sessions, webinars and podcast to audio file which can be used later to generate transcript. We will be using **pytube** library to convert youtube video into audio file and **OpenAI Whisper** library for the transcript generation.

### What is Whisper AI?

**Whisper AI** is developed by OpenAI for automatic speech recognition (ASR), which transcribes spoken language into text. It was trained on a massive dataset of 680,000 hours of multilingual, supervised data from the internet, allowing it to handle a wide variety of accents, vocabularies, and topics. Whisper breaks down input speech into phonetic components and compares them against its knowledge base to determine the most probable sequence of words, enabling it to transcribe speech with high accuracy. The Whisper model has diverse applications including transcribing meetings, converting educational materials into text, enabling voice assistants, and automatic captioning

You can read more about whisper below:
- <a href="https://openai.com/index/whisper/">OpenAI Whisper</a>
- <a href="https://github.com/openai/whisper/blob/main/model-card.md">Model Types</a>

### Convert YouTube Video to Audio File
**Business Perspective:** Great Learning has a large repository of video content on YouTube and other platforms. To summarize these videos, the first step is to extract the audio. Audio files are easier and faster to process for transcription compared to video files. Using **pytube**, Great Learning can download videos from YouTube and convert them into audio files in a business-friendly manner.


***Steps involved:***
1.Data Preparation
2.Devise prompts
3.Evaluation
4.Improve the prompt-COT
