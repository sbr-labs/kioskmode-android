# Kiosk Mode (Android)

Turn a cheap Android tablet into a wall-mounted **smart kiosk + security camera** for
Home Assistant — in a single app.

- 📺 **Kiosk dashboard** — full-screen WebView of your Home Assistant dashboard.
- 🎥 **Real H.264 camera** — an on-device RTSP server (`rtsp://<tablet>:8554/`) so HA gets a
  proper camera feed, front or rear, un-mirrored.
- 🧠 **On-device detection** — motion, face (ML Kit) and noise, each with sensitivity, used to
  wake the screen (e.g. *only faces turn the screen on*).
- 🕰️ **Burn-in-safe screensaver** — drifting analog clock + optional weather.
- 🔆 Auto-brightness from the light sensor, follows system light/dark, fade transitions.
- 🔊 **Two-way intercom**, screen on/off, kiosk lock, and a web settings page reachable from
  any device.
- ⬆️ **Self-updating** — checks a release feed and one-tap installs new versions.
- 🏠 First-class **Home Assistant** entities via the companion
  [Kiosk Mode integration](https://github.com/sbr-labs/kioskmode-ha).

## Install

1. Download `kioskmode.apk` from the [latest release](https://github.com/sbr-labs/kioskmode-android/releases/latest)
   and install it on the tablet (allow installs from unknown sources).
2. Launch it — on first run you'll get a **setup screen**: enter your Home Assistant dashboard
   URL. Optionally add a weather location, a NAS recording URL, and an update feed.
3. Set the app as the device's Home launcher for full kiosk behaviour.

Everything is configurable later from **Settings** (`http://<tablet-ip>:2323/`).
Nothing is hard-coded to one network — leave any field blank to disable that feature.

## Home Assistant entities

Paired with the [companion integration](https://github.com/sbr-labs/kioskmode-ha), the app exposes:

| Entity | Details |
|---|---|
| `camera.kioskcam` | Live H.264 stream (RTSP) + JPEG snapshots |
| Binary sensors | Streaming, Motion, Face, Noise, Charging, Screen On, Dark Mode |
| Sensors | Battery, Battery Temperature, Camera FPS, Noise Level, Version, Wi-Fi Signal, Wi-Fi Network, Wi-Fi Band, Wi-Fi Link Speed, Memory Free, Storage Free, Uptime, Orientation, Power Source |
| Switch | Screen on/off |

## Settings reference

| Setting | What it does |
|---|---|
| Dashboard URL | The page the kiosk shows on launch. |
| Camera | Front/rear, flip, resolution. |
| Detection | Motion / face / noise toggles + sensitivity; which event wakes the screen. |
| Weather location | Lat/lon for the screensaver. Blank = clock only. |
| NAS recording URL | Address of your recorder's control server. Blank hides recording. |
| Update feed | Blank = official GitHub releases; or point at your own host. |

## Updates

The app checks [`latest.json`](latest.json) in this repo and offers a one-tap update when a
newer build is released. Point the **Update feed** setting at your own host to self-manage updates.

## License

Free for personal and other **noncommercial** use under the
[PolyForm Noncommercial License 1.0.0](LICENSE). **Commercial use requires a paid
license** — contact sjbrowning7@gmail.com for commercial / royalty terms.
