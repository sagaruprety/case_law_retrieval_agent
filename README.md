# How To Build A Legal Case Discovery Search Engine using Large Language Models

## Introduction

Finding legal cases is an extremely important task that lawyers do, and also the most time consuming and labor-intensive. There is a vast trove of judicial decisions data which needs to be searched, and existing softwares mostly offer boolean and keyword-based search approaches.

In this blog we build a simple way for lawyers to upload case documents, and build a simple AI application that allows for search and analyses of legal case documents related to a given new case scenario. We utilize all open-source components - Mistral AI model, Qdrant vector database, and the Langchain library.

To run the code, one needs to download the Mistral AI model (Mistral-7B) in either the local machine or a cloud.  Although we quantize the model and reduce its size, it would need a GPU with at least 16 GB of RAM. I would recommend using Google Colab for running the code, as their free-tier GPU can take the above load easily. 

## Why Legal Case Discovery Search?

Legal case discovery is the process of identifying and gathering relevant information to support a given legal case. Technically termed as Case law retrieval, it is needed to analyze judicial precedents and decisions so that lawyers can advise their clients on a similar legal case. Case law is one of two sources of law, along with statutes. Although statutes are limited in their size and slowly amended or expanded, case law forms a rapidly and ever expanding source. This process can be time-consuming and labor-intensive, especially when dealing with large volumes of data. Large language models (LLMs) can help expedite this process by semantically searching for keywords to match a broad yet relevant set of case precedents and statutes. This can not only help legal professionals but also benefit a layperson who can get some preliminary understanding of similar cases and their outcomes, before deciding to proceed with their own case and hiring a lawyer.

## Architecture

This tutorial utilizes LLMs and the Retrieval Augmented Generation (RAG) architecture to build a search agent over case law documents. We build a traditional retrieval component using vector databases to filter down the large number of case documents, based on a user query. Then those filtered document chunks are passed on to the LLM, along with the query. The reasoning and semantic understanding capabilities of LLMs helps them the exact answer to the query. 

### About Mistral

Mistral-7B is a relatively recent large language model which is open-source and developed by Mistral AI, a french startup, which has gained attention because of it outperforming the popular Llama2 models. Specifically, the 7 billion parameter version of Mistral is reported to outperform the 13 Billion and 34 Billion parameter versions of Llama2, which is a significant milestone in generative AI, as this means improved latency without sacrificing model performance.

### About Qdrant

Qdrant is an open-source vector search engine that enables fast and efficient similarity search. It is designed to work with high-dimensional data, making it suitable for use with large language models like Mistral. The integration of Qdrant in the architecture aims to enhance the search capabilities for legal case discovery, allowing for quick and accurate retrieval of relevant information from a large corpus of legal documents.

### About Langchain

Langchain is a blockchain-based platform tailored for storing and sharing language data. Its decentralized and secure nature makes it an ideal solution for preserving the integrity and confidentiality of legal case data processed by large language models. By incorporating Langchain into the architecture, the blog will highlight the importance of data security and integrity in legal case discovery search, especially when leveraging advanced language models like Mistral.

### About Dataset

The dataset used in this tutorial was constructed as part of the Artificial Intelligence for Legal Assistance) Track at FIRE 2019 conference, which is an important conference in the discipline of Information Retrieval. It can be downloaded from here. It contains thousands of case law documents, but one can consider a subset of 500 documents (files c1.txt to c500.txt in the Object_casedocs directory) for the purpose of this tutorial.
