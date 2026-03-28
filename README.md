# 🎵 VibeBot — Spotify Voice Chatbot

> **Tell it your mood. It builds the playlist. It starts playing.**

VibeBot is a lightweight, single-file AI music chatbot built with pure HTML, CSS, and JavaScript — no frameworks, no build tools, no backend. Just open it in a browser and talk to it.

![Status](https://img.shields.io/badge/Status-Live-1DB954?style=for-the-badge&logo=spotify&logoColor=white)
![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-1DB954?style=for-the-badge)
![Single File](https://img.shields.io/badge/Size-Single%20File-1DB954?style=for-the-badge)

---

## 📸 What It Looks Like

```
┌─────────────────────────────────────────────┐
│  🟢  VIBEBOT  for Spotify                   │
├─────────────────────────────────────────────┤
│  Quick Mood:                                │
│  🚶 Morning Walk  🏃 Running  💪 Gym        │
│  🎉 Bollywood Party  🔥 Afrobeats  🌙 Chill │
├─────────────────────────────────────────────┤
│                                             │
│  ♪  Hey! I'm VibeBot 🎵                    │
│     Tell me your mood or activity...        │
│                                             │
│         "I'm going for a run 🏃"         👤 │
│                                             │
│  ♪  Let's go! Pulling high-energy bangers  │
│     at 140–160 BPM! 🏃💨                   │
│                                             │
│  ┌─────────────────────────────────────┐   │
│  │ 🏃 Run Hard Playlist · 140–160 BPM  │   │
│  │─────────────────────────────────── │   │
│  │ ▶ 1. 🐯 Eye of the Tiger — Survivor │   │
│  │   2. 💥 Till I Collapse — Eminem    │   │
│  │   3. ⚡ Stronger — Kanye West       │   │
│  │   ████░░░░░░  1:24 / 4:05          │   │
│  └─────────────────────────────────────┘   │
│                                             │
├─────────────────────────────────────────────┤
│  🟢 Eye of the Tiger · Survivor  ⏮ ▶ ⏭   │
├─────────────────────────────────────────────┤
│  [ Tell me your vibe...      ]  📤  🎙️     │
└─────────────────────────────────────────────┘
```

---

## ✨ Features

- 💬 **Natural language chat** — Type anything like *"I'm going for a run"* or *"Bollywood party mood"*
- 🎵 **Auto playlist generation** — Detects your vibe and builds a themed playlist instantly
- ▶️ **Built-in music player** — Now Playing bar, play/pause, prev/next, seekable progress bar
- 🎙️ **Voice input** — Press the mic button and speak your mood (Chrome/Edge)
- 🌊 **Animated wave visualiser** — Green bars animate on the currently playing song
- 🎨 **Spotify-inspired dark UI** — Custom green theme with smooth animations
- 📦 **Zero dependencies** — Pure HTML + CSS + JS, runs anywhere

---

## 🎯 Supported Moods

| Mood Chip | Keywords Detected | BPM | Example Songs |
|---|---|---|---|
| 🚶 Morning Walk | walk, stroll, morning | 100–110 | Levitating, Happy, Blinding Lights |
| 🏃 Running | run, jog, sprint | 140–160 | Eye of the Tiger, Till I Collapse |
| 💪 Gym | gym, workout, lift, weights | 160–180 | SICKO MODE, Lose Yourself, HUMBLE. |
| 🎉 Bollywood Party | bollywood, hindi, desi, punjabi | 120–140 | Kala Chashma, Param Sundari |
| 🔥 Afrobeats | afrobeats, afro | 105–125 | Essence, Calm Down, Ye |
| 🌙 Late Night Chill | chill, relax, calm, late night | 70–90 | Redbone, Nights, Golden Hour |

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/vibebot.git
cd vibebot
```

### 2. Open in browser

```bash
# macOS
open spotify-vibebot.html

# Windows
start spotify-vibebot.html

# Linux
xdg-open spotify-vibebot.html
```

That's it. No `npm install`. No server. No config. Just open and use.

---

## 🗣️ How to Use

### Option 1 — Type your mood
Click the input bar at the bottom and type anything:

```
"I'm going for a run"
"Gym workout playlist"
"Bollywood party mood"
"Late night chill vibes"
"I need something to study to"
```

### Option 2 — Use Quick Mood chips
Click any of the 6 preset mood chips at the top for an instant playlist.

### Option 3 — Voice input
Click the 🎙️ green mic button and speak your mood out loud.
> Requires Chrome or Edge. Mic turns red while listening.

---

## 🗂️ Project Structure

```
vibebot/
│
├── spotify-vibebot.html    # Entire app — HTML + CSS + JS in one file
└── README.md               # This file
```

Everything is self-contained in a single `.html` file:

| Section | What it does |
|---|---|
| `<style>` | All UI styles — dark theme, animations, layout |
| `PLAYLISTS` object | Song data for all 6 mood playlists |
| `detectIntent()` | Regex-based mood detection from user text |
| `renderPlaylist()` | Builds the playlist card HTML dynamically |
| `playSong()` | Controls playback state and UI updates |
| `startProgress()` | Simulates track progress with a timer |
| `toggleMic()` | Web Speech API voice input handler |

---

## 🧠 How Intent Detection Works

VibeBot uses regex pattern matching to detect your mood from natural language:

```js
function detectIntent(text) {
  const t = text.toLowerCase();
  if (t.match(/walk|stroll|morning walk/))     return 'walk';
  if (t.match(/run|running|jog|sprint/))        return 'run';
  if (t.match(/gym|workout|lift|weights/))      return 'gym';
  if (t.match(/bollywood|hindi|desi|punjabi/))  return 'bollywood';
  if (t.match(/afrobeat|afro/))                 return 'afrobeats';
  if (t.match(/chill|relax|calm|late night/))   return 'chill';
  return null; // unknown mood
}
```

If no intent is detected, VibeBot prompts you with example suggestions.

---

## 🎨 Customisation

### Add a new mood and playlist

Inside `spotify-vibebot.html`, add a new entry to the `PLAYLISTS` object:

```js
PLAYLISTS.lofi = {
  title: "📚 Lo-Fi Study Session",
  bpm: "65–80 BPM",
  emoji: "📚",
  songs: [
    { name: "Chill Lofi Beat",  artist: "Lofi Girl",  dur: "3:20", emoji: "☕" },
    { name: "Rainy Day Study",  artist: "ChilledCow", dur: "4:10", emoji: "🌧️" },
    // add more...
  ]
};
```

Then register the detection keyword:

```js
if (t.match(/study|focus|lofi|lo-fi/)) return 'lofi';
```

And add a bot response:

```js
RESPONSES.lofi = "Focus mode activated 📚 Loading smooth Lo-Fi beats...";
```

Finally, add a chip in the HTML:

```html
<div class="chip" onclick="quickMood('lofi study')">
  <span class="chip-emoji">📚</span> Lo-Fi Study
</div>
```

### Change the colour theme

Edit the CSS variables at the top of `<style>`:

```css
:root {
  --green: #1DB954;        /* Main accent colour */
  --green-dark: #158a3e;   /* Hover / dark variant */
  --bg: #0a0a0a;           /* Page background */
  --surface: #111111;      /* Card and bubble background */
}
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 — custom properties, keyframe animations, flexbox |
| Logic | Vanilla JavaScript ES6+ |
| Fonts | Space Mono via Google Fonts |
| Voice | Web Speech API — browser-native, no library needed |
| Build system | None — zero build step |
| Dependencies | None |

---

## 🌐 Browser Support

| Browser | Text Chat | Voice Input | Animations |
|---|---|---|---|
| Chrome 90+ | ✅ | ✅ | ✅ |
| Edge 90+ | ✅ | ✅ | ✅ |
| Firefox 88+ | ✅ | ❌ | ✅ |
| Safari 14+ | ✅ | ⚠️ Partial | ✅ |

> Voice input uses the Web Speech API which is fully supported in Chrome and Edge only.

---

## 🗺️ Roadmap

- [ ] Connect real Spotify Web API for actual audio playback
- [ ] AI-powered responses via Ollama (local LLM, no API key needed)
- [ ] More moods — K-pop, Jazz, Lo-fi, Tamil, Punjabi, Classical
- [ ] Dynamic Vibe Wheel — AI-generated follow-up suggestions
- [ ] Multi-language support — Hindi, Hinglish, regional languages
- [ ] Playlist history across sessions
- [ ] Mobile PWA support

---

## 🤝 Contributing

Contributions are welcome!

```bash
# 1. Fork the repository on GitHub

# 2. Clone your fork
git clone https://github.com/yourusername/vibebot.git

# 3. Make your changes to spotify-vibebot.html

# 4. Test by opening the file directly in Chrome

# 5. Submit a pull request with a clear description
```







<div align="center">
  Built with 🎵 and pure vanilla JS &nbsp;·&nbsp; No frameworks harmed in the making of this project
</div>
