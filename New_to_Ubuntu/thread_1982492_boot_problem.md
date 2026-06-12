---
title: "boot problem"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by spkanu on 2012-05-18
Hi 
i am new to ubuntu.
When i was trying to update ubuntu 11.10 to ubuntu 12.04, accident the power was shut n the update process did not completed.
It was installing the update files n it happens.
Now my laptop dos't start n said for the recovery n the grub screen appears.

Can anybody help me out.......

---

### Post by PhantomTurtle on 2012-05-18
Well if something important is damaged then it might not be worth your time trying to recover this installation. First you want to recover any important files by using the Ubuntu live cd and copying them to a USB drive or something else. Now you don't remove the live CD. Next try to recover grub. Use this link to install Boot-repair in the live environment: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Now if this works and grub loads. Next you want to go into recovery mode(choose it in the grub menu)(to get grub menu press escape at boot). Now select dpkg  repair broken packages, and it will attempt to fix the packages that might be broken and install updates. If this doesn't work, I think it would be easier to boot into the live cd and reinstall.

---

### Post by spkanu on 2012-05-19
I tried to run live cd but it dosent work.

When i start my laptop a black screen comes and written as GNU GRUB version 1.99-21ubuntu3

ubuntu, with linux3.2.0-24-generic
Ubuntu,  with linux3.2.0-24-generic (recovery mode)
Previous linux version 
memory test (memtest86+)
Memory test (memtest86+, serial console 115200)


But any of these option dosent work.
It said no such partition

Below there is a option for the edit the commands before booting or for command-line.

---

### Post by PhantomTurtle on 2012-05-19
That might just mean that it is very badly broken, there might not be a way to fix it. Make sure to backup your important files first. Might be easier to start over by reinstalling.

---

### Post by YannBuntu on 2012-05-19
Hello

> **spkanu said:**
> When i was trying to update ubuntu 11.10 to ubuntu 12.04, accident the power was shut n the update process did not completed.

In such situations, system files are generally broken, so better reinstall as suggested by PhantomTurtle. See [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by spkanu on 2012-05-21
find the solution by boot repair live cd...............
thanks a lot...:p

---

