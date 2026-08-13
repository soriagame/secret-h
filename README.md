# Secret Hitler — Table Companion

An unofficial, non-commercial fan-made companion app for playing **Secret Hitler** in person. Each player uses their own phone for secret roles and anonymous voting, so nothing has to be passed around the table.

**This is not an official product.** It is not affiliated with, endorsed by, sponsored by, or connected to Goat, Wolf & Cabbage or any of the creators or publishers of Secret Hitler.

## Credits

Secret Hitler was designed by **Mike Boxleiter, Tommy Maranges and Max Temkin**, illustrated by **Mackenzie Schubert**, and published by **Goat, Wolf & Cabbage** — <https://www.secrethitler.com/>

All credit for the game's design, rules and identity belongs to them. If you enjoy the game, [buy a physical copy](https://www.secrethitler.com/) and support the people who made it.

The optional special-roles variant adapts the information structure of roles from **The Resistance: Avalon** by Don Eskridge. That variant is an original reimplementation and is likewise unaffiliated with and unendorsed by Avalon's creators or publishers.

## Licence

The original game is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-nc-sa/4.0/).

In accordance with the ShareAlike condition, **this adaptation is released under the same licence** — see [LICENSE](LICENSE) for the full notice, including a complete statement of changes made.

You may copy, modify and redistribute this app, provided you credit the original creators, keep it non-commercial, and release your version under the same terms.

## What it does

- **5–10 players**, with role counts and the presidential-power board adjusting automatically
- **Secret roles dealt privately** to each phone. Fascists see each other; Hitler sees them only at 5–6 players, per the printed rules
- **Anonymous voting** — only the Ja/Nein totals are ever shown, never who voted which way
- Full legislative session, veto power, election tracker with chaos, all presidential powers, and all four win conditions
- Tap-to-reveal role badge so you can check your role without exposing it to a neighbour
- Rejoining works: same name and code restores your seat if a phone dies

### Optional special roles

Off by default. When switched on, these occupy existing Liberal and Fascist seats, so the party balance never changes.

| Role | Side | What it does |
|---|---|---|
| **Churchill** | Liberal | Secretly knows the Fascists — but not the Gestapo |
| **The Spy** | Liberal | Shown two names, one of whom is Churchill |
| **Gestapo** | Fascist | Invisible to Churchill; otherwise a normal Fascist |
| **The Italian** | Fascist | Knows no one, known by no one; Churchill can see them |
| **Doppelgänger** | Fascist | Appears to The Spy as a possible Churchill |
| **The Executioner** | Fascist | If the Liberals reach five policies, gets one shot to name Churchill |

The lobby gives live balance advice and blocks invalid combinations. **Churchill & Gestapo** is the recommended pairing and works from five players up; Churchill on its own is noticeably Liberal-favoured.

Note that all four Fascist roles can never be enabled at once — there are only three Fascist seats even at ten players.

## Running your own copy

It's a single HTML file with no build step. It needs a free [Firebase Realtime Database](https://console.firebase.google.com/) to sync devices.

1. Create a Firebase project, then add a **Realtime Database**.
2. Set the database rules. **Do not leave it in test mode** — those rules expire after 30 days and the app will stop working without warning. Use the contents of [`firebase-rules.json`](firebase-rules.json) instead.
3. Paste your database URL into the `FIREBASE_DB_URL` constant near the top of the script in `index.html`.
4. Host the file anywhere static — GitHub Pages works well. The file must be named `index.html`.

If you leave `FIREBASE_DB_URL` empty, the app shows a setup screen that walks through this.

## Known limitations

- **Roles are not secret from a determined player.** Game state lives in an open database, so anyone who opens browser developer tools can read every role. Fine among friends; unsuitable if someone would cheat. Fixing this properly needs server-side dealing.
- The database rules above are fully open — anyone with the URL can read and write it. Keep that Firebase project for this game only.
- Players who join after a deal must wait for the current game to end; they're included in the next one.
- If a game gets stuck because someone's phone died, any player can abandon it from the "Game stuck?" panel.

## Note on the subject matter

Secret Hitler is a social deduction game about the danger of creeping authoritarianism and how ordinary institutions can be captured from within. Its subject is treated as a cautionary one. Nothing here endorses fascism or the historical figure the game is named for.

## No warranty

Provided as is, for private play among friends, with no guarantee of being bug-free or a faithful implementation of every rule. Where this app and the published rulebook disagree, **the rulebook is correct**.
