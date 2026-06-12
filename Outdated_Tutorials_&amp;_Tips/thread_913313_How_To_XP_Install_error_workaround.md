---
title: "How To: XP Install error workaround"
date: 2008-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by SkonesMickLoud on 2008-09-07
If you've ever attempted to dual boot XP and Ubuntu/any Linux flavor/s, you may have run into what I have found to be a somewhat common occurrence.

An XP installation is broken into two main parts.  For the first part, you boot your computer from the XP disk, and allow it to copy it's files to the specified partition.  Then, your system reboots to the said partition and the actual installation begins.

This is where the problem may arise.  I obviously can't speak for every system, but the majority of the times I have setup a dual boot, I successfully booted to the CD and copied, then rebooted into grub with no option to boot into the XP install.  I've found that for some reason, a second reboot here requires you to start the XP install over.

Below is a workaround that I have found to be successful each time I tried it:

First, from within your current Ubuntu install or a live CD, backup and edit your menu.lst:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst~
## sudo cp /boot/grub/menu.lst /target/usb/flash/drive ## Not necessary, but I like a little CYA. ##
sudo nano -w /boot/grub/menu.lst

```Delete all entries to the menu.lst, adding (or leaving) the entry for XP.  If you're leery of deleting stuff, you could simply comment out all other OS entries.  Either way, make a backup or two.

```

title        Windows 95/98/NT/2000/XP
root        (hdx,y)
makeactive
chainloader    +1

```Activate "hiddenmenu" and set "timeout 0".  Save and quit.  Reboot.

Set your BIOS to boot from CD and install XP.  Upon the first reboot, should GRUB somehow load, the only choice it will have will be to go to the XP partition, so the installation should continue as normal.

Once the installation is complete, you should boot into XP to verify the install worked.  If it did you will need to reinstall GRUB to the MBR and restore your old menu.lst, allowing you to dual/multi-boot.  I personally prefer a Puppy Linux disk, but SuperGrubDisk, Ubuntu Live or any other flavor distro will work just fine.  An excellent HowTo on installing GRUB from a Ubuntu LiveCD can be found [HERE]("http://ubuntuforums.org/showthread.php?t=224351").  Mount the necessary drives/partitions, copy the backup and verify:

```

cp /boot/grub/menu.lst~ /boot/grub/menu.lst
cat /boot/grub/menu.lst

```To be safe, I generally attempt to boot to each flavor I have, just to be sure everythig went well.

Enjoy your dual/multi-boot!

---

