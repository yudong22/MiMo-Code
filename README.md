<h1 align="center">MiMoCode Desktop (macOS GUI)</h1>

<p align="center">
  <img src="assets/readme/mimocode-banner.png" alt="MiMoCode Desktop" width="700">
</p>

<p align="center"><strong>Next-Generation macOS Native GUI Experience for AI Coding Assistant</strong></p>

<p align="center">
  <a href="README.zh.md">中文</a> | English
</p>

---

## 💡 Why Build a Native GUI?

While Terminal UIs (TUI) are lightweight, they face inherent constraints in visual fidelity and OS-level integration:
- **Visual Limitations**: Terminals cannot render rich graphics, glassmorphism blur effects, multi-panel flex layouts, or sub-pixel micro-animations;
- **Lack of OS Integration**: Unable to leverage native macOS window controls, global keyboard shortcuts, system tray accessibility, and deep-link protocol handlers (`opencode://`);
- **User Experience**: A modern GUI provides an intuitive dual mouse/keyboard interface, non-blocking modal overlays, and clearer code exploration views.

---

## 🛠️ Technical Approach & Architecture

- 🏗️ **Electron + SolidJS Desktop Architecture (`packages/desktop`)**: Encapsulates reactive web UI (`packages/app`) inside Electron, combining web aesthetics with macOS native performance.
- ⚡ **Embedded Headless Server & Sidecar**: Houses a bundled `node.js` opencode sidecar server communicating via high-performance IPC and local HTTP loopback.
- 📦 **Zero-External Bundling & Native C++ Bindings**: Uses pure ESM static bundling to eliminate runtime `ERR_MODULE_NOT_FOUND` errors, dereferencing native `@lydell/node-pty` C++ modules into the app bundle.
- 🔄 **Millisecond-Level UI Hot Reloading (HMR)**: Full-source file watching without stale pre-bundled caches for instant renderer development feedback.

---

## ✨ Key Advantages & Highlights

1. 🎨 **Immersive macOS Aesthetics**:
   - Native macOS Light/Dark theme switching;
   - Modal dialogs with glass backdrop blur (`backdrop-filter: blur(6px)` + `rgba(0, 0, 0, 0.45)`) and `rounded-2xl` cards.
2. ⚙️ **Rich Tool Activity UI**:
   - Live structured view: `Action Verb` + `<Extension Tag>` + **`Filename (Bold)`** + `Line Range/Result Pills (#L1-160 / 3 results)`;
   - Real-time parameter normalization for accurate filename and line-range extraction.
3. 📌 **Minimalist macOS System Tray (Systray)**:
   - Compact menu bar tray icon with streamlined controls (`Open MiMoCode`, `Quit ⌘Q`).
4. 🛡️ **Interaction Protection**:
   - Non-shifting dropdown popovers and focus isolation preventing accidental `Space` / `Enter` modal dismissal.

---

## 📸 Screenshots

<p align="center">
  <!-- Placeholder: Desktop App Main Window -->
  <img src="assets/readme/desktop-app-main.png" alt="MiMoCode Desktop App" width="700">
  <br>
  <em>Desktop App Main Interface & Sidebar Panel</em>
</p>

<p align="center">
  <!-- Placeholder: Tool Activity UI -->
  <img src="assets/readme/tool-activity-preview.png" alt="Tool Activity UI" width="700">
  <br>
  <em>AI Agent Tool Activity Expansion View</em>
</p>

<p align="center">
  <!-- Placeholder: Glass Backdrop Modal -->
  <img src="assets/readme/backdrop-modal-preview.png" alt="Modal & Backdrop Blur" width="700">
  <br>
  <em>Immersive Glass Backdrop Confirmation Modal</em>
</p>

---

## 🚀 Quick Start (Development)

```bash
# Install dependencies
bun ci

# Run desktop dev app
bun run --cwd packages/desktop dev

# Build local macOS .app & .dmg release artifacts
bun run --cwd packages/desktop package:mac
```
