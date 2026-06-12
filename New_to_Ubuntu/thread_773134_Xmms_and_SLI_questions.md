---
title: "Xmms and SLI questions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bobpur on 2008-04-28
First of all, I've got 8.04 (Hardy Heron) running pretty good on a home-built machine running a 3800+ x2 AMD processor on an ASUS A8N-32SLI Deluxe mobo with 2 X XFX 7600 GT videocards, 2 gbs kingston RAM, and 4 X 250 gbs Hard drives (2 X WD SATA & 2 X Seagate PATA). This was a Windows XP RAID 0 machine, No more! :)
Problem #1. I have Streamtuner and Streamripper installed which won't play without XMMS. I've found out that XMMS is no longer in Synaptic Pkg. Man. Just XMMS2 which doesn't work with Streamripper/tuner. It's not in Add / Remove programs either. Any ideas to get my tunes back? How about an alternative to Streamtuner/ripper? 
Problem #2. I removed one videocard to install Ubuntu and then installed the nvidia driver. After everything was up and running I decided to put back the other video card and the SLI setup just to see what would happen. My movies play great! and the screensavers play fast and smooth with great color. Do I have a functioning SLI Linux machine? If not, is SLI possible in linux? I've been looking for info on this but haven't found anything yet.

Thanks.

---

### Post by stchman on 2008-04-28
> **bobpur said:**
> First of all, I've got 8.04 (Hardy Heron) running pretty good on a home-built machine running a 3800+ x2 AMD processor on an ASUS A8N-32SLI Deluxe mobo with 2 X XFX 7600 GT videocards, 2 gbs kingston RAM, and 4 X 250 gbs Hard drives (2 X WD SATA & 2 X Seagate PATA). This was a Windows XP RAID 0 machine, No more! :)
Problem #1. I have Streamtuner and Streamripper installed which won't play without XMMS. I've found out that XMMS is no longer in Synaptic Pkg. Man. Just XMMS2 which doesn't work with Streamripper/tuner. It's not in Add / Remove programs either. Any ideas to get my tunes back? How about an alternative to Streamtuner/ripper? 
Problem #2. I removed one videocard to install Ubuntu and then installed the nvidia driver. After everything was up and running I decided to put back the other video card and the SLI setup just to see what would happen. My movies play great! and the screensavers play fast and smooth with great color. Do I have a functioning SLI Linux machine? If not, is SLI possible in linux? I've been looking for info on this but haven't found anything yet.

Thanks.

XMMS is severly outdated.  Use Audacious instead.

```
sudo apt-get install audacious
```

The people who created Audacious took the XMMS code and updated it.

All of the skins and such are still compatible.

---

