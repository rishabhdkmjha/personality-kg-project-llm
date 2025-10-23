# personality-kg-project-llm

# LLM-Powered Personality Knowledge Graph

This project is a Python-based solution that constructs a knowledge graph from unstructured text to model the personality traits of subjects mentioned in the document. The entire workflow, from data generation to graph construction, is powered and assisted by a Large Language Model (LLM).

This repository represents the final deliverable for the "LLM Reasoning & Personality Knowledge Graph Challenge."

## Problem Statement

The objective is to develop a Python solution that takes a text document, extracts entities and relationships, and builds a knowledge graph. A key requirement is to model the personality of the subjects within this graph, based on a recognized psychological framework.

## My Approach

This solution uses an LLM-driven pipeline to transform unstructured text into a structured knowledge graph stored in a Neo4j database.

1.  **Theoretical Framework:** The system is built upon the **Big Five (OCEAN) personality model**, providing a robust, empirically validated schema for personality analysis.[1, 2]
2.  **Data Strategy:** Lacking a pre-annotated dataset, this project utilizes an LLM to generate **synthetic narratives** based on specific personality profiles. The same LLM is then used to create a "gold standard" set of annotations for development and evaluation.
3.  **Extraction Pipeline:** A hybrid approach is used. An open-source LLM (`Llama3`) running for free on Google Colab via **Ollama** performs the core semantic extraction of entities and relationships. This process is orchestrated using the **LangChain** framework, which provides modular tools for building LLM-powered applications.
4.  **Storage and Visualization:** The extracted graph data is populated into a **Neo4j AuraDB** (a free cloud-hosted graph database), allowing for powerful querying and visualization of the final knowledge graph.

## Tech Stack

*   **Language:** Python
*   **LLM Orchestration:** LangChain
*   **LLM Provider:** Ollama (running Llama 3 on Google Colab)
*   **Graph Database:** Neo4j AuraDB
*   **Core Libraries:** `langchain-experimental`, `langchain-community`, `langchain-ollama`, `neo4j`

## Setup and Usage

1.  **Clone the Repository:**
    ```bash
    git clone <your-repo-url>
    cd personality-kg-project
    ```

2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Set Up Environment:**
    *   This project was developed in a Google Colab notebook. Open the `notebooks/development_notebook.ipynb` file in Colab.
    *   **Enable GPU:** For best performance, change the runtime type to **T4 GPU** (`Runtime` > `Change runtime type`).
    *   Set up a free Neo4j AuraDB instance and get your connection credentials (URI, Username, Password).
    *   Update the credentials in the notebook where specified.

4.  **Run the Pipeline:**
    *   Execute the cells in the notebook sequentially. The notebook is divided into logical steps:
        1.  Setup and Start Ollama Server
        2.  Run the Extraction Pipeline & Populate Graph

## Repository Contents

*   `/notebooks/development_notebook.ipynb`: The main Colab notebook containing the end-to-end code.
*   `/data/synthetic_data.json`: The synthetic data generated and used for development.
*   `report.md`: A detailed report explaining design choices, insights, and limitations.
*   `README.md`: This file.
*   `requirements.txt`: A list of required Python packages.
