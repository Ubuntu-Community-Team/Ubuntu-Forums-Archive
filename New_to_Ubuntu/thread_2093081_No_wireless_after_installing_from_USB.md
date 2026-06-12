---
title: "No wireless after installing from USB"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by la508 on 2012-12-09
Hello everyone! 

I am a [SIZE=4]complete beginner[/SIZE] in Ubuntu. I have just got a new computer and put in a 2nd hard drive to run Ubuntu 12.10. Firstly, I booted from a USB and selected "Try Ubuntu" to have a play around and make sure the wireless worked. I clicked the wireless icon in the top right and my home networks were displayed and there was no trouble in connecting. This required no fiddling with drivers or anything.

However, once I did the installation my networks are no longer listed. I did some Googling and ran ```
sudo lshw -C network
```This only showed my ethernet, so I ran ```
lsusb
```This lists my wireless adapter as Broadcom 4320 somethingsomething... so it's picking it up. I assume, with my my pretty limited knowledge, that it's lost the drivers somewhere between the Try Ubuntu and installation.

Any ideas how to get it working again? Thanks everyone.

---

### Post by Bucky Ball on 2012-12-09
Welcome to the forums. 

Strange that, but try looking in Additional Drivers. Is there the Broadcom STA driver in there unticked? Have you plugged in an ethernet cable and is that working? if so, get your updates (with the dongle plugged in) and see if that picks up the wireless dongle.

---

### Post by la508 on 2012-12-09
Thanks for the welcome. Like I said, I'm a  total beginner so I might be spending a lot of time around here.

I posted that from Windows 8 and strangely, after I booted back to Ubuntu to check Additional Drivers, it picked up the wireless fine - guess it just needed a restart after the first installation. Now I feel a little silly. #-o

---

### Post by Bucky Ball on 2012-12-09
No need. Glad it's all working. Broadcom is very well supported in Linux now days. 

Enjoy the OS and the learning curve and see you round the forums. ;)

---

