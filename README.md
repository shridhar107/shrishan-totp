# Zerodha Kite TOTP

A standalone, single-file HTML + JavaScript TOTP generator for Zerodha Kite — designed to work directly in your Android Chrome browser, no app or server required.

## Features

| Feature | Detail |
|---|---|
| **First-run setup** | If no secret is saved, prompts for `KITE_TOTP_SECRET`. Shows/hides with 👁 button |
| **Persistent storage** | Secret is saved to `localStorage` — survives browser restarts |
| **Edit button** | "✏️ Edit Secret" button returns you to setup at any time |
| **Live TOTP** | Generates an RFC 6238 / pyotp-compatible 6-digit code, auto-refreshes every 30 s |
| **Countdown ring** | SVG ring timer + progress bar. Turns amber at ≤10 s, red at ≤5 s |
| **Copy button** | One-tap "📋 Copy to Clipboard" — turns green with ✓ Copied! feedback |
| **Android Chrome ready** | Fully responsive, touch-friendly tap targets |
| **No server needed** | Pure browser — TOTP computed with WebCrypto + HMAC-SHA1, no network calls |

## Files

| File | Description |
|---|---|
| `zerodha-kite-totp.html` | Main TOTP generator — open this in your browser |

## Usage

### Browser (Android / Desktop)

1. Open `zerodha-kite-totp.html` in Chrome.
2. First time: paste your TOTP secret and tap **Save**.
3. The 6-digit code refreshes automatically every 30 seconds.
4. Tap **📋 Copy to Clipboard** to copy the current code.

### Adding to Android Home Screen

#### Method 1: Chrome Bookmarks Widget (Most Reliable)

1. Open `zerodha-kite-totp.html` in Chrome (URL starts with `file:///`).
2. Tap **⋮ → Bookmark** (the star icon) to save it.
3. Go to your home screen, long-press an empty space, and select **Widgets**.
4. Scroll to **Chrome** and drag the **Chrome Bookmarks** widget (1×1 shortcut) to your home screen.
5. When prompted, select the bookmark you just saved.

You now have a tap-to-launch icon that opens the file directly in Chrome.

#### Method 2: Built-in File Manager Shortcut (Samsung / Pixel / Others)

1. Open your phone's built-in **File Manager** app (e.g. *My Files*, *File Manager*, or *Files*).
2. Navigate to the folder containing `zerodha-kite-totp.html`.
3. Long-press the file to select it.
4. Tap the **three-dot menu** (⋮) and choose **Add to Home screen**.

The shortcut will open the file in your default browser (Chrome).

## TOTP Secret

Your `KITE_TOTP_SECRET` is the base32 key embedded in the Zerodha 2FA QR code. You can extract it using any QR code scanner — look for the `secret=` parameter in the `otpauth://` URI.

> **Security note:** The secret is stored only in your browser's `localStorage` on your device. It is never transmitted anywhere.

## Clipboard Note

Chrome on Android requires `https://` or `localhost` for the native Clipboard API. If opening via `file://`, copy falls back to `execCommand('copy')`, which still works in most cases.
