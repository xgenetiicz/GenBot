# GenBot - Discord Activity & Playtime Tracker

A self-hosted Discord bot that automatically tracks and visualizes game activity across servers in real time. Users can see exactly how much time they've spent on each game, compete on per-server leaderboards, and invite the bot to any Discord server.

## What it does

- Tracks playtime per user, per game, per server (guild)
- Logs accurate time spent in each game session automatically
- Provides per-server leaderboards — users compete for most hours on a specific game
- Slash commands for querying stats and leaderboards
- Deployed and running in production on a Hetzner VPS

## Invite the bot

[Click here to invite PlayTimeBot to your server](https://discord.com/oauth2/authorize?client_id=1384557784741318767&scope=bot&permissions=2182171648)

## Tech stack

| Layer | Technology |
|---|---|
| Language | Java 21 |
| Framework | Spring Boot |
| Discord API | JDA (Java Discord API) |
| Database | PostgreSQL |
| ORM | Hibernate + Spring Data JPA |
| Build tool | Maven |
| Fuzzy matching | Apache Commons Text (Levenshtein) |
| Deployment | Hetzner VPS |

## Architecture

Event-driven backend built with JDA - dedicated listeners capture real-time presence and activity updates from Discord. Game sessions are tracked with precise start/end timestamps and persisted to PostgreSQL.

- `ConcurrentHashMap` used for thread-safe handling of concurrent sessions across multiple guilds
- Slash commands delegate to a service layer for clean separation of concerns
- Global records tracked per user across all servers; leaderboards scoped per guild
- Secrets managed via `.env` excluded from version control

## Configuration in small parts:

### Prerequisites

- Java 21
- PostgreSQL database
- Discord bot token ([Discord Developer Portal](https://discord.com/developers/applications))

### Configuration

Created a `.env` file in the root directory:

### Running it by:

```bash
mvn clean install
mvn spring-boot:run
```

## License

MIT
