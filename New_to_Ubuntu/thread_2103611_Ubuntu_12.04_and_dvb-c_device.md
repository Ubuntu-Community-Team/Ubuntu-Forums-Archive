---
title: "Ubuntu 12.04 and dvb-c device"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Agnosticismus on 2013-01-10
Hi, i'm pretty new to Linux,and I'm having some issues getting a dvb-c working after reinstalling Ubuntu 12.04. The tuner is a terratec cinergy htc xs hd with empia 28xx chip.
I installed Ubuntu 12.04 a couple of weeks ago, and installed the v4l-dvb drivers from linuxtv.org following the "basic approach" and I worked great.
Now when I reinstall the drivers on a fresh installation of Ubuntu, and build the v4l drivers, the em28xx drivers are not build. And when I do mod probe em28xx, it says module not found. So I've tried using make menu config and selecting the chip, and thereafter make install, and then mod probe em28xx, the I get the error "
Unknown symbol in module, or unknown parameter (see dmesg) ". And I' m stuck... 
I would very much like a solution for my problem, but also an explanation what I'm doing wrong. If I have to update the kernel or other useful hints...

---

