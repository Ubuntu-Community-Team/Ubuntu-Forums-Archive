---
title: "S3 Savage graphics"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by bobmct on 2013-11-23
I'm trying to install a GUI onto a machine that has been running Ubuntu Server 12.04 successfully.  This machine is old and small  and has a 1.8Ghz CPU, 2GB RAM and its onboard video is 
VGA Built in S3 Savage8 high performance 128-bit 3D engine

I've been able to install Ubuntu 13.10 Desktop to the point of completion and when it reboots I have NO graphics what so ever.  

The logs show that the graphics is NOT configured correctly for this machine.

Would someone please advise the configuration parameters to use and which file(s) to place them so this will start in a usable form?

Thank you anyone. :confused:

---

### Post by mörgæs on 2013-11-24
The S3 cards are often troublesome. As a first attempt how does Lubuntu 13.10 work?

---

### Post by bobmct on 2013-11-24
Lubuntu 13.10 installed fine and ALL the screens were fine.  But then upon reboot they video goes haywire.
What kan I do the get into the system (pe-GUI) and run something like xorgfix, etc???

---

### Post by Yellow Pasque on 2013-11-25
If I have some time tonight/tomorrow, I'll try rolling a newer version (2.3.7) of the savage DDX driver for you in a PPA. I suspect you're hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/1225320](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/1225320)

[http://cgit.freedesktop.org/xorg/driver/xf86-video-savage/](http://cgit.freedesktop.org/xorg/driver/xf86-video-savage/)

---

