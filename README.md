# 🩺 Swastik Health — Pan-India Healthcare Platform

A full-stack healthcare access platform built for the Indian market, unifying hospital discovery, doctor booking, blood bank lookup, ambulance dispatch, medicine availability, insurance comparison, and emergency SOS into a single interface.

![status](https://img.shields.io/badge/status-active-brightgreen) ![type](https://img.shields.io/badge/type-personal%20project-blue)

---

## ✨ Features

- **Authentication** — real signup/login backed by persistent storage; accounts, health records, and reviews survive across sessions
- **Hospital discovery** — state-wise filtering across a curated dataset of major Indian hospitals (AIIMS, Apollo, Tata Memorial, Narayana Health, and more), with live occupancy, accreditation, and specialty tags
- **Doctor booking** — browse specialists by city/hospital, view fees and ratings, book available time slots
- **Emergency SOS** — one-tap SOS activation with national helpline numbers (108, 100, 101, 104, etc.) and nearby ambulance dispatch with live ETA
- **Blood bank lookup** — real-time unit availability by blood group and city
- **Medicine availability** — stock status and pricing across major pharmacy chains
- **Insurance comparison** — coverage, premiums, and cashless hospital networks (including Ayushman Bharat)
- **Patient health records** — per-user record storage (lab reports, scans, vaccination history)
- **Hospital reviews** — community ratings and reviews, persisted and visible to all users
- **National health stats dashboard** — live-style breakdown of hospitals, beds, and doctors by state (NHM/MoHFW data)

## 🛠️ Tech Stack

- **Frontend:** Vanilla JavaScript, HTML5, CSS-in-JS (custom dark theme, no framework dependency)
- **Persistence:** Key-value storage layer for user accounts, health records, and reviews — data persists across sessions and devices
- **Design:** Custom component system (cards, badges, progress bars) built from scratch, no UI library

## 🚀 Architecture Notes

The app follows a simple state → render loop:
- A single `state` object drives the entire UI
- `render()` re-builds the DOM from state on every change
- An async persistence layer (`loadUsers`, `saveUsers`, `loadRecords`, `saveRecords`, `loadReviews`, `saveReviews`) syncs auth, records, and reviews to storage, with in-memory fallback so the UI never blocks on network calls
- Sign-in/sign-up resolve immediately against cached data; record fetches happen in the background so the app feels instant

## ⚠️ Known Limitations

This was built as a rapid prototype, not a production system:
- Passwords are stored in plain text in the data layer — a real deployment would need hashing (bcrypt) and a proper auth provider
- Uses a lightweight key-value store rather than a relational database
- Hospital/doctor/pharmacy data is static seed data, not a live API integration
- No server-side validation — all checks currently run client-side

## 📌 Roadmap

- [ ] Move auth to a real backend (Node/Express + MongoDB or PostgreSQL) with hashed passwords
- [ ] Replace static hospital data with a live source (e.g., Google Places API)
- [ ] Add real-time appointment booking with conflict checks
- [ ] Push notifications for SOS and appointment reminders

