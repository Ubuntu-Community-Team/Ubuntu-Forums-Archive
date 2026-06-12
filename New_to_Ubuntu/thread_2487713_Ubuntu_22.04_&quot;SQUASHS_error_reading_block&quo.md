---
title: "Ubuntu 22.04 &quot;SQUASHS error reading block&quot; during installation"
date: 2023-06-13
forum: New to Ubuntu
---

### Post by rvfet on 2023-06-13
Hi everyone, first of all I gotta say that I'm fairly new to Linux (been using windows since 2014).

When I try to run the installer that is written to my USB Stick using Ventoy I'm getting "SQUASHFS error reading block" errors with "-5" at the end. I got no clue what it means but did quite a lot of research before asking it in here. I tried flashing the .iso with Rufus, belenaEtcher and even Unetbootin but still got the same error. I did a checksum with both SHA256 and MD5 and both showed that the .iso is indeed not corrupted. As I mentioned earlier I'm not that experienced with "Linux", so I can't even figure out what might be the problem. I read bunch of similar questions on AskUbuntu and other forums that I came across but none of them led me to a solution.

If needed, I can provide further information, thanks in advance and have a nice day!

---

### Post by Rubi1200 on 2023-06-13
Hi and welcome to the forums :-)

What are the computer specs. such as RAM, graphics, make and model of laptop/computer? Do you want to try or install? Do you want to dual-boot alongside Windows? Have you set BIOS to boot from the liveUSB?

Might be worth trying but sometimes I use DD mode with Rufus if an image is not booting up as expected. Have you tried a different USB stick?

---

### Post by Holger_Gehrke on 2023-06-13
Squashfs is a compressed file system. There's an image of such a filesystem in the ISO that is used as the root file system for the live system / installer. Either the downloaded image is broken or your USB stick is faulty.

Holger

---

