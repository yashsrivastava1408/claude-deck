# Claude Deck

**Website**: [claudedeck.org](https://claudedeck.org)

A self-hosted web application for visualizing and managing Claude Code configuration. Provides a unified interface for managing MCP servers, plugins, slash commands, hooks, agents, permissions, usage tracking, and other Claude Code extensions.

## Open Source Contributions 🛠️

![Open Source Contributor](https://img.shields.io/badge/Open%20Source-Contributor-green)

### Claude Deck — Open Source Contribution (External Maintainer PR)

Claude Deck is a self-hosted web dashboard for managing and visualizing Claude Code configurations.

**Key Contributions:**

- **Security Engineering** — Hardened the backend by remediating critical path traversal and DoS vulnerabilities, and implementing robust input validation
- Implemented production-ready Docker support using a multi-stage Dockerfile
- Designed docker-compose workflow for simplified local and production deployment
- Stabilized production build by resolving TypeScript strict-mode issues
- Improved runtime reliability through null-safety fixes and edge-case handling
- Added SPA routing fallback and deployment stability improvements
- Reduced onboarding complexity by enabling minimal-setup execution

**Impact:**

- Enabled containerized deployment and simplified onboarding with single-command setup
- Improved production stability and reduced runtime edge-case failures

Contribution reviewed and merged by project maintainers.

🔗 Merged PR: https://github.com/adrirubio/claude-deck/pull/38

## Features

- **Dashboard** — Overview of all Claude Code configurations with context window visualizer
- **Config Editor** — Browse, inspect, and edit configuration files across all scopes
- **MCP Servers** — Add, edit, test, and manage MCP server connections with OAuth support. Browse and install servers from the [MCP Registry](https://registry.modelcontextprotocol.io). View tools, resources, and prompts. Supports stdio, HTTP, and SSE transports
- **Slash Commands** — Browse, create, and edit custom commands (user and project scope)
- **Plugins** — Browse installed plugins with detail views and enable/disable toggles
- **Hooks** — Configure automation hooks by event type (PreToolUse, PostToolUse, etc.)
- **Permissions** — Visual allow/deny rule builder for tool access control
- **Agents** — Create and manage custom agent configurations
- **Skills** — Browse installed skills and discover new ones from [skills.sh](https://skills.sh)
- **Memory** — View and edit Claude Code memory files
- **Output Styles** — Configure response output formats
- **Status Line** — Customize Claude Code status line display
- **Session Transcripts** — View conversation history with full message details and tool use
- **Usage Tracking** — Monitor token usage, costs, and billing blocks with daily/monthly charts
- **Plan History** — Browse and review Claude Code implementation plans
- **Backup & Restore** — Create and manage configuration backups with selective restore
- **Projects** — Discover and manage project directories

## Screenshots

| Dashboard | MCP Servers |
|-----------|-------------|
| ![Dashboard](screenshots/dashboard.png) | ![MCP Servers](screenshots/mcp-servers.png) |

| Usage Tracking | Session Transcripts |
|----------------|---------------------|
| ![Usage Tracking](screenshots/usage-tracking.png) | ![Session Transcripts](screenshots/sessions.png) |

## Tech Stack

| Layer | Technology |
|-------|------------|
| Backend | Python 3.11+ with FastAPI |
| Frontend | React 19 + TypeScript + Vite 7 |
| UI Components | shadcn/ui + Tailwind CSS |
| Charts | Recharts (via shadcn/ui) |
| Database | SQLite (async via SQLAlchemy + aiosqlite) |
| Containerization | Docker + Docker Compose |

## Quick Start with Docker

```bash
git clone https://github.com/adrirubio/claude-deck.git
cd claude-deck
docker compose up
```

This builds and starts Claude Deck at http://localhost:8000, mounting your `~/.claude` and `~/.claude.json` configuration files.

> [!NOTE]
> The container mounts your home directory's Claude Code configuration. The container runs as root to access these files; adjust permissions if running as a non-root user.

## Manual Installation

**Prerequisites**: Python 3.11+, Node.js 18+

```bash
git clone https://github.com/adrirubio/claude-deck.git
cd claude-deck
./scripts/install.sh
```

## Development

```bash
./scripts/dev.sh
```

This starts:
- Backend at http://localhost:8000 (API docs at http://localhost:8000/docs)
- Frontend at http://localhost:5173

## Configuration Files

Claude Deck reads and writes these Claude Code configuration files:

| File/Directory | Scope | Description |
|---------------|-------|-------------|
| `~/.claude.json` | User | OAuth, caches, MCP servers |
| `~/.claude/settings.json` | User | User settings, permissions, disabled servers |
| `~/.claude/settings.local.json` | User | Local overrides (not committed) |
| `~/.claude/commands/` | User | User slash commands |
| `~/.claude/agents/` | User | User agents |
| `~/.claude/skills/` | User | User skills |
| `~/.claude/projects/` | User | Session transcripts & usage data |
| `.claude/settings.json` | Project | Project settings |
| `.claude/commands/` | Project | Project slash commands |
| `.mcp.json` | Project | Project MCP servers |
| `CLAUDE.md` | Project | Project instructions |

## Contributing

1. Fork the repo and create a feature branch
2. Run `cd frontend && npm run lint` before submitting
3. Open a pull request against `master`

API documentation is available at http://localhost:8000/docs when running the dev server.

## Built By

[Adrian](https://github.com/adrirubio) (13) and [Juan](https://github.com/juanrubio) during the 2025 Christmas break as a learning project — to explore open source, Claude Code, and full-stack development together.

## Acknowledgments

The session transcript viewer was inspired by and includes code adapted from [claude-code-transcripts](https://github.com/simonw/claude-code-transcripts) by [Simon Willison](https://simonwillison.net/).

The usage tracking feature ports algorithms from [ccusage](https://github.com/ryoppippi/ccusage) by [ryoppippi](https://github.com/ryoppippi), including session block identification, tiered pricing, and burn rate projections.



## Disclaimer

Claude Deck is a community project and is not affiliated with or endorsed by Anthropic.

## License

MIT License
