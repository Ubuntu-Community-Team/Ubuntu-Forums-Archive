---
title: "No network connection on USB hard drive install"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Alpha Beta on 2008-09-18
This is my first post in any kind of forum, and I already checked Google to see if my problem has already been encountered, and I couldn't find it, so here I am. I also am a complete Ubuntu newbie.:)
On my laptop, my computer is set to dual-boot between Windows Vista and Ubuntu. Since Vista is my primary OS (sorry guys, I love Ubuntu but I feel more comfortable in Windows; plus I am a PC gamer), my Ubuntu partition is only about 10 GB. I bought a external hard drive, separated it into two partitions, and installed Ubuntu on the second partition. I don't really need it on there, but I wanted to try it out just for fun. Still, it might come in useful one of these days, and there is already plenty of room on the hard drive. I got Ubuntu to boot from it successfully, so I thought I was happy. However, when it come time to plug in my ethernet cable into my laptop, it wouldn't connect. The system tray icon would just keep looping with only one of the green circles filled in. I let it sit there for 5 minutes and it doesn't stop. I have since removed it from my USB drive, but I want it back. The network and even wireless works fine when it runs from the laptops hard drive. I am just curious as to what the problem is. I'll try to check if anybody has any solutions any chance I get. Thanks.

---

### Post by bobnutfield on 2008-09-18
If you can boot into Ubuntu, do so an open a terminal and type:

> sudo ifconfig -a

This will tell you what network interfaces Ubuntu is recoginzing.  If they are being properly recognized, it may just be a matter of configuring them.  When you run those commands, make sure both the ethernet and the wireless are plugged in.  Post the results.

---

