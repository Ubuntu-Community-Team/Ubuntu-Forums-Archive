---
title: "how do i get sd cards to mount at boot up?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by thebestofall007 on 2008-08-19
i have a strange problem with sd cards not wanting to mount if they are in the slot if i boot up, but if i wait for the computer to boot up completely with the card unplugged, the card mounts when i plug it in. what do i do, or what configuration file do i edit (if i had to, like the fstab) to correct this problem? i don't have this problem with usb thumbdrives.

---

### Post by nicedude on 2008-08-20
Try getting a program called pysdm which is a mount manager in the repositories and in it select your SD card and look through the mount options there is one for device should mount at bootup, select that and press apply and see if it mounts when you reboot.

command to install pysdm

sudo apt-get install pysdm

command to launch it

sudo pysdm

Hope that does it since it is easy fix if it works for you.

---

### Post by thebestofall007 on 2008-08-25
> **nicedude said:**
> Try getting a program called pysdm which is a mount manager in the repositories and in it select your SD card and look through the mount options there is one for device should mount at bootup, select that and press apply and see if it mounts when you reboot.

command to install pysdm

sudo apt-get install pysdm

command to launch it

sudo pysdm

Hope that does it since it is easy fix if it works for you.



doesnt work for me. the device doesnt show.

---

