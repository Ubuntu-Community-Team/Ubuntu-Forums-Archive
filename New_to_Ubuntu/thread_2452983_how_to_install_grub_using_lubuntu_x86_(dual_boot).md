---
title: "how to install grub using lubuntu x86? (dual boot)"
date: 2020-10-31
forum: New to Ubuntu
---

### Post by spanishsteve on 2020-10-31
Hello,
I installed Windows 7 and lubuntu 19.04 x86 in the same computer (dual boot), but it does not appear the grub screen to choose between Windows 7 and lubuntu. I may be wrong, but after installing lubuntu I think that on the screen says that I have to format my USB device to install the grub and I cannot do that because the lubuntu installer is in the device. What should I do? 
Thanks.

---

### Post by yapidumoac on 2020-10-31
[The Ultimate Windows 7 and Ubuntu Linux Dual Boot Guide]("https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653")

---

### Post by Deep_Peasant on 2020-10-31
Both OS on one drive?

First thing I would do is shutdown PC. Remove USB installer. Start PC.

What OS boots your PC to then?

---

### Post by guiverc on 2020-10-31
Lubuntu 19.04 (along with all 19.04 products) is EOL or *end-of-life*.

For validation, you can view

 - [https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-19-04-end-of-life-and-current-support-statuses/) or 
- [https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/](https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/)

Unless you used an *alpha* 19.04 ISO image, or *release-upgraded* from 18.10 (on an i386 install), you will be using an *amd64* or x86_64 system, which means you can use the current Lubuntu 20.04 LTS or Lubuntu 20.10 system.

If you are using x86 (32-bit i386) then returning to Lubuntu 18.04 LTS is the safest course of action, as 19.04 was the last release with full x86/i386 support, and it's been EOL for some time now.

If you just installed it, I would try and fix it, but instead re-install a supported release of Lubuntu.

---

