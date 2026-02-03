# vm-setup

One-command server setup for mise-powered development environments.

## Quick Start

On any new server, run:

```bash
curl -fsSL https://raw.githubusercontent.com/pranavb-senslyze/vm-setup/main/install.sh | bash
```

That's it! This will:
- Install mise
- Install all your default tools (fzf, zoxide, ripgrep)
- Configure your `.bashrc` with tool-specific settings

## Adding New Tools

Edit `config.json`:

```json
{
  "tools": {
    "existing-tool": {
      "version": "latest",
      "bashrc": []
    },
    "new-tool": {
      "version": "latest",
      "bashrc": [
        "eval \"$(new-tool init bash)\""
      ]
    }
  }
}
```

## Configuration Format

### Tools Section
Each tool entry has:
- `version`: Tool version ("latest", specific version, etc.)
- `bashrc`: Array of lines to add to `.bashrc` (empty if none needed)

### Global Bashrc
Lines that apply to everything (e.g., mise activation itself).

### Escaping Notes
In JSON, escape double quotes with `\"`:
```json
"bashrc": [
  "eval \"$(zoxide init bash)\""
]
```

## Files

- `install.sh` - The bootstrap script (one-liner you curl)
- `config.json` - Declarative tool definitions
- `README.md` - This file

## Post-Setup

After running the installer:
```bash
source ~/.bashrc
```

Or start a new shell session.

## Repository

GitHub: https://github.com/pranavb-senslyze/vm-setup
