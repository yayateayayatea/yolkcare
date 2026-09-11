# YorkCare by Half Boiled Egg

__Team members:__ Gordon Liew Yew Yang, Marilyn Emah Sim Mei Lim

__Problem Statement:__ Stress & Workload Manager

__Video Presentation:__ [link_to_video]()

__Presentation Slides:__ [link_to_slide]()

---

## 1. Project Overview

### The Problem

University students burn out not from one thing, but from everything piling up across assignments, jobs, errands, and social life simultaneously — with no way to see the total weight until it's too late. Load is fragmented across five life domains with no unified view, there's no early warning signal so students only react after burnout hits, manual tracking is too high-friction to maintain under pressure, and recovery is never treated as a real priority. The key stakeholders are university students in Malaysia. Apps like Finch gamify self-care but never model actual load or capacity, Todoist and TickTick handle tasks well but are completely blind to physical and social strain, and Daylio only reflects past mood with no ability to predict or intervene — none of them give students a unified, proactive view of how much they're truly carrying.

### Our Solution

YorkCare is a mobile app that gives university students a real-time picture of how much they're carrying across mental, physical, time, social, and errand load — before burnout hits. Instead of manual logging, students report their day through AI-powered camera and mic input, keeping the friction near zero. Algorithms then calculate total load across categories and surface smart suggestions to rebalance, defer, or recover.

---

## 2. Ideation & Process

### 2.1 Ideas We Considered

| Idea | Keep / Drop |
| :-- | :-- |
| Achievement Board | ✅ Keep — Reinforces progress visibility and motivates students to maintain healthy habits over time |
| Virtual Farm (YorkCare Eggs) | ✅ Keep — Ties recovery and stress management to a rewarding, low-stakes mechanic that fits the team identity and keeps students returning daily |
| AI Camera + Mic Input | ✅ Keep — Directly solves the friction problem that kills every manual tracker; core to what makes this app different |
| Statistics & History Panel | ✅ Keep — Lets students spot patterns in their load and stress over time, turning short-term data into long-term self-awareness |
| Profile Panel | ✅ Keep — Grounds the experience in personal context and allows customisation of load categories to fit each student's lifestyle |
| Daily Quote | ✅ Keep — Low-effort, high-warmth touchpoint that nudges students to open the app daily without adding cognitive load |
| Social Leaderboard | ❌ Drop — Comparing stress loads publicly creates social pressure and could shame students who are already struggling |
| Calorie & Fitness Tracker | ❌ Drop — Scope creep; physical load is already captured through AI input and a dedicated fitness tracker pulls focus away from the core burnout problem |
| In-App Messaging | ❌ Drop — Adds significant development complexity and duplicates what messaging apps already do better |
| Paid Stress Consultation Booking | ❌ Drop — Introduces a monetisation layer that conflicts with the app's accessible, student-first positioning |

### 2.2 Ideation Boards

![Ideation Board](./pic/pic01.jpeg)

### 2.3 Mentor Consultation

| Date | Mentor | Feedback Received | What Was Changed |
| :---: | :---: | :--- | :--- |
| 12th September 2026 | Zach Khong | We are penguin egg instead | Eat more |

---

## 3. Design & Prototype

__UI Prototype:__ [View on Canva](https://canva.link/xjfs6m4h9synss4)

__Backup Link:__ [link_to_backup]()

---

## 4. What Makes It Different

YorkCare isn't another mood journal or task manager — it's the only student-focused tool that unifies load across five life domains and acts on it before burnout hits. Here's what sets it apart:

| Feature | The Twist |
| :--- | :--- |
| AI Camera + Mic Logging | No other wellness app lets you report your day by just talking or pointing your camera — eliminating the friction that kills manual tracking habits |
| Multi-Domain Load Calculator | Most apps track one dimension; YorkCare weighs mental, physical, time, social, and errand load together into a single capacity score |
| Proactive Recovery Nudge | Instead of just showing data, the app tells you when to stop — suggesting rest, downtime, or a hangout before you hit the wall |
| Load Balancer | Automatically groups and defers lower-priority tasks when capacity is high, so the app doesn't just warn you — it helps you respond |
| Egg & Farm Reward System | Recovery and stress management are tied to a playful virtual farm mechanic, making rest feel like a win rather than lost productivity |
| Burnout-First Design | Every feature is built around one goal — catching overload early — rather than maximising productivity like most competing tools |

---

## 5. Technical Architecture & Feasibility

### Tech Stack

YorkCare is a self-contained Android app with no multi-user sync or server-side logic required, so a lightweight local architecture is the right fit for this scope.

| Layer | Technology | Why | Constraint |
| :--- | :--- | :--- | :--- |
| UI | Jetpack Compose | Modern declarative Android UI, native to Kotlin and well-suited for dynamic dashboards and animations | Android only; no iOS support |
| Architecture | MVVM (ViewModel + LiveData) | Clean separation of UI and business logic, natively supported in Jetpack; keeps the codebase maintainable | Requires discipline to keep ViewModels focused and not overloaded |
| Local Database | SQLite via Room | Built into Android with zero setup cost; ideal for storing per-user load history, stress logs, and task data on-device | Data is local only — no cross-device sync or backup unless added separately |
| AI Multimodal Input | Gemini API | Handles both camera and mic input in a single API; free tier is sufficient for prototype scale; integrates naturally with Android | Requires internet connection; API key must never be bundled into the APK |
| Speech-to-Text | Google Cloud Speech-to-Text | Accurate transcription with Malay and English support; free monthly quota fits demo-scale usage | Requires internet; API key should be handled server-side or via a secure proxy to avoid exposure |

### System Architecture

The app follows the **MVVM (Model–View–ViewModel)** pattern throughout:

- **View** — Jetpack Compose UI screens that observe state from the ViewModel
- **ViewModel** — handles all business logic including load calculation, suggestion generation, and API calls
- **Model** — Room database for local persistence; Gemini and Google STT APIs for AI-powered input processing

### Deployment

The app is distributed as a direct APK install onto a physical Android device running **API level 26 (Android 8.0) or above**, which covers the majority of mid-range devices in use today. No Play Store submission is required for prototype demonstration.

### Build Plan & Scope

| Phase | Focus |
| :--- | :--- |
| Phase 1 | Core UI screens — home dashboard, load input, history panel |
| Phase 2 | AI camera and mic integration via Gemini API |
| Phase 3 | Load calculator algorithm and category scoring |
| Phase 4 | Virtual farm mechanic and achievement board |
| Phase 5 | Polish — daily quotes, recovery nudges, profile panel |
