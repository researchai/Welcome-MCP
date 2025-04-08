# Debugging Guide for GitHub MCP Installation

This guide provides detailed instructions for installing and debugging the GitHub Model Control Protocol (MCP) integration in Cursor IDE.

## Common Installation Issues and Solutions

### 1. Node.js and NPX Issues

If you encounter `npx command not found`:

```bash
# Check if Node.js is installed
node --version
npm --version

# If not installed, install Node.js using:
# On macOS with Homebrew:
brew install node

# On Windows:
# Download from https://nodejs.org/
```

### 2. MCP Configuration Issues

If your MCP tools are not available, check your configuration:

1. **Locate Configuration File**:
   ```bash
   # Configuration should be in:
   ~/.cursor/mcp.json
   ```

2. **Correct Configuration Format**:
   ```json
   {
     "mcpServers": {
       "github": {
         "command": "npx",
         "args": [
           "-y",
           "@smithery/cli@latest",
           "install",
           "@smithery-ai/github",
           "--client",
           "cursor",
           "--config",
           "{\"githubPersonalAccessToken\":\"YOUR_GITHUB_TOKEN\"}"
         ]
       }
     }
   }
   ```

### 3. GitHub Token Issues

If experiencing authentication problems:

1. **Check Token Validity**:
   - Go to GitHub Settings → Developer Settings → Personal Access Tokens
   - Ensure token has not expired
   - Verify token has required permissions (repo scope)

2. **Token Configuration**:
   - Ensure token is properly formatted in mcp.json
   - No extra escape characters
   - No surrounding quotes around the JSON string

### 4. Installation Steps

```bash
# 1. Install Smithery CLI
npm install -g @smithery/cli

# 2. Install GitHub integration
npx @smithery/cli@latest install @smithery-ai/github --client cursor --config '{"githubPersonalAccessToken":"YOUR_TOKEN"}'
```

### 5. Troubleshooting Steps

If tools are still not available:

1. **Restart Cursor IDE**
   - Close Cursor completely
   - Reopen Cursor
   - Check if tools are available

2. **Check Logs**
   - Look for error messages in the terminal
   - Check Cursor's developer tools (if available)

3. **Verify Installation**
   ```bash
   # Check Smithery CLI version
   npx @smithery/cli@latest --version
   
   # Check if GitHub integration is installed
   npx @smithery/cli@latest list
   ```

4. **Common Error Messages**:
   - "Client closed": Check if token is valid
   - "Command not found": Check Node.js installation
   - "Configuration error": Verify JSON syntax in mcp.json

## Best Practices

1. Always use the latest version of Cursor IDE
2. Keep Node.js and npm updated
3. Use proper JSON formatting in configuration files
4. Store tokens securely
5. Check GitHub permissions regularly

## Need Help?

If you continue to experience issues:
1. Check the [Cursor Documentation](https://cursor.sh/docs)
2. Join the Cursor Community
3. Open an issue in this repository

---

*Created with ❤️ using Cursor MCP*