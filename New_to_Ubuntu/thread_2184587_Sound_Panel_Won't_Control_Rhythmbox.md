---
title: "Sound Panel Won't Control Rhythmbox"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by loganellis17 on 2013-10-29
Upon upgrading to 13.10, rhythmbox kept crashing on startup, so I updated to rhythmbox 3.0 and that fixed the problem. Now, though, in the sound panel in the top right of the screen I can't control rhythmbox. Clicking the play button will start up rhythmbox as it always has, but I can't skip, pause, or play songs. I tried editing the settings with dconf -editor, but it still isn't working. What can I do to get it working again?

---

### Post by sandyd on 2013-10-29
> **loganellis17 said:**
> Upon upgrading to 13.10, rhythmbox kept crashing on startup, so I updated to rhythmbox 3.0 and that fixed the problem. Now, though, in the sound panel in the top right of the screen I can't control rhythmbox. Clicking the play button will start up rhythmbox as it always has, but I can't skip, pause, or play songs. I tried editing the settings with dconf -editor, but it still isn't working. What can I do to get it working again?

How did you update to 3.0?

---

### Post by loganellis17 on 2013-10-29
I downloaded it from the repository ppa:jacob/media, after first removing the old version of rhythmbox.

---

### Post by mc4man on 2013-10-29
I'd probably start by seeing if a new user or guest session has this issue. 
A guest session should suffice, log into, open nautilus, browse to Computer > home > your user > Music & copy a couple of tracks to the Music folder for guest (or new user you've created if doing that way

After copy is done open RB, then ck. in sound menu & see if it works

Tried the ppa, nothing is amiss here (do wonder why librhythmbox-core7 is still there but shouldn't be an issue in most cases

---

### Post by loganellis17 on 2013-10-30
The guest session does not have this issue, I can play, pause, and skip songs without any problem.

---

