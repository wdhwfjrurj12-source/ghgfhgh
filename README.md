# Windows MCP Server Launcher

A PowerShell launcher for running a local MCP server on Windows and exposing it through a temporary Cloudflare Quick Tunnel.

> **Project status:** This project has not been independently security-audited. Review the source before running it. Do not use it on a machine or with accounts you cannot afford to expose.

## What it does

The launcher is designed to:
1. Write the bundled MCP server script to a local application-data folder.
2. Locate Python and install the required Python packages (including `mcp`, `starlette`, and `uvicorn`) if needed.
3. Download the Cloudflare `cloudflared` client if it is not already present.
4. Start the local server and create a Cloudflare Quick Tunnel, which provides a temporary public URL.
5. Set the public base URL and a newly generated password in environment variables for the server process.

Exact behavior depends on the version of the launcher you run. Inspect the PowerShell source before execution.

## Security and privacy notes

- **A public tunnel exposes a service outside your computer.** Only run this if you understand which MCP tools and data the server makes available.
- A password is not a substitute for reviewing authentication, authorization, and the tools exposed by the server.
- The launcher may download and execute software, install Python packages, create local files, and open network connections.
- Cloudflare Quick Tunnel URLs are temporary and are not a permanent hosting or identity guarantee.
- Do not put API keys, passwords, private files, or other secrets in the repository or share them in logs.
- Before using this with real accounts or sensitive data, review the server implementation, package sources, network behavior, and permissions.

## Before running

1. Read the full `Start-MCP-Server.ps1` source.
2. Confirm that the Python packages and Cloudflare client are obtained from sources you trust.
3. Confirm the server's authentication and tool permissions meet your needs.
4. Run it only on a Windows machine you control, and stop it when you are finished.
5. If you are unsure what a command does, do not run it until you have checked it.

## Verification

This repository's documentation is not a malware scan, a code audit, or a guarantee that the launcher is safe. No independent audit or antivirus-clean result is claimed here. Security tools may produce different results, and a clean scan alone cannot prove software is harmless.

For a more reproducible review, compare the source you inspect with the exact release you run, record its SHA-256 hash, and review any changes before updating. Report suspected security issues privately to the repository owner rather than posting secrets or credentials in a public issue.

## Download

Use the repository's **Code → Download ZIP** option to download the repository source. Only run the launcher after reviewing it and understanding the network and installation actions described above.

## Disclaimer

This is a community project and is **not an official OpenAI or ChatGPT product**. It is provided without a guarantee of fitness, security, or suitability for a particular use.