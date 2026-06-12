---
title: "No Sound in Heron"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by GuitarHero on 2008-08-21
With a fresh install I'm not getting any sound.  It is recognizing my Audigy 1 Soundblaster card but nothing comes out of the speakers.  Yes they are plugged in and on. How do I troubleshoot this?

---

### Post by bitninja on 2008-08-21
Try running alsamixer from a terminal...if it's not installed, a simple apt-get install alsamixer should work. You might be able to turn up your levels if, for some reason, they are turned down or muted.

---

### Post by prshah on 2008-08-21
> **GuitarHero said:**
> With a fresh install I'm not getting any sound.  It is recognizing my Audigy 1 Soundblaster card but nothing comes out of the speakers.  Yes they are plugged in and on. How do I troubleshoot this?

Do you also have an internet (onboard) sound chip? In that case, you can check if sound is being directed to that, instead of your sound blaster, by plugging the speakers into those ports.

If that is the case, post back on how to disable the onboard sound and/or redirect sound to your soundblaster instead of the onboard.

---

