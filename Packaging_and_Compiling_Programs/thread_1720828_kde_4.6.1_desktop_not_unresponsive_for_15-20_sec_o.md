---
title: "kde 4.6.1 desktop not unresponsive for 15-20 sec on first log in"
date: 2011-04-03
forum: Packaging and Compiling Programs
---

### Post by oobuntoo on 2011-04-03
On the very **first log in** and **after** splash screen, KDE desktop is not responsive for about 15-20 seconds. **After** the start-up sound is played, then the desktop is responsive again. What is the cause of this long delay? Anyone one else experienced this? I'm beginning to think that this has something to do with pulseaudio.

---

### Post by oobuntoo on 2011-04-05
Since most people here don't use Kubuntu, I had to look for my own answer. Removing pulseaudio solved my problem.

---

### Post by Kevbert on 2011-04-06
Seems OK here. Tried the Daily Build which failed to install 100% due to an un-named package. Rebooted in repair mode and selected repair all damaged packages. Reboot then seemed to be as fast as normally expected.
Unfortunately Ubuntu 11.04 Daily Build failed at the same point and that won't boot at all due to a missing kernel (both normal and repair modes).

---

