# Habit Tracker — React Native & Firebase

<img src="/screen.png" width="900">

<div align="center">
  <br />
  <div>
    <img src="https://img.shields.io/badge/-React_Native-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React Native" />
    <img src="https://img.shields.io/badge/-Expo-000000?style=for-the-badge&logo=expo&logoColor=white" alt="Expo" />
    <img src="https://img.shields.io/badge/-Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
    <img src="https://img.shields.io/badge/-TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/-Expo_Router-000000?style=for-the-badge&logo=expo&logoColor=white" alt="Expo Router" />
  </div>
  <h3 align="center">A full-featured Habit Tracker built with React Native, Expo, and Firebase</h3>
  <br />
</div>

---

## ⚙️ Tech Stack

| Technology | Purpose |
|---|---|
| **React Native 0.79** | Cross-platform mobile development |
| **Expo SDK 53** | Development tooling, OTA updates, native APIs |
| **Expo Router** | File-based navigation (tabs + stack) |
| **Firebase Firestore** | Real-time NoSQL database |
| **Firebase Auth** | Email/password authentication |
| **TypeScript** | Type safety across the codebase |
| **React Native Paper** | Material Design UI components |
| **React Native Reanimated** | Smooth animations |
| **React Native Gesture Handler** | Swipe gestures on habit cards |
| **React Native SVG** | Custom ring/progress charts |
| **React Native Chart Kit** | Data visualizations |
| **AsyncStorage** | Local persistence |
| **Expo Haptics** | Tactile feedback |

---

## ⚡️ Features

### 🔐 Authentication
- **Sign In / Sign Up** with email and password via Firebase Auth
- Animated auth screen that adapts layout when the keyboard opens
- Inline error messages for validation and Firebase errors
- Auto-redirects authenticated users to the home screen

### 🧭 Onboarding
- One-time onboarding flow shown after a new account is created
- Introduces the app's core concepts before the first use

### 🏠 Home Screen
- **Dynamic greeting** — "Good Morning / Afternoon / Evening" based on time of day
- **Horizontal date strip** with a 7-day calendar centred on today
- **Frequency filter tabs** — filter habits by All / Daily / Weekly / Monthly
- **Today's progress bar** — shows completed vs total habits for the active filter
- **Swipe gestures** on every habit card:
  - Swipe **right** → mark habit as completed ✅
  - Swipe **left** → delete the habit 🗑️
- **Tap** a habit card to open the Edit Habit screen
- **Category-coloured icons** for each habit (Health, Fitness, Mindfulness, Learning, Productivity, Social, Finance, Other)
- **Streak counter** (🔥) displayed on each habit card
- Empty-state prompt when no habits exist

### ✅ Daily Check-ins
- **Hero card** prompts the user to set up daily check-ins (hidden once check-ins exist)
- **Add Check-in modal** with:
  - Quick-pick presets: 💧 Water, 😴 Sleep, 🏃 Steps, 🧘 Meditate, 📖 Read
  - Custom title, emoji, unit, goal, and accent colour
- **SVG ring progress indicator** per check-in item showing current vs goal
- **Smart step-size** increment/decrement (+/−) buttons that scale with the goal value
- **Completion badge** showing how many check-ins are done out of total for the day
- Check-in data is scoped to the current day only and synced via Firestore

### ➕ Add Habit
- **Icon picker** — choose from 16 emoji icons
- **Colour picker** — 12 accent colour swatches
- **Frequency selector** — Daily / Weekly / Monthly
- **Repeat count** — set 1–10 repetitions per day
- **Optional reminder** — pick a push-notification time from preset slots (06:00 – 22:00)
- Supports a pre-filled title and category when navigated from a category shortcut

### ✏️ Edit Habit
- Same rich form as Add Habit, pre-populated with existing habit data
- Updates title, description, icon, colour, frequency, repeat count, and reminder in Firestore

### � Activity Overview Screen
- **Concentric ring stat card** showing:
  - 🟢 Current streak (outer ring, lime)
  - 🟣 Total completions (middle ring, lavender)
  - 🔴 Active days (inner ring, red)
- **Per-habit heatmap cards** — 31-day tile grid showing completion history for each habit, colour-coded per habit with a "last active" highlight
- **Monthly bar chart** — 6-month history of habit completions with best month, total (6-month), and this-month stats

### 🔥 Streaks Screen
- **Hero challenge card** with a motivational daily challenge banner
- **Overview summary cards** — total habits, best streak, total completions
- **Leaderboard** — top 3 habits ranked by best streak with gold/silver/bronze badges
- **Detailed habit list** sorted by best streak, each showing:
  - Current streak 🔥 and best streak 🏆
  - Completion rate % with a mini progress bar

### � Account Screen
- **Edit profile** — update display name and email address inline with animated active-field highlight
- **Member since** date pulled from Firebase Auth metadata
- **Save Changes** button with loading state
- **Sign Out** button at the bottom of the screen

---

## 🗂️ Project Structure

```
habit-tracker/
├── app/
│   ├── (tabs)/
│   │   ├── index.tsx        # Home screen (habits + daily check-ins)
│   │   ├── overview.tsx     # Activity overview (heatmaps + charts)
│   │   ├── streaks.tsx      # Streaks leaderboard
│   │   ├── account.tsx      # Profile / sign-out
│   │   └── _layout.tsx      # Bottom tab navigator
│   ├── add-habit.tsx        # Create a new habit
│   ├── edit-habit.tsx       # Edit an existing habit
│   ├── auth.tsx             # Sign In / Sign Up
│   ├── onboarding.tsx       # First-run onboarding
│   └── _layout.tsx          # Root stack layout
├── lib/
│   ├── firebase.ts          # Firebase config + collection constants
│   ├── auth-context.tsx     # Auth state context provider
│   └── colors.ts            # App-wide colour tokens
└── types/
    └── database.type.ts     # TypeScript interfaces (Habit, HabitCompletion, Reminder, DailyCheckin)
```

---

## 👌 Quick Start

### Prerequisites

- [Node.js](https://nodejs.org/) ≥ 18
- [Expo CLI](https://docs.expo.dev/get-started/installation/)
- A [Firebase](https://firebase.google.com/) project with **Authentication** and **Firestore** enabled

### Setup

```bash
# 1. Clone the repository
git clone https://github.com/rasso7/habit-tracker.git
cd habit-tracker

# 2. Install dependencies
npm install

# 3. Add your Firebase config
# Create a .env file at the root (see .env.example)
# EXPO_PUBLIC_FIREBASE_API_KEY=...
# EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=...
# EXPO_PUBLIC_FIREBASE_PROJECT_ID=...
# ...

# 4. Start the development server
npm start
```

Open the app on a physical device with the **Expo Go** app, or press `a` / `i` for Android / iOS simulators.

---

## ☁️ Deployment

### Expo EAS Build

```bash
npm install -g eas-cli
eas build --platform android   # or ios / all
```

### Expo Go (Development)

```bash
npm start   # opens Expo DevTools at http://localhost:8081
```

---

## 🔗 Links

- [React Native Docs](https://reactnative.dev/)
- [Expo Docs](https://docs.expo.dev/)
- [Firebase Docs](https://firebase.google.com/docs)
- [Expo Router Docs](https://docs.expo.dev/router/introduction/)
