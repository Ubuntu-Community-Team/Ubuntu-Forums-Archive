---
title: "How to install HD drivers?"
date: 2019-01-09
forum: New to Ubuntu
---

### Post by kibiras on 2019-01-09
Hello. Can anyone here explain me how to correctly install HD Graphic drivers?

---

### Post by deadflowr on 2019-01-09
Already installed, generally.
What card?

---

### Post by kibiras on 2019-01-09
> **deadflowr said:**
> Already installed, generally.
What card?

Intel Corporation HD Graphics 630

---

### Post by mastablasta on 2019-01-09
intel drivers are opensource and part of kernel (core of the OS), so they load at startup. there is no need for any additional install.
the issue is likely elsewhere not in GPU drivers.

edit: since drivers are in kernel - newer kernel= newer drivers version. if you are having issues with current drivers, then you have two easy options - either load a newer kernel to current OS or upgrade the OS.

---

### Post by kibiras on 2019-01-09
> **mastablasta said:**
> intel drivers are opensource and part of kernel (core of the OS), so they load at startup. there is no need for any additional install.
the issue is likely elsewhere not in GPU drivers.

edit: since drivers are in kernel - newer kernel= newer drivers version. if you are having issues with current drivers, then you have two easy options - either load a newer kernel to current OS or upgrade the OS.

Oh, that is awesome :). Thanks.

---

### Post by Impavidus on 2019-01-09
I think you're on Ubuntu 18.04, right? Ubuntu 18.04 somes with kernel 4.15. Newer kernels will come available as [HWE stacks](https://wiki.ubuntu.com/Kernel/LTSEnablementStack). In fact, it seems that [4.18 is already available](https://packages.ubuntu.com/bionic-updates/linux-generic-hwe-18.04), so if kernel 4.15 is not good enough for your hardware, try to install it with```
sudo apt install linux-generic-hwe-18.04
```That will be installed by default if you install from the 18.04.2 live disk, which will be released soon.

If it doesn't work, this change is easy to undo. Upgrading the entire OS is not easy to undo.

---

### Post by kibiras on 2019-01-09
> **Impavidus said:**
> I think you're on Ubuntu 18.04, right? Ubuntu 18.04 somes with kernel 4.15. Newer kernels will come available as [HWE stacks]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"). In fact, it seems that [4.18 is already available]("https://packages.ubuntu.com/bionic-updates/linux-generic-hwe-18.04"), so if kernel 4.15 is not good enough for your hardware, try to install it with```
sudo apt install linux-generic-hwe-18.04
```That will be installed by default if you install from the 18.04.2 live disk, which will be released soon.

If it doesn't work, this change is easy to undo. Upgrading the entire OS is not easy to undo.

But how to know when I need to update some drivers or other staff? I was thinkin Software Updater do all the job. If I have drivers why they wont update automatically :). I mean how to know when I need to update one or other thing?:D

---

### Post by QIII on 2019-01-09
If your hardware works right now, there is no reason to worry about updating drivers.  You can leave well enough alone.

The HWE stacks come out primarily to support newer hardware or to address issues with current hardware.

---

### Post by kibiras on 2019-01-09
> **QIII said:**
> If your hardware works right now, there is no reason to worry about updating drivers.  You can leave well enough alone.

The HWE stacks come out primarily to support newer hardware or to address issues with current hardware.

Meh I need to learn so much about Ubuntu.

---

### Post by oldrocker99 on 2019-01-09
> Meh I need to learn so much about Ubuntu.
Dude, I'm 70 and and I have been learning new things every darn day. I have been an exclusive Linux user, except for a year or so, dual-booting with Win7, for no other reason than to play Steam games. Then, Steam for Linux came out. Finally, there are tons of games for Linux, and now Steam has Steam Play, which, still in beta, runs about 50% of the Windows games I have tried. Others have screwy graphics, or no sound, unplayable or playable, but...

These are very good days for Linux users. There is, and always has been, software which can fulfill 98% of tasks you might want to accomplish, and it's all for free. Steam games for Linux, of course, need to be bought, although there is a raft of free-to-play Steam games, for example DOTA, and all you need is an account to have some fun for nuthin'.

---

### Post by kibiras on 2019-01-09
> **oldrocker99 said:**
> Dude, I'm 70 and and I have been learning new things every darn day. I have been an exclusive Linux user, except for a year or so, dual-booting with Win7, for no other reason than to play Steam games. Then, Steam for Linux came out. Finally, there are tons of games for Linux, and now Steam has Steam Play, which, still in beta, runs about 50% of the Windows games I have tried. Others have screwy graphics, or no sound, unplayable or playable, but...

These are very good days for Linux users. There is, and always has been, software which can fulfill 98% of tasks you might want to accomplish, and it's all for free. Steam games for Linux, of course, need to be bought, although there is a raft of free-to-play Steam games, for example DOTA, and all you need is an account to have some fun for nuthin'.

You keep me motivated :D.

---

