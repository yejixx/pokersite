# Poker Site

A real-time Texas Hold'em poker app for playing with friends in private or public lobbies. The app supports lobby creation, lobby discovery, join-by-code, seat approval, in-game chat, configurable table settings, and full hand resolution with side pot handling and showdown logic.

## Features

- Create or join lobbies with a 6-character code
- Browse public lobbies and filter by name or code
- Configure lobby name, public/private visibility, auto-accept, max seats, stack size, and blinds
- Sit down, request approval, or join instantly when auto-accept is enabled
- Host controls for starting hands, editing settings, and kicking players
- In-game chat for players and spectators
- Full Texas Hold'em hand engine with:
  - Blinds and dealer rotation
  - Betting rounds
  - Hand evaluation
  - Side pots
  - Showdown and hand completion
  - Bust-out tracking

## Tech Stack

- Node.js
- Express
- Socket.IO
- Vanilla JavaScript frontend
- HTML and CSS

## Getting Started

### Prerequisites

- Node.js 18 or newer
- npm

### Install

```bash
npm install
```

### Start the app

```bash
npm start
```

Then open the app in your browser at `http://localhost:3000`.

## How It Works

The server creates and manages lobbies, handles socket events, and broadcasts game state to connected clients. The poker engine contains the actual game rules and scoring logic, while the browser client renders the lobby, table, action bar, chat, and modal flows.

Public lobby discovery, seat approval, and host migration are all handled in the socket server. The client is a single-page interface that switches between home, lobby search, lobby view, and modal states.

## Project Structure

- `server.js` — Express and Socket.IO server
- `poker-engine.js` — Texas Hold'em game engine and hand evaluation
- `public/index.html` — App shell and UI structure
- `public/js/app.js` — Client-side behaviour and socket event handling
- `public/css/style.css` — Styling for the interface
- `render.yaml` — Render deployment config

## Deployment

This repo includes a Render service definition in `render.yaml`. It installs dependencies with `npm install` and starts the app with `node server.js`.

## Notes

- Lobby codes are generated automatically and are 6 characters long.
- Public lobbies can be discovered from the Find Lobby screen.
- Hosts can update table settings unless a hand is actively in progress.
- Players who bust are removed from the table automatically.
