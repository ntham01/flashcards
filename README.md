# Ficheiro

Simple flashcards. Each card has a front and a back, each with a title and an optional subtitle, and you flip through a deck with the arrows. Sign in with a username and password and your decks follow you to any device. Every device also keeps its own copy, so studying works offline and syncs when you're back online.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The whole app |
| `firebase-config.js` | Your Firebase project's keys (you fill this in) |
| `firestore.rules` | Database rules: each account sees only its own decks |

Without a filled-in `firebase-config.js` the app still works, but decks stay in that one browser.

## One-time setup (about 10 minutes, free)

Accounts need somewhere to live, and GitHub Pages only serves files. Ficheiro uses Firebase's free plan for sign-in and storage.

1. **Create a project.** Go to [console.firebase.google.com](https://console.firebase.google.com) → *Create a project*. Name it `ficheiro`. You can turn Google Analytics off.
2. **Turn on sign-in.** *Build → Authentication → Get started → Sign-in method → Email/Password* → enable the first switch → *Save*. Ficheiro turns your username into an internal address (`you@ficheiro.example.com`). No email is ever sent.
3. **Create the database.** *Build → Firestore Database → Create database*. Pick a location near you (for Europe, `eur3`), then start in **production mode**.
4. **Add the rules.** In Firestore, open the *Rules* tab, replace everything with the contents of `firestore.rules`, and press *Publish*.
5. **Get your keys.** *Project settings* (gear icon) → *General* → *Your apps* → the web icon `</>` → register an app called `Ficheiro` (no hosting needed). Copy the values from the `firebaseConfig` it shows into `firebase-config.js`.
6. **Publish on GitHub.** Make a repository (e.g. `ficheiro`) and upload all four files. Then go to *Settings → Pages → Build and deployment → Deploy from a branch*, choose `main` and `/ (root)`, and save. After a minute the app is at `https://<your-github-name>.github.io/ficheiro/`.
7. **Allow your site.** Back in Firebase: *Authentication → Settings → Authorized domains → Add domain* → `<your-github-name>.github.io`.

Open the site, choose **create an account**, and you're in. Sign in with the same username and password on your phone or any other computer.

## Good to know

- **Keep your password.** There's no email, so there's no "forgot password" link. If you lose it, you can delete the account in *Authentication → Users* and create it again. Now and then, use **download** in each deck's ⋯ menu to keep a copy.
- **Other people.** Anyone who opens your link can make their own account. They only ever see their own decks. To stop new sign-ups, go to *Authentication → Settings → User actions* and turn off *Enable create (sign-up)* once your account exists.
- **The keys in `firebase-config.js` are not secret.** Firebase web keys are meant to be public. The rules in `firestore.rules` are what protect your data.
- **Open it from the web, not as a file.** Sign-in doesn't work from a double-clicked `index.html` (`file://`). Use the GitHub Pages link, or run `npx serve` in the folder to test locally.
- **Add to home screen.** On a phone, use *Share → Add to Home Screen* and it opens like an app.
- **Moving from Anki.** In Anki, use *File → Export → Notes in Plain Text*, then press **+ → import** on Ficheiro's home screen.

## Using it

- **Home.** The cards icon at the top left always takes you back to your decks.
- **Decks.** The home screen lists your decks. Press **+** for **from scratch** (makes "New Deck 1", "New Deck 2" and so on, and opens it) or **import**. Hover a deck for **⋯** (or right-click it; on a phone the ⋯ is always there): rename, download, delete. Drag a deck to reorder it; on a phone, hold it for a moment first.
- **A deck** opens on its cover, which shows the title; tap it to flip to the deck's description, and press → to go to card 1. Edit the title and description at the top of the page. Tap a card to flip it. Use the **←** **→** buttons, swipe, or the arrow keys to move. **front first / back first** sets which side shows first.
- **Cover:** pick a colour in the row above the card, or press **cover** next to the colours to upload, change or remove an image. When you upload, drag to frame it and zoom with the slider; you see the final pixel-dithered cover as you adjust.
- **Lock in:** press **lock in** under the card counter to hide everything but the cards. Mark each card ✓ (knew it) or ✕ (didn't); both move on. At the end, **start over** brings back only the ✕ cards. Keys: → ✓, ← ✕, Space flips, Esc leaves. Nothing from lock-in is saved.
- **Adding cards:** press **+** next to **all cards**.
- **All cards** are listed further down the page. Scroll to bring them into view. Tap one to open it and edit or delete it; tap its title again to close it.
- **Download** in the ⋯ menu saves a deck as a file. **+ → import** on the home screen brings it back, or brings in a plain-text list (front, back on each line).
