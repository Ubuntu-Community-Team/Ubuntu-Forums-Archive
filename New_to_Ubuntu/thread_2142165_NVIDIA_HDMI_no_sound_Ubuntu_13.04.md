---
title: "NVIDIA HDMI no sound Ubuntu 13.04"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by divxpr on 2013-05-04
Hi everyone,

I know there must be like a billion of this thread but i cant find a solution, i had been hours looking for an answer and im getting frustrated.

So i have a HP PC with a Nvidia GeForce GT 240 card connected to a Samsung HDTV.

The problem is that i don't have sound. I tried a lot of " solutions" that havent solved my problem.

I already installed Nvidia X Server and at the "Sound Settings" i got this 2 options, but no HDMI.

Digital Output (S/PDIF)
Built in Audio

Analog Output
Built in Audio


Please give me all the information you can, i'm an absolute newbie.

Regards,

Iván

---

### Post by jajodo on 2013-05-05
This is a known bug.  For me and some others installing this deb fixes it [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages).  Select the version for raring.  Other users have had to update the kernel.

---

### Post by jajodo on 2013-05-05
Just realized there is more than one file type there.  This is the exact link: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+sourcepub/3158528/+listing-archive-extra](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+sourcepub/3158528/+listing-archive-extra)

---

