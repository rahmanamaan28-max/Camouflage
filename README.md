# Meccha Chameleon — deploy to GitHub Pages

This game now uses real WebRTC (via the free [PeerJS](https://peerjs.com)
public broker) for multiplayer, so it works across separate phones/devices —
not just multiple tabs on one browser. No backend of your own is required.

## Deploy in ~2 minutes

1. Create a new GitHub repository (public or private both work, but public
   is simplest if you don't have GitHub Pro).
2. Add this file to the repo as `index.html` (exactly that name, at the
   repo root — GitHub Pages serves it automatically as your homepage).
3. Commit and push.
4. In the repo: **Settings → Pages** → under "Build and deployment", set
   **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`.
   Save.
5. GitHub will give you a URL like
   `https://yourusername.github.io/your-repo-name/` — that's your live game.
   It can take a minute or two to go live the first time.

## Playing across devices

- One person taps **Create Room**, gets a 4-letter code, and shares it.
- Everyone else taps **Join Room** and types that code in.
- All players need to open the *same* GitHub Pages URL — the room code
  only matches people up; it doesn't matter if you're on wifi, cellular
  data, or different networks entirely, since it's peer-to-peer over the
  internet, not local-network-only.
- Keep the host's device on/awake for the whole round — connections are
  relayed through the host, so if they close the tab everyone else drops
  too.

## Notes

- Requires an internet connection (to reach PeerJS's free signaling
  server for the initial handshake). After that, gameplay data flows
  directly device-to-device.
- The PeerJS script is pulled from a public CDN
  (`cdn.jsdelivr.net/npm/peerjs@1.5.4`) — no npm install or build step
  needed, it's plain static HTML/CSS/JS.
- If you ever want your *own* signaling server instead of the shared
  public one (higher reliability for bigger groups), PeerJS supports
  self-hosting one — see their docs — but it isn't necessary for casual
  play with a handful of friends.
