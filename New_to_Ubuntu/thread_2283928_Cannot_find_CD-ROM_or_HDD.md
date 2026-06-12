---
title: "Cannot find CD-ROM or HDD"
date: 2015-06-25
forum: New to Ubuntu
---

### Post by Jason_Stickler on 2015-06-25
Hello,

I am new to Ubuntu.  I am trying to install Ubuntu server on a Gigabyte Z97X-UD3H motherboard.  I have a Samsung 850 Pro as hdd and a standard DVD-ROM.  I initially attempted a USB install and it would not detect any device to install to except the USB drive.  I then tried burning the ISO to CD and I get in past detecting my keyboard and then I get a Retry mounting CD-ROM.  I honestly have no idea where to begin.

The HDD is completely blank - I have never used it for anything.  I feel like the issue is more of a problem with the chipset.

Thanks for your assistance.

---

### Post by dino99 on 2015-06-26
the first check to do is to know if these devices are found and well identified into the bios/uefi, then verify their settings

---

### Post by Jason_Stickler on 2015-06-26
The drive is recognized in the BIOS.  From what I can tell it looks like it might be UEFI settings though.  I have tried setting all to legacy with the same issues.  Someone suggested trying a USB drive cage to see if that makes a difference which I would imagine it will.  I think if I can install the OS then maybe I will have a little better luck figuring things out.

---

### Post by dino99 on 2015-06-26
ok it's a good news; let us focus on uefi needed settings for ubuntu installation: some howto/wiki to read first, that will set you more familiar with it
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

note: you talked about 'hdd', but i think you have that ssd : [http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era](http://www.anandtech.com/show/8216/samsung-ssd-850-pro-128gb-256gb-1tb-review-enter-the-3d-era)

and about ssd: 
[http://askubuntu.com/questions/519208/installing-ubuntu-on-a-ssd-and-hdd-system](http://askubuntu.com/questions/519208/installing-ubuntu-on-a-ssd-and-hdd-system)
[http://ubuntuforums.org/showthread.php?t=2243633](http://ubuntuforums.org/showthread.php?t=2243633)

---

### Post by llamabr on 2015-06-27
Are you saying you burned the iso with some other computer, and then  while doing the install, you get stuck after identifying your keyboard?  IF so:
1. Try making a new CD.  They sometimes don't copy right.  If that's not the issue:
2. There's a special thread for installation issues.  It's here:
[http://ubuntuforums.org/forumdisplay.php?f=333]("http://ubuntuforums.org/forumdisplay.php?f=333")

---

