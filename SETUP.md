# Launch Message: Setup Guide

You'll do three things: put the app online (free), add it to your iPhone's Home Screen, and build a 4-step Shortcut that does the sending.

---

## 1. Put the app online (on your Windows PC, about 5 minutes)

iPhones can only install web apps from a website, so the files need a free host. GitHub Pages is free and permanent.

1. Go to https://github.com and create a free account if you don't have one.
2. Click **+** (top right), then **New repository**. Name it `launch-message`, choose **Public**, and click **Create repository**.
3. On the next page, click **uploading an existing file**. Drag in these four files: `index.html`, `manifest.json`, `icon-180.png`, `icon-512.png`. Click **Commit changes**.
4. Go to the repo's **Settings**, then **Pages**. Under "Branch", pick **main** and **/ (root)**, then click **Save**.
5. After about a minute your app is live at `https://YOUR-USERNAME.github.io/launch-message/`

> The phone number and message are **not** in these files. They're stored only on your iPhone, so the public page holds nothing personal.

## 2. Add it to your iPhone's Home Screen

1. On the iPhone, open that link in **Safari**.
2. Tap **Share** (the square with an arrow), then **Add to Home Screen**. Make sure **Open as Web App** is on, then tap **Add**.
3. Open **Launch** from the Home Screen, tap the **gear**, enter the phone number and message, and tap **Save**.

## 3. Build the Shortcut (on the iPhone)

iOS doesn't let any app (App Store apps included) send a text silently by itself. Apple's **Shortcuts** app can, so the red button hands the number and message to this Shortcut.

1. Open **Shortcuts**, tap **+**, and name it exactly **Launch Message**.
2. Add these actions in order (use the search bar at the bottom):
   1. **Get Dictionary from Input**. It should read "Get dictionary from *Shortcut Input*".
   2. **Get Dictionary Value**. Set it to: Get **Value** for key `to` in **Dictionary**.
   3. **Get Dictionary Value** again. Set it to: Get **Value** for key `msg` in **Dictionary**.
   4. **Send Message**:
      - Tap the **Message** field, then choose the variable **Dictionary Value** (the *second* one, which is `msg`).
      - Tap **Recipients**, then choose the variable **Dictionary Value** (the *first* one, which is `to`).
      - Tap the **>** arrow on the action and turn **Show When Run** **OFF**. This setting is what makes it send without you tapping send.
3. Tap **Done**.

### First run
- Press the red button. iOS may ask to open Shortcuts, so tap **Open**.
- The first time, Shortcuts asks whether "Launch Message" may send a message. Tap **Always Allow**.
- After that, one press sends one text. The button locks for 4 seconds afterward so a double-tap can't send two texts.

**Test it with your own number first.**

---

## No-setup fallback
In the app's Settings, switch **Send method** to **Open Messages**. The button then opens Messages with the number and text already filled in, and you tap the send arrow. No Shortcut is needed.

## Troubleshooting
- **"Shortcut not found":** the name in the app's Settings must match the Shortcut's name exactly.
- **Message is blank or wrong:** check that the two Dictionary Value variables in Send Message aren't swapped.
- **It asks for confirmation every time:** make sure **Show When Run** is off on the Send Message action.
