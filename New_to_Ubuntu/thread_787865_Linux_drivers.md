---
title: "Linux drivers"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Google Spider on 2008-05-09
After installing a Linux distro, how many drivers do you have to install?

I just install the video driver and everything else just works automagically...there is sound in the speakers and I am connected to the internet :guitar:

But in windows I have to install Video driver, sound driver, chipset(?) driver and modem driver.

So are the other drivers included by default in common distros like Mint, Ubuntu, Mandriva?

I doubt that I'm not utilizing the full potential of my hardware.:( Should I search and install driver for my sound card?

---

### Post by hyper_ch on 2008-05-09
drivers are mostly included...

---

### Post by Steveway on 2008-05-09
The Linux-kernel is a monolithic kernel, that means that everything is included.
So in an ideal world every driver would be in the kernel.
Sadly companies most companies don't give out open-source drivers so they can't legally be included in the kernel and have to be installed in another way. (ex. NVIDIA-drivers, some W-Lan drivers...)

---

### Post by Google Spider on 2008-05-09
> **hyper_ch said:**
> drivers are mostly included...

How do I manually check that the sound driver *is* installed? Is it possible to play mp3's without the sound driver installed?

---

### Post by bumanie on 2008-05-09
The majority of drivers are included in the kernel Sometimes very new hardware is not, but kernels get regular upgrades to help cope with this. The open source community does very well, seeing they don't have access to proprietary source code. But that is what the open source community attempt to do, is have most things working upon install. You will find that you will have to install some things like multi-media codecs and a few other things, but most hardware will run OK without doing anything more.

---

