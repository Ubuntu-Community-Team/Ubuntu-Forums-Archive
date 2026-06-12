---
title: "How do i uninstall Ubuntu and Reinstall Windows 7?"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by JKLO on 2013-07-15
Hey guys, i just got a laptop but it has ubuntu 12.1 on it. I have no idea how to uninstall ubuntu and reinstall Windows OS. 
I have the boot CD for windows and in attempting to boot it says "An error occurred while loading the archive" and doesn't run. 
No it isn't dual boot. just purely Ubuntu. 
Please help.

I don't like ubuntu and just want to get rid of it. Thanks.

---

### Post by newbie-user on 2013-07-15
Are you booting to the CD? Is the CD scratched?

---

### Post by fantab on 2013-07-15
You probably don't have a NTFS partition to install Windows to. Windows only installs to NTFS partitions and will not boot the DVD is it doesn't see a NTFS Partition.
_EDIT_: If its really a CD you are trying to install Windows from then it could be 'repair disc' and not real install disc. Because Windows 7 install files don't fit on a CD. Its always been a DVD.

You can dual boot Ubuntu and Windows 7. Its quite easy.

To Dual-Boot you have to create a NTFS partition and install Windows7 on it. Then you can run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to fix your Grub-Boot Loader. 
You can use [GParted LiveCD/USB]("http://gparted.sourceforge.net/livecd.php") to make space for Windows, create an NTFS partition and install Windows. Just remember to reformat it when installing Windows.

If you want completely remove Ubuntu then before you do that make sure you have all the necessary drivers for your Laptop hardware to run Windows7, because the manufacturer won't provide you any for Windows. Did they?

To remove Ubuntu:
Run [GParted LiveCD/USB]("http://gparted.sourceforge.net/livecd.php") and delete ALL the partitions. Then recreate Partitions as required formatted with NTFS. Reformat these partitions again with Windows Installer before you install Windows.

---

### Post by su:bhatta on 2013-07-15
It seems to be some problem with the CD ! what are you getting when you boot from the cd? 
When does it give you the message "An error occurred while loading the archive" ?

---

