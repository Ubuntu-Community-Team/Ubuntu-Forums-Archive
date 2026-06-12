---
title: "TV/Display falls asleep even though active in OS"
date: 2017-06-25
forum: New to Ubuntu
---

### Post by borg101 on 2017-06-25
I'm trying out Ubuntu on my HTPC and I'm running into an issue.  The TV doesn't receive an activity signal from my GTX960 via HDMI.  Normally, I would assume this to be a hardware issue, but this is not the case with Mint 17, 18, and 18.1, nor Elementary OS Freya or Loki....all of which I've run on the same HTPC/TV setup.  I am using the latest NVIDIA driver instead of xorg.  Any ideas?

---

### Post by ajlongstreet on 2017-06-26
Are you using Nvidia drivers [COLOR=#000000][FONT=&quot]375.66?[/FONT][/COLOR]

---

### Post by Autodave on 2017-06-28
Did you disable the screen saver?

---

### Post by borg101 on 2017-06-28
> **Autodave said:**
> Did you disable the screen saver?
I did and that fixed it.  Thanks

---

### Post by borg101 on 2017-06-28
> **ajlongstreet said:**
> Are you using Nvidia drivers [COLOR=#000000][FONT=&amp]375.66?[/FONT][/COLOR]
I am.  I found that if I turned the screensaver off, it no longer happened.  As I mostly use my PC for movies and games and all the software I use has built in screensavers, it's not a huge deal to lose it.

---

