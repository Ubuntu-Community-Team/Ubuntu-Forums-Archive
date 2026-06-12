---
title: "Help with resizing my ubuntu partition"
date: 2018-08-12
forum: New to Ubuntu
---

### Post by shunk2 on 2018-08-12
I recently installed ubuntu on my computer, I'm having trouble resizing the partition that ubuntu runs off of, I installed GParted and I don't know what to do from here, I want to move all of my available space to ubuntu. I am dual booting windows, would be great if I could completely remove it. Here's a screenshot of GParted. (I'm a bit of a newbie to anything linux related so give me a break xd)

---

### Post by deadflowr on 2018-08-12
Look like a wubi install
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")
[https://ubuntuforums.org/showthread.php?t=2229766]("https://ubuntuforums.org/showthread.php?t=2229766")
given that, I would think it's easier to start over and do a proper dual-boot setup.
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
wubi doesn't create partitions, but rather it creates disk files that act a lot like virtual disks, or much like what you would use for virtual machines such as virtualbox or vmware.
Which is why you don't see any linux partitions in gparted.
And the /host is typical of how Ubuntu would show in gparted in a wubi install.

Just some rambling thoughts

---

### Post by shunk2 on 2018-08-12
> **deadflowr said:**
> Look like a wubi install
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://ubuntuforums.org/showthread.php?t=2229766](https://ubuntuforums.org/showthread.php?t=2229766)
given that, I would think it's easier to start over and do a proper dual-boot setup.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
wubi doesn't create partitions, but rather it creates disk files that act a lot like virtual disks, or much like what you would use for virtual machines such as virtualbox or vmware.
Which is why you don't see any linux partitions in gparted.
And the /host is typical of how Ubuntu would show in gparted in a wubi install.

Just some rambling thoughts
Okay, is there anyway to get rid of windows and just keep ubuntu instead of getting rid of ubuntu to start over?

---

### Post by deadflowr on 2018-08-12
> **shunk2 said:**
> Okay, is there anyway to get rid of windows and just keep ubuntu instead of getting rid of ubuntu to start over?

Download Ubuntu and make a usb or dvd to create a bootable installer.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0")
[https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows#0]("https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows#0")
(And I'm sure others can chime in with better how-tos in regards to getting a working bootable media going)

Once you create the bootable media, run it and you'll have an option to install Ubuntu.
At one point during the install (early) you'll be asked to select how it will be installed and offer an option to wipe everything and install it over the full hard drive.
Doing that will wipe Windows out.


In the current setup, there is no way to remove windows and keep Ubuntu as Ubuntu requires there be a windows as the current setup you have is more akin to running Ubuntu as an app for windows than a separate and independent installation.

EDIT:
I guess there is at least one rather convoluted way to migrate a wubi install to a partition: [https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")
Which through that method (if it even works anymore) you could in theory move Ubuntu to it's own partition and then resize windows or even wipe out all of Windows partitions.
The caveat to doing this is that it is not well tested beyond older versions of Ubuntu and may or may not work as suggested.

IMO, it's far easier to wipe out everything and start totally fresh with a clean install.

---

### Post by shunk2 on 2018-08-12
> **deadflowr said:**
> Download Ubuntu and make a usb or dvd to create a bootable installer.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)
[https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-burn-a-dvd-on-windows#0)
(And I'm sure others can chime in with better how-tos in regards to getting a working bootable media going)

Once you create the bootable media, run it and you'll have an option to install Ubuntu.
At one point during the install (early) you'll be asked to select how it will be installed and offer an option to wipe everything and install it over the full hard drive.
Doing that will wipe Windows out.


In the current setup, there is no way to remove windows and keep Ubuntu as Ubuntu requires there be a windows as the current setup you have is more akin to running Ubuntu as an app for windows than a separate and independent installation.

EDIT:
I guess there is at least one rather convoluted way to migrate a wubi install to a partition: [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
Which through that method (if it even works anymore) you could in theory move Ubuntu to it's own partition and then resize windows or even wipe out all of Windows partitions.
The caveat to doing this is that it is not well tested beyond older versions of Ubuntu and may or may not work as suggested.

IMO, it's far easier to wipe out everything and start totally fresh with a clean install.
Okay, I'm going to try the migratewubi thing, but I don't have a swap partition, I don't know how to do that through gparted, could you explain how to make MigrateWubi work through the current state of what my partitions look like?

---

### Post by kurt18947 on 2018-08-12
No harm in trying migratewubi but don't be surprised if you end up re-installing from scratch. Even Ubuntu sanctioned upgrades often have issues that warrant re-installs. Do you have a lot of customizations in your current Wubi install? I just installed Xubuntu 18.04 on a midrange SSD, took less than 10 minutes. The customizations will take much longer.

---

### Post by shunk2 on 2018-08-12
I understand my current problem now, I used wubi to install ubuntu and that made it so it only gives ubuntu up to 32gb of hard drive space (or whatever, something like that should be right) so I hit the maximum amount I can use on ubuntu, so I wasn't able to do anymore things that I've done. I need to wipe the drive and install ubuntu without using wubi, instead an sd card, cd, or flash drive, right?

---

### Post by yancek on 2018-08-12
The reason you can't resize the Ubuntu partition is because there is none.  The image you posted shows only windows partitions.  How Wubi works is explained in the WubiGuid link posted above.  If you want to get rid of windows and only use Ubuntu then yes,  a full install to that or another drive would be what you should do.  Obviously, if you have any personal data on either the Wubi Ubuntu or windows, you would need to back that up to another drive first or it will all be lost.

You can use the links posted above to make a bootable DVD/flash drive.  Before installing, I would recommend you test boot the DVD or flash drive and try using it for a brief time to see if there are any problems.  If so, make sure to keep notes of exactly what problems you have (if any).

---

### Post by shunk2 on 2018-08-12
> **yancek said:**
> The reason you can't resize the Ubuntu partition is because there is none.  The image you posted shows only windows partitions.  How Wubi works is explained in the WubiGuid link posted above.  If you want to get rid of windows and only use Ubuntu then yes,  a full install to that or another drive would be what you should do.  Obviously, if you have any personal data on either the Wubi Ubuntu or windows, you would need to back that up to another drive first or it will all be lost.

You can use the links posted above to make a bootable DVD/flash drive.  Before installing, I would recommend you test boot the DVD or flash drive and try using it for a brief time to see if there are any problems.  If so, make sure to keep notes of exactly what problems you have (if any).
Yeah, after a bit I noticed that, but I don't seem to have a cd or a usb drive :/

---

