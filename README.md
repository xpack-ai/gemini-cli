# Gemini CLI \<> XPack

[![Gemini CLI CI](https://github.com/google-gemini/gemini-cli/actions/workflows/ci.yml/badge.svg)](https://github.com/google-gemini/gemini-cli/actions/workflows/ci.yml)

![Gemini CLI Screenshot](./docs/assets/xpack/gemini-screenshot.png)

## Introduction

This repository showcases the powerful integration of **Gemini CLI** with **XPack.AI**, demonstrating how you can extend the capabilities of your AI agent by connecting to thousands of ready-to-use tools worldwide. Building upon the robust foundation of the [Gemini CLI](https://github.com/google-gemini/gemini-cli), this project provides a practical example of configuring its Model Context Protocol (MCP) service to leverage XPack's extensive service marketplace.

## What is Gemini CLI?

[Gemini CLI](https://github.com/google-gemini/gemini-cli) is a command-line AI workflow tool designed to connect to your existing tools, understand your codebase, and accelerate your development workflows. It empowers developers to:

- Query and edit large codebases.
- Generate new applications from various inputs.
- Automate operational tasks.
- Integrate with external capabilities via MCP servers.

## What is XPack\.AI?

[XPack.AI](https://xpack.ai/) is a platform that enables AI agents to connect to a vast ecosystem of global services and tools through a unified Model Context Protocol (MCP). With XPack, you can effortlessly expand your AI agent's functionalities, accessing diverse APIs and services across various domains like finance, logistics, messaging, and more, all in under a minute.

## Gemini CLI + XPack: Bridging AI with Global Services

This project focuses on demonstrating how to configure Gemini CLI to utilize XPack as an MCP server. By doing so, your Gemini CLI instance gains immediate access to XPack's rich collection of tools, allowing you to:

- **Access a diverse range of services:** From financial data to image processing, integrate capabilities that were previously out of reach.
- **Accelerate development:** Rapidly prototype and build AI-powered solutions by leveraging pre-built tools.
- **Streamline workflows:** Automate complex tasks by combining Gemini CLI's intelligence with XPack's external service integrations.

## Quickstart

### Install Gemini CLI

This section outlines the basic setup for Gemini CLI. For detailed instructions on Gemini CLI installation and authentication, please refer to the [official Gemini CLI documentation](https://github.com/google-gemini/gemini-cli).

1. **Prerequisites:** Ensure you have [Node.js version 18](https://nodejs.org/en/download) or higher installed.
2. **Run the CLI:** Execute the following command in your terminal:

   ```bash
   npx https://github.com/xpack-ai/gemini-cli
   ```

   Or install it with:

   ```bash
   npm install -g @google/gemini-cli
   gemini
   ```

3. **Pick a color theme**
4. **Authenticate:** When prompted, sign in with your personal Google account. This will grant you up to 60 model requests per minute and 1,000 model requests per day using Gemini.

### Configure XPack MCP

To connect your Gemini CLI to XPack, you need to configure an MCP server entry in your Gemini CLI settings. This allows Gemini CLI to discover and utilize the tools available through XPack.

1.  **Obtain your XPack Auth Key:**
    *   Visit [XPack.AI](https://xpack.ai/) and sign up for an account.
    *   Generate your Auth key from your XPack dashboard.

    ![XPack.ai Dashboard](./docs/assets/xpack/xpack-dashboard.png)


2.  **Configure Gemini CLI `settings.json`:**
    * Create or open the `.gemini/settings.json` file in your project's root directory or at the global level (`~/.gemini/settings.json`). 
    * Add the following `mcpServers` configuration block, replacing **`YOUR_XPACK_AUTH_KEY`** with your actual XPack Auth key:

    ```json
    {
      "mcpServers": {
        "xpack-mcp-market": {
          "type": "sse",
          "url": "https://api.xpack.ai/v1/mcp?apikey=YOUR_XPACK_AUTH_KEY"
        }
      }
    }
    ```


3.  **Verify Connection:**
    After configuring, restart your Gemini CLI. You can verify the connection and discovered tools using the `/mcp list` command within the Gemini CLI:

    ```bash
    /mcp list
    ```

    You should see `xpack-mcp-market` listed with a `Ready` status and a list of available tools.

    ![Gemini CLI Configure XPack](./docs/assets/xpack/connected_xpack.png)

## Examples

Once the CLI is running, you can start interacting with Gemini from your shell.

You can start a project from a new directory:

```sh
cd new-project/
gemini
> Write me a Gemini Discord bot that answers questions using a FAQ.md file I will provide
```

Or work with an existing project:

```sh
git clone https://github.com/xpack-ai/gemini-cli
cd gemini-cli
gemini
> Give me a summary of all of the changes that went in yesterday
```

### Next steps

- Explore more [XPack Services](https://xpack.ai/service) to discover additional integration possibilities.
- Learn how to [contribute to or build from the source](./CONTRIBUTING.md).
- Explore the available **[CLI Commands](./docs/cli/commands.md)**.
- If you encounter any issues, review the **[Troubleshooting guide](./docs/troubleshooting.md)**.
- For more comprehensive documentation, see the [full documentation](./docs/index.md).
### Troubleshooting

Head over to the [troubleshooting](docs/troubleshooting.md) guide if you're having issues.


## Popular Tasks

This section provides practical examples of how users who prefer a CLI-style workflow can leverage Gemini CLI with XPack as an personal AI assistant for various tasks.

### Analyze YouTube comments and provide suggestions to improve video creation
Easily analyze YouTube video comments to understand audience sentiment and get suggestions for improving your content.

```bash
gemini
> Please use xpack-mcp-server to read the comments on this YouTube video: https://www.youtube.com/watch?v=LPZh9BOjkQs, analyze the sentiment of the feedback, and recommend improvements for the video.
```


![Analyze YouTube comments Image](./docs/assets/xpack/demo-youtube-analysis.png)

### Current Gold Price and Influencing Factors
Quickly check the latest gold price and discover key factors that may affect future trends.

```bash
gemini
> Please use xpack-mcp-server to look up the current real-time price of gold and provide specific factors that may impact its price in the future.
```

![Current Gold Price Image](./docs/assets/xpack/demo-gold-monitor.png)

### Remove Image Background
Instantly remove the background from any image for clean, professional results.

```bash
gemini
> Please use xpack-mcp-server to remove the background from this image (@/docs/assets/xpack/stunning-quality-product.png) .
```
![remove bg origin image](./docs/assets/xpack/stunning-quality-product.png)

```bash
gemini
> Please remove the background from this image.
```

![A yellow handbag with the background removed](./docs/assets/xpack/demo-remove-bg.png)

### Uninstall

Head over to the [Uninstall](docs/Uninstall.md) guide for uninstallation instructions.

## Terms of Service and Privacy Notice

For details on the terms of service and privacy notice applicable to your use of Gemini CLI, see the [Terms of Service and Privacy Notice](./docs/tos-privacy.md).
