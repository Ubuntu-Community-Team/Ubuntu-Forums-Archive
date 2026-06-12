---
title: "Failed upgrade from 12.04 to 14.04"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by stm146 on 2014-08-21
For the last 2 years I've been running a dual boot config with XP and 12.04LTS. After being prompted several times to upgrade to 14.04LTS I backed up my data and started the upgrade. It took several hours (I let it run overnight so not sure how long it actually took). When I rebooted I got an "initramfs" terminal instead of the Unity gui. When I booted again I got an Ubuntu screen with the message: "Serious errors were found while checking the disk drive for /." When I reboot in diagnostic mode the last few lines displayed are:
mount: mounting /dev/loop0 on /root failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg.

When I boot 14.04 with the 3.2.0-67 linux kernel I get to the Unity gui, but the system's unstable and locks up. Usually the cursor will still move but I can't click on anything. Sometimes this happens as I'm entering my password and other times up to 40 minutes after booting.

I'd be grateful for any advice on how to get 14.04 running with the 3.13.0-34 linux kernel.

---

### Post by nerdtron on 2014-08-21
Since you already backed-up your data, why not reinstall Ubuntu. Upgrades from one version to another are usually hit-or-miss.

---

### Post by Jonathan Precise on 2014-08-21
Looks like you're running WUBI (Ubuntu inside Windows), which is no longer supported. I'd advise backing up all data (in XP and Ubuntu) using the Clonezilla Backup System. Then delete the WUBI program from Windows XP. Insert a freshly-burned Ubuntu DVD (verify that the SHA256 sums match). Boot from the DVD. (check that the BIOS is set to boot from the DVD first). Hit install ubuntu. Partition it up. Follow all the instructions. Reboot. Enjoy a working Ubuntu!

**If you did not make a backup:** hope everything comes out good.

**If everything goes wrong:** restore from backup.

**If you did not make a backup and everything goes wrong:  [SIZE=3]PANIC![/SIZE]**

---

### Post by Jonathan Precise on 2014-08-21
> **nerdtron said:**
> Since you already backed-up your data, why not reinstall Ubuntu. Upgrades from one version to another are usually hit-or-miss.

The reason it didn't work is that he is using WUBI.

> ...
**mount: mounting /dev/loop0 on /root failed: invalid argument**
...

means he/she is on a CDROM or WUBI (in the CDROM you can't upgrade the release, so he/she is using WUBI)

---

### Post by hakuna_matata on 2014-08-23
> **stm146 said:**
> "Serious errors were found while checking the disk drive for /."
Try this: [http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)
but add **gksudo: **[http://ubuntuforums.org/showthread.php?t=2217829&p=13035996#post13035996](http://ubuntuforums.org/showthread.php?t=2217829&p=13035996#post13035996)

---

### Post by stm146 on 2014-08-26
Thanks Jonathan Precise -  I was in fact using WUBI though I'd forgotten this since installing 12.04 2 years ago and didn't know it's no longer supported. I backed up XP data and tried a fresh 14.04 install from USB but hit some graphics problems so I've now installed 14.04 on another machine instead. I might raise the graphics issue separately but will now close the original 14.04 install issue.

---

