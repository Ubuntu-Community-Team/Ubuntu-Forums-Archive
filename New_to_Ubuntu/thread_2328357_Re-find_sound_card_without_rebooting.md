---
title: "Re-find sound card without rebooting"
date: 2016-06-20
forum: New to Ubuntu
---

### Post by Bill_McLaren on 2016-06-20
I am using Ubunto 16.04 as a host for Virtualbox (as well as general use).

The problem I have is that I use the PC with a TV and when the TV is switched off Ubuntu looses the sound device of the HDMI connection and reverts back to the internal speaker. If I reboot the PC after switching the TV back on it has the device again however, as I have to shut down several virtual machines to do that, it is a bit of a pain. Is there any way to force Ubuntu to recheck what it has connected (similar to a windows rescan for hardware)?

---

### Post by grahammechanical on 2016-06-20
You do not mention the Sound Settings utility. Can you not use that to re-direct the output from Built-in audio to HDMI/DisplayPort 2?

Regards.

---

### Post by HermanAB on 2016-06-20
You can also unload and reload the sound device driver (a kernel module) using lsmod, rmmod and modprobe.

---

