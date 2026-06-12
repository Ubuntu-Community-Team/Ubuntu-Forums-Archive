---
title: "Suspend and stream, lost widgets, and MP3"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by clixis on 2008-05-16
As a NOOB (Heron) at last I have it down to 3 outstanding questions (until I discover the next one!):

1. Streaming video in Firefox, such as from the CNN and ESPN websites, works fine after I boot up, but after I suspend Linux and come back I can no longer stream video or audio. Is this a bug or is it me?

2. After enabling compiz, I sometimes lose the the three widgets in the upper right corner of each window, so I can't close or minimize them. I don't know if this is related to compiz.

3. Is there an app that burns MP3 audio CDs? I can listen to MP3 audio in the Movie player, but neither Brasero or GnomeBreaker seem to write MP3s.

---

### Post by herbster on 2008-05-16
1. Suspending/hibernating can cause issues upon restoring/booting back up. For me, I get no sound, and after thorough testing some time ago discovered it's my sound card driver. Which video card are you using? And do you close and restart the browser? When you restore do you logout/log back in and then attempt again to open the browser and stream?

3. Yes, use K3b, it's the king of burning solutions IMO. Should be as simple as

```
sudo apt-get install k3b
```

Can't help you with #2, not a compiz user, but others will chime in.

---

### Post by clixis on 2008-05-16
Thanks herbster for the info.

Regarding suspend/hibernate, I have a Radeon R300 (ATI) video card and the driver is fglrx. Neither the Movie Player nor Firefox works afterwards. Closing and restarting the Movie Player or Firefox does not cure the problem. But if I do a Restart of Linux, reboot and relog in, everything works - until I suspend again.

Thanks for the tip on k3b - I thought it would only run on KDE.

---

