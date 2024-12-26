# Shell-AI: let AI write your shell commands

[![PyPI version](https://badge.fury.io/py/shell-ai.svg)](https://pypi.org/project/shell-ai/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Forks](https://img.shields.io/github/forks/ricklamers/shell-ai)](https://github.com/ricklamers/shell-ai/network)
[![Stars](https://img.shields.io/github/stars/ricklamers/shell-ai)](https://github.com/ricklamers/shell-ai/stargazers)


Shell-AI (`shai`) is a CLI utility that brings the power of natural language understanding to your command line. Simply input what you want to do in natural language, and `shai` will suggest single-line commands that achieve your intent. Under the hood, Shell-AI leverages the [LangChain](https://github.com/langchain-ai/langchain) for LLM use and builds on the excellent [InquirerPy](https://github.com/kazhala/InquirerPy) for the interactive CLI.

![demo-shell-ai](https://github.com/ricklamers/shell-ai/assets/1309307/b4057165-5c23-46d4-b68e-00915b738dc3)

## Installation

You can install Shell-AI directly from PyPI using pip:

```bash
pip install shell-ai
```

Note that on Linux, Python 3.10 or later is required.

After installation, you can invoke the utility using the `shai` command.

## Usage

To use Shell-AI, open your terminal and type:

```bash
shai run terraform dry run thingy
```

Shell-AI will then suggest 3 commands to fulfill your request:
- `terraform plan`
- `terraform plan -input=false`
- `terraform plan`

## Features

- **Natural Language Input**: Describe what you want to do in plain English (or other supported languages).
- **Command Suggestions**: Get single-line command suggestions that accomplish what you asked for.
- **Cross-Platform**: Works on Linux, macOS, and Windows.
- **Azure Compatibility**: Shell-AI now supports Azure OpenAI deployments.

## Configuration

Shell-AI can be configured through environment variables or a config file located at `~/.config/shell-ai/config.json` (Linux/MacOS) or `%APPDATA%\shell-ai\config.json` (Windows).

### Environment Variables

- `OPENAI_API_KEY`: (Required) Your OpenAI API key, leave empty if you use ollama
- `GROQ_API_KEY`: (Required if using Groq) Your Groq API key
- `OPENAI_MODEL`: The OpenAI model to use (default: "gpt-3.5-turbo")
- `SHAI_SUGGESTION_COUNT`: Number of suggestions to generate (default: 3)
- `SHAI_SKIP_CONFIRM`: Skip command confirmation when set to "true"
- `SHAI_SKIP_HISTORY`: Skip writing to shell history when set to "true"
- `SHAI_API_PROVIDER`: Choose between "openai", "ollama", "azure", or "groq" (default: "groq")
- `SHAI_TEMPERATURE`: Controls randomness in the output (default: 0.05). Lower values (e.g., 0.05) make output more focused and deterministic, while higher values (e.g., 0.7) make it more creative and varied.
- `CTX`: Enable context mode when set to "true" (Note: outputs will be sent to the API)
- `OLLAMA_MODEL`: The Ollama model to use (default: "phi3.5")
- `OLLAMA_API_BASE`: The Ollama endpoint to use (default: "http://localhost:11434/v1/")

### Config File Example

```json
{
  "OPENAI_API_KEY": "your_openai_api_key_here",
  "OPENAI_MODEL": "gpt-3.5-turbo",
  "SHAI_SUGGESTION_COUNT": "3",
  "CTX": true
}
```


### Config Example for Ollama
```json
   {
   "OPENAI_API_KEY":"",
   "SHAI_SUGGESTION_COUNT": "3",
   "SHAI_API_PROVIDER": "ollama",
   "OLLAMA_MODEL": "phi3.5",
   "OLLAMA_API_BASE": "http://localhost:11434/v1/",
   "SHAI_TEMPERATURE": "0.05"
   }
```
The application will read from this file if it exists, overriding any existing environment variables.

Run the application after setting these configurations.

### Using with Groq

To use Shell AI with Groq:

1. Get your API key from Groq
2. Set the following environment variables:
   ```bash
   export SHAI_API_PROVIDER=groq
   export GROQ_API_KEY=your_api_key_here
   export GROQ_MODEL=llama-3.3-70b-versatile
   ```

## Contributing

This implementation can be made much smarter! Contribute your ideas as Pull Requests and make AI Shell better for everyone.

Contributions are welcome! Please read the [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

Shell-AI is licensed under the MIT License. See [LICENSE](LICENSE) for details.
