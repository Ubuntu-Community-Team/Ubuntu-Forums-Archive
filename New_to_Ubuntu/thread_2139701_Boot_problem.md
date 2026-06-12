---
title: "Boot problem"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by freaki1 on 2013-04-27
I installed Ubuntu 13.04 via DVD and everytime i restart, theres just a  black screen bith the blinking cursor. I tried updating my video driver,  but that did not help. i tried it with ubuntu 12.something, too but  there was the same problem. I searched 3 hours straight and tried  everzthing i found but nothing yet helped. I have the NVIDIA GeForce GTX  260 along with an asus M5A78L - M LX mainboard and the AMD FX-6100.

---

### Post by mkstallings1 on 2013-04-27
A tool I have that I have used a lot is Boot Repair.  You can download the .iso and burn it to disc, and when you run the live cd it will fix grub for you.  That could possibly be your problem that grub isn't configured correctly.

---

### Post by Feathers McGraw on 2013-04-27
> **mkstallings1 said:**
> A tool I have that I have used a lot is Boot Repair.  You can download the .iso and burn it to disc, and when you run the live cd it will fix grub for you.  That could possibly be your problem that grub isn't configured correctly.

+1

---

### Post by oldfred on 2013-04-27
While boot repair is good at fixing boot issues, it sounds like a video issue.
You can from boot repair add the nomodeset parameter or just manually add it yourself.
 Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply


       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

