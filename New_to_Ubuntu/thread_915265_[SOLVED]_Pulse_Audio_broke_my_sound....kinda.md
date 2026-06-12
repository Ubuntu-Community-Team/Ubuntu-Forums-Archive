---
title: "[SOLVED] Pulse Audio broke my sound....kinda"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by cartisdm on 2008-09-09
First off, I hate to repost this thread but I really need to get the sound working.  Previously if I had Firefox open, I couldn't get sound in other programs.  I followed [this guide]("http://ubuntuforums.org/showthread.php?p=4928900") as recommended by another user and it fixed the sound problem.  But now, I don't have any sound AT ALL within firefox.  I can't hear youtube, ESPN, etc.

I can still hear stuff like Pidgin and VLC player with Firefox open or closed, but I can't get sounds out of FF at all no matter what.

:confused::confused::confused:

---

### Post by t0p on 2008-09-09
Have you tried the updated version of the guide you followed?  It's at [this link]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472").  It solved my pulseaudio and flash issues once and for all.

---

### Post by cartisdm on 2008-09-09
> **t0p said:**
> Have you tried the updated version of the guide you followed?  It's at [this link]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472").  It solved my pulseaudio and flash issues once and for all.


I ran through it just in case, but it was essentially the exact same thing.  Didn't fix the problem regardless

---

### Post by billgoldberg on 2008-09-09
Go to system -> preferences -> sound.

Switch everything to ALSA and it should work.

I don't think you need to log out or anything before it starts working.

The change should be immediate.

---

### Post by cartisdm on 2008-09-09
> **billgoldberg said:**
> Go to system -> preferences -> sound.

Switch everything to ALSA and it should work.

I don't think you need to log out or anything before it starts working.

The change should be immediate.

Nope, I even rebooted just to be sure.  Still same result.

---

### Post by cartisdm on 2008-09-10
No worries, I fixed it myself.  For anyone else curious, run the following command and restart Firefox

```
sudo apt-get install libflashsupport
```

---

