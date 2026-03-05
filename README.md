# CoffeeLedger

A personal coffee journal to log brews, rate beans, and track your coffee journey — synced across devices in real time.

**Live:** [coffee.fisicaro.xyz](https://coffee.fisicaro.xyz)

## Features

- Google sign-in with real-time cloud sync
- Log bean name, grind setting, brew method, rating, and tasting notes
- Photo upload with client-side compression
- Stats dashboard (total entries, unique beans, average rating)
- Sort, search, edit, and delete entries
- Responsive design for mobile and desktop

## Tech Stack

- **Frontend:** Vanilla HTML/CSS/JS (single-file, no build step)
- **Backend:** Firebase Auth + Firestore
- **Hosting:** Docker + Nginx
- **Design:** Coffee-themed palette with Cormorant Garamond & DM Sans

## Setup

1. Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
2. Enable **Authentication** (Google sign-in) and **Firestore**
3. Copy your Firebase config and replace the placeholder values in `index.html`:
   ```js
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     projectId: "YOUR_PROJECT",
     storageBucket: "YOUR_PROJECT.firebasestorage.app",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```
4. Run locally:
   ```bash
   docker compose up --build
   ```
5. Open [http://localhost:8090](http://localhost:8090)

## Architecture

The entire app is a single `index.html` — markup, styles, and logic included. Firebase handles authentication and data persistence with real-time `onSnapshot` listeners. Images are compressed client-side and stored as base64 in Firestore documents.
