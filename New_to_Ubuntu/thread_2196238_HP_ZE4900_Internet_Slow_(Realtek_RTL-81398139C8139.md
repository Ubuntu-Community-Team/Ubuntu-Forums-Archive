---
title: "HP ZE4900 Internet Slow (Realtek RTL-8139/8139C/8139C+)"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by firstdefence on 2013-12-28
Hi all, trying to help a friend who has an ancient HP ZE4900 Laptop. XP was dire, so, I suggested Linux and to my surprise he said Okay. I tried quite a few different distros but the lack of PAE on the CPU limited me and in the end the only one that installed was Lubuntu: lubuntu-10.04-desktop-i386 to be exact.

Everything appears to have installed correctly and as far as I know the drivers for the network codec: RTL8139/81/8139C/8139C+ installed okay too. I went to the Realtek site to check for driver updates but I think the latest drivers were built into the kernel.

The memory for the system is only 384MB but everything else seems to run pretty well.

Downloads are quick; I have orange 38MB Fibre and downloaded Firefox in seconds, I considered it might be the chromium browser. Ok installed Firefox and it is much faster, so I have to assume the Chromium browser is duff, I'll try few more...

---

### Post by firstdefence on 2013-12-28
Definitely the browser, installed Konqueror with a few add-ons and its much quicker, Firefox is a close second. So I've removed Chromium Web Browser and will stick with Firefox and Konqueror, might try Swiftfox too later on.

---

### Post by mörgæs on 2013-12-28
Hi, welcome to the fora.

10.04 is a security hazard and should not be used any more.

Here's some options for dealing with the [PAE]("https://help.ubuntu.com/community/PAE") problem. Installing Bodhi Linux is probably the easiest solution.

---

