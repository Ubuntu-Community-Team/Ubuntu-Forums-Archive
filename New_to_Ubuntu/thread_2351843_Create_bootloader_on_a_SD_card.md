---
title: "Create bootloader on a SD card"
date: 2017-02-07
forum: New to Ubuntu
---

### Post by tharmund on 2017-02-07
I am new to linux, I installed Lubuntu,        I installed the bootloader on an USB drive, so I have to connect it in order to boot the OS, but I need the USB drive for stuff, and I have a unused 1 GB SD card,     is there any way to create a bootloader on the SD card? 

**I am new to linux, therefore I need step by step instruction.**

---

### Post by yancek on 2017-02-07
You should be able to.  You would need to first determine which device is the SD Card and do a standard sudo grub-install /dev/???   (Replace the ??? with the actual correct device name in the command). The Ubuntu documentation explains different methods at the link below.  Since you have a working system, it shouldn't be that difficult especially on a system with only one OS and that being a Linux OS.

 [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System)

---

### Post by ajgreeny on 2017-02-07
If your machine uses a built in card reader you also need to know if the machine can boot from that; not all machines can do so.

---

### Post by tharmund on 2017-02-07
Yes it does, that is why I mentioned an SD card... and I finally did, now the bootloader in on the SD and the OS boots.

---

### Post by ajgreeny on 2017-02-08
Great news!
Please mark as SOLVED from the Thread Tools menu up top.

---

