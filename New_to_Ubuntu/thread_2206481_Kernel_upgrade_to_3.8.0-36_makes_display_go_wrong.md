---
title: "Kernel upgrade to 3.8.0-36 makes display go wrong"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by sanchises on 2014-02-19
Hi everyone,

Recently, my update manager installed the new linux-header packages, that upgraded my linux kernel to 3.8.0-36. However, on reboot, my display setup was completely screwed up (see below); however, when loading the previous 3.8.0-35 version from GRUB, everything works fine. Does anyone have an idea on **what could have gone wrong**? **Should I file a bug report of this?**

I'm using an **nVidia Quadro 1000M** with Optimus disabled (i.e.,** discrete graphics** mode) and a **secondary monitor** on the **VGA port.**
Instead of having two displays, with the new kernel I can **only** use my laptop display in 1024x768 and 800x600 instead of the intended 1600x900. The secondary monitor is **not detected** at all.

Some additional quirks, regardless of what kernel version, GRUB shows some interesting behaviour: with secondary monitor attached, GRUB runs in native resolution, and without secondary monitor it runs in low resolution (not sure if 800x600 or 1024x767).

I'm using Ubuntu 12.04 LTS. 

Thanks a lot!

P.S. I'm completely new here so I may have posted this in the wrong section - please be gentle on me ;)

---

### Post by PugIIIB on 2014-02-19
I might be having a similar problem. After updating to 3.8.0-36 my computer does not boot successfully, but instead pulls up tty1. This problem is fixed when (headers and image)-3.8.0-36-generic are removed.

I say that the problem might be similar because I have an nVidia graphics card as well and I have only ever seen this opening tty1 instead of booting problem before when I was first updating the nVidia drivers when I got my computer. Perhaps 3.8.0-36 gets along even more poorly with nvida than normal.

---

### Post by paul110 on 2014-03-04
Same problem here as well. NVIDIA driver version 319.82 fails to load on Ubuntu 12.04 (64 bit) with 3.8.0-36 headers. Booting with 3.8.0-35 headers is fine.

Similarly my second machine running an older version of ubuntu fails to boot after applying the latest updates.

Anyone know if there is a bug reported or a fix for this?

---

