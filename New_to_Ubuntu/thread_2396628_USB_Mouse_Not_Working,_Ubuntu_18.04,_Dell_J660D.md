---
title: "USB Mouse Not Working, Ubuntu 18.04, Dell J660D"
date: 2018-07-18
forum: New to Ubuntu
---

### Post by punonymous on 2018-07-18
I'm new to Linux, just created a Live USB to test moving away from Windows 7. When I boot in Ubuntu, the old USB mouse doesn't work, although the cursor appears to move automatically just a little right after it appears as the computer loads Ubuntu. After that, it won't do anything.

I've tried updating Xorg, but that didn't help. This is what I got from lsusb:

Bus 003 Device 001 ID: 1d6b:002 Linux Foundation 2.0 root hub
Bus 007 Device 001 ID: 1d6b:001 Linux Foundation 1.1 root hub
Bus 006 Device 001 ID: 1d6b:001 Linux Foundation 1.1 root hub
Bus 002 Device 002 ID: 1d6b:002 Linux Foundation 2.0 root hub
Bus 005 Device 001 ID: 1d6b:001 Linux Foundation 1.1 root hub
Bus 001 Device 001 ID: 1d6b:002 Linux Foundation 2.0 root hub
Bus 004 Device 001 ID: 1d6b:001 Linux Foundation 1.1 root hub
Bus 009 Device 002 ID: 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 009 Device 002 ID: 1d6b:003 Linux Foundation 3.0 root hub
Bus 008 Device 002 ID: 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001 ID: 1d6b:002 Linux Foundation 2.0 root hub

The flash drive shows up, but I should also be seeing my mouse (Dell J660D), but I don't (and a Panda Wireless PAU06 USB card, but that's a different matter). I read on another thread that it should be working with the rt2800usb driver which that poster said should have come with the distro, but...

What should I do next?

---

