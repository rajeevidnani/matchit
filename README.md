# Match It

A fast emoji matching game in the style of Dobble / Spot It: two cards are on screen, they share
**exactly one** symbol, and you tap it before the clock runs out.

I built it for my niece. It started as an experiment in how far I could get vibe-coding a real,
playable app — one with accounts, saved scores and custom content — rather than another toy demo.
It works, she plays it, and that was the bar.

## How it plays

- Two cards, one shared emoji, find it as fast as you can
- Score climbs with speed; high scores are saved to your profile
- **Themes** change the whole emoji set — animals, food, faces, whatever you like
- **Build your own theme** by picking a custom set of emojis, saved to your account

The card generation uses the maths behind Dobble: a finite projective plane of order 7, which gives
57 cards and 57 symbols where any two cards share precisely one. That property is what makes the
game work, and it is generated rather than hand-built (`src/utils/dobbleLogic.ts`).

## Stack

React · TypeScript · Vite · Tailwind · Firebase (auth + Firestore for profiles, scores and custom
themes). Firestore rules scope every read and write to the owning user; leaderboard scores are the
only public read.

## Run it

```bash
npm install
cp .env.example .env.local   # add your own Gemini API key if you want the AI features
npm run dev
```

The Firebase config in `firebase-applet-config.json` is a public client identifier, not a secret —
access is controlled by the Firestore rules in `firestore.rules`.

---

Built by [Rajeev Idnani](https://www.linkedin.com/in/rajeev-idnani).
