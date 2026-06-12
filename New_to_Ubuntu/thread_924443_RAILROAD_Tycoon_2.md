---
title: "RAILROAD Tycoon 2"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by monolux on 2008-09-19
I've installed rrt2 in my linux mint...but can't seem to make it go full screen, nor can hear any sound! Can anyone help me?

---

### Post by perlluver on 2008-09-25
> **monolux said:**
> I've installed rrt2 in my linux mint...but can't seem to make it go full screen, nor can hear any sound! Can anyone help me?

This appears to be a wine problem, beings that RRT2, is not a Linux game, I would check [Wine HQ]("http://www.winehq.org/") to see how it ran and what marks it got.

---

### Post by Keith_Beef on 2009-01-04
No sound here, either.

```
$ /usr/local/bin/rt2
Warning: Unable to open audio: Couldn't open audio device or ESD connection

```

---

### Post by ernstblaauw on 2009-05-07
> **perlluver said:**
> This appears to be a wine problem, beings that RRT2, is not a Linux game, I would check [Wine HQ]("http://www.winehq.org/") to see how it ran and what marks it got.

No, Railroad Tycoon is actually available as a Linux game. Wine is not needed.

I don;t have sound either - it seems the program can't access /dev/dsp for some reason. I'm running Jaunty, and I don't have find the answer yet (I already installed the package alsa-oss). 

Does someone here got sound with this game (or another Loki game)?

---

### Post by Dry Heat on 2009-05-23
I do have sound under Railroad Tycoon 2.
I'm running Ubuntu 9.04 "Jaunty Jackalope".
I have a C-Media CMI8768 sound card.
(The commercial name is a Diamond Xtreme Sound 7.1).
Under System/Preferences/Sound, I have manually selected the C-Media ALSA driver.
(As opposed to the Pulse Audio driver that is the default under Jaunty).
I had problems originally with sound when running WINE games, but seemed to resolve them by doing the above.
Now it seems to work with native games as well.
I have Sim City 3000 and Neverwinter Nights running with sound, as an example.

Hope this helps.  Let me know if you need further info.

Dry Heat   :popcorn:

---

