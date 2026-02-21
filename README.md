# Zype MCP Client

Connect AI assistants to the [Zype](https://www.zype.com) video platform using the Model Context Protocol (MCP).

## Features

- **Video Management**: List, get, create, update, and delete videos
- **Transcriptions**: AI-powered transcription and translation
- **Playlists**: Full playlist CRUD and video management
- **Categories**: Organize content with categories
- **Subtitles**: Manage video subtitles
- **Analytics**: Access engagement, revenue, and platform metrics
- **Monetization**: Subscriptions, plans, transactions, and ad tags
- **Zobjects**: Custom metadata objects (actors, directors, teams, etc.)
- **Access Control**: Three modes (readonly, safe, full)

## Prerequisites

- A Zype account with Admin API access
- Your Zype Admin API Key (found in Zype Dashboard → Settings → API Keys)

## Installation

### Cursor

Add to your Cursor MCP settings (`.cursor/mcp.json` in your project, or global settings):

```json
{
  "mcpServers": {
    "zype": {
      "command": "npx",
      "args": ["-y", "@zype-com/mcp"],
      "env": {
        "ZYPE_API_KEY": "your_admin_api_key_here",
        "ZYPE_MCP_MODE": "safe"
      }
    }
  }
}
```

### Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "zype": {
      "command": "npx",
      "args": ["-y", "@zype-com/mcp"],
      "env": {
        "ZYPE_API_KEY": "your_admin_api_key_here",
        "ZYPE_MCP_MODE": "safe"
      }
    }
  }
}
```

### Gemini CLI

Add to `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "zype": {
      "command": "npx",
      "args": ["-y", "@zype-com/mcp"],
      "env": {
        "ZYPE_API_KEY": "your_admin_api_key_here",
        "ZYPE_MCP_MODE": "safe"
      }
    }
  }
}
```

## Configuration

### Environment Variables

| Variable | Required | Description |
|----------|----------|-------------|
| `ZYPE_API_KEY` | Yes | Your Zype Admin API Key |
| `ZYPE_MCP_MODE` | No | Access mode: `readonly`, `safe` (default), or `full` |

### Access Modes

| Mode | Description |
|------|-------------|
| `readonly` | Only read operations allowed |
| `safe` | Read + write allowed. Destructive operations require `confirm: true` |
| `full` | All operations allowed without confirmation |

**Recommendation**: Use `safe` mode to prevent accidental deletions.

## Available Tools

### Videos
`list_videos`, `get_video`, `create_video`, `update_video`, `delete_video`, `download_video`

### Transcriptions
`list_transcriptions`, `get_transcription`, `transcribe_video`, `translate_video`, `list_translation_languages`

### Playlists
`list_playlists`, `get_playlist`, `create_playlist`, `update_playlist`, `delete_playlist`, `list_playlist_videos`, `add_videos_to_playlist`, `remove_videos_from_playlist`

### Categories
`list_categories`, `get_category`, `create_category`, `update_category`, `delete_category`

### Subtitles
`list_subtitles`, `get_subtitle`, `create_subtitle`, `update_subtitle`, `create_subtitle_playlist`, `delete_subtitle_playlist`, `delete_subtitle`

### Analytics
`get_plays`, `get_viewers`, `get_hours_watched`, `get_view_time`, `list_stream_hours`, `list_player_requests`, `list_new_subscriptions`, `list_subscription_revenue`

### Monetization
`list_subscriptions`, `get_subscription`, `create_subscription`, `cancel_subscription`, `list_plans`, `get_plan`, `create_plan`, `update_plan`, `delete_plan`, `list_transactions`, `get_transaction`, `list_redemption_codes`, `get_redemption_code`, `list_ad_tags`, `get_ad_tag`, `create_ad_tag`, `update_ad_tag`, `delete_ad_tag`, `list_revenue_models`, `get_revenue_model`

### Zobjects (Custom Metadata)
`list_zobject_types`, `get_zobject_type`, `create_zobject_type`, `update_zobject_type`, `delete_zobject_type`, `list_zobjects`, `get_zobject`, `create_zobject`, `update_zobject`, `delete_zobject`, `add_videos_to_zobject`, `remove_videos_from_zobject`, `get_zobject_videos`, `add_playlists_to_zobject`, `remove_playlists_from_zobject`, `get_zobject_playlists`

### Player
`get_player`

## Example Prompts

```
"List my 10 most recent videos"
"Get details for video ID abc123"
"Create a playlist called 'Featured Content'"
"Transcribe video abc123"
"Translate video abc123 to Spanish"
"Show me my analytics for the last 30 days"
"What are my top performing videos?"
"List all actors in my library"
```

## Support

- [Zype Documentation](https://docs.zype.com)
- [Zype Support](https://support.zype.com)

## License

MIT
