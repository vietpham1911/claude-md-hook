# Claude Code: Global `CLAUDE.md` Hook

Inject custom instructions into every Claude Code interaction using a CLAUDE.md file and a **user-prompt-submit** hook.

## Overview

This repository contains a simple setup that makes Claude Code reliably follow your personal rules by forcing it to re-read a CLAUDE.md file after every prompt submission.

### Add Hook Configuration

Add the following to your `settings.json`:

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "(cat ~/CLAUDE.md; printf \"\\n\"; jq -r '.input_text') || exit 1"
          }
        ]
      }
    ]
  }
}
```
Note: Replace ~/CLAUDE.md with your actual CLAUDE.md path.

### Writing Effective CLAUDE.md Files
Prefix critical rules with ALWAYS (in capital letters) to significantly increase the probability that Claude will follow them. Use the CLAUDE.md file in the repository if you need some inspiration :)
