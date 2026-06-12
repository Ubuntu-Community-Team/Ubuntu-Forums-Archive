---
title: "Ubuntu BusyBox installation"
date: 2017-11-23
forum: New to Ubuntu
---

### Post by thegoldenpig on 2017-11-23
I want to duel boot Windows 10 and Ubuntu 16.04, so I installed ubuntu to a 15G flash drive. When I boot into the drive, it shows a menu with options. If I click on "Try ubuntu" it shows a grey screen with white cursor blinking, then reboots into a BusyBox prompt. The same thing happens when I click on install. If I click help, any key I press goes into BusyBox. Any command in busybox gives me a kernel panic. How can I install ubuntu like this? I'm new to ubuntu, and don't know much.

---

### Post by yancek on 2017-11-23
I would suggest that you do an md5 checksum on the downloaded Ubuntu iso file to verify the download.  You might also post some information on the hardware you are using.  Also what software did you use on windows to create the bootable Ubuntu usb?

---

### Post by Geoffrey_Arndt on 2017-11-23
Plus, it's always good (often required even) to advise what your hardware specs are, especially the video system (nVidia, amd/ati, intel, etc.).   For creating a reliable boot usb, my preference is "Etcher" . . . 

[https://etcher.io/](https://etcher.io/)

---

### Post by C.S.Cameron on 2017-11-24
Welcome to the Forums.

Often times it is a bad **Persistent** install that causes BusyBox. 
Try a **Live** only install if you have previously been trying a **Persistent** install.
UNetbootin should work for that if you are using Windows.

---

