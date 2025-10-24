# LLM Unit Test & Comment Generator

-----

## 🚀 Overview

This tool is an **AI-Powered Unit Test Generator** designed to streamline Test-Driven Development (TDD) by automatically generating comprehensive unit tests and adding clear, helpful comments to any given source code.

It leverages powerful Large Language Models, offering the flexibility to use both **Google's Gemini** and **OpenAI's GPT**. The entire application is packaged as a **Jupyter Notebook (`.ipynb`)** and uses **Gradio** to provide an interactive web interface for testing and analysis.

-----

## ✨ Features

  * **Multi-Model Support:** Choose between **Gemini-2.5-Flash** and **GPT-4o-mini** for generation.
  * **Automatic Language Detection:** The tool automatically detects the programming language of the input code.
  * **Idiomatic Testing:** Generates tests using the most standard framework for the detected language (e.g., `pytest`/`unittest` for Python, `Jest` for JavaScript, `JUnit` for Java, Go testing for Go).
  * **Comprehensive Coverage:** Tests are designed to cover all logical branches, edge cases, and typical use scenarios.
  * **High-Quality Comments:** Adds clear comments using standard documentation practices (docstrings, Javadoc, etc.) and includes a crucial comment explaining the purpose of each unit test method.
  * **Structured, Runnable Output:** The output is raw, runnable code with the unit tests presented first, followed by the commented version of the original source code.
  * **Integrated Test Execution:** Includes functionality to run the generated tests for multiple languages directly within the interface (Python, Java, JavaScript, C++, Go, and C\#).

-----

## 🛠️ Installation and Setup

### 1\. Prerequisites

You must have **Python** and **Jupyter** installed to run the notebook.

### 2\. Install Dependencies

Run the first cell of the Jupyter notebook to install the required Python packages:

```bash
pip install -q -U google-genai openai python-dotenv gradio requests
```

### 3\. API Key Configuration

The tool requires API keys for both LLM providers. Create a file named **`.env`** in the same directory as the notebook and add your keys:

```ini
OPENAI_API_KEY="your-openai-api-key-here"
GEMINI_API_KEY="your-gemini-api-key-here"
```

The notebook loads these keys automatically.

### 4\. Java Testing Dependency (Optional)

If you plan to test **Java** code, the tool attempts to automatically download the JUnit Standalone JAR file (`junit-platform-console-standalone-1.10.3.jar`). Ensure your environment can access this file.

-----

## 💻 Usage

1.  **Open the Notebook:** Open `llm_unit_test_generator_plus_comments.ipynb` in your Jupyter environment.
2.  **Run All Cells:** Execute all cells in the notebook sequentially. The final cell will launch the Gradio web interface.
3.  **Use the Interface:**
      * **Input Code:** Paste the code you want to test into the "Code to Test" box. You can also select a provided sample (e.g., `example1` for Python, `example2` for Java).
      * **Select Model:** Choose either "GPT" or "Gemini".
      * **Generate Tests:** Click the **"Generate Tests and Comments"** button. The LLM's output will stream into the "Generated Tests & Commented Code" box.
      * **Run Tests:** Click **"Run unit tests"** to execute the generated code in a temporary environment and view the results in the "Unit tests results" box.

-----

## 📝 Generation Guidelines

The LLMs are instructed to follow a strict set of rules to ensure high-quality and reliable output:

  * **Test-First, Code-Second:** Unit tests are always placed before the original source code (which is included in commented form).
  * **C++ Constraint:** For C++, external frameworks like GTest are prohibited. Tests are written using a `main()` function with `<iostream>` and `<cassert>`.
  * **JavaScript Modules:** For JavaScript, tests are generated using CommonJS (`require`) syntax.