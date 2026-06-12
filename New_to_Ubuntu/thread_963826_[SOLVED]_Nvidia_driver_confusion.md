---
title: "[SOLVED] Nvidia driver confusion"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by EvilBro on 2008-10-30
I was under the impression that I have been using the nvidia driver all this time. However, today I looked at "Hardware Drivers" and it said the status of the NVIDIA accelerated graphics driver (latest cards) was "Not in use". Is there a way to see what I am actually using?

---

### Post by phidia on 2008-10-30
Open up /etc/X11/xorg.conf scroll down to "Devices" and read what's on the "driver" line.

---

### Post by EvilBro on 2008-10-30
> **phidia said:**
> Open up /etc/X11/xorg.conf scroll down to "Devices" and read what's on the "driver" line.
It says "nvidia", so I'm guessing that is what I am using. :) It also tells me I have a GeForce FX 5700, which is good as I had forgotten what type of card I owned. :)

Thanks!

---

### Post by phidia on 2008-10-30
Glad that helped!! There is a slightly easier way to do this too. > sudo dpkg -l nvidia*
But it didn't work on my system with a nvidia card so the old primitive way is more foolproof.

---

