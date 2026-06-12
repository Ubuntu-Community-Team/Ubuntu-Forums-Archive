---
title: "Can't get past grub rescue after installing lubuntu 14.04"
date: 2014-10-19
forum: New to Ubuntu
---

### Post by James_Frayne on 2014-10-19
I am new to linux and have been trying to dual boot linux and Windows XP on an old Pentium 4 PC. I had managed this with fedora but fedora did not run well on the PC perhaps due to the low specification so I decided to try lubuntu instead.

I installed lubuntu 14.04 from a live usb after deleting the partition with fedora on it. The install completed successfully but when I rebooted I got stuck at the grub rescue prompt.

I did some research and booted boot repair from a live CD. This ran successfully but when I rebooted I was back at the grub rescue prompt. The info from boot repair is here: [http://paste.ubuntu.com/8589235/](http://paste.ubuntu.com/8589235/).

I think I must have deleted something I shouldn't when I was fiddling with the partitions before installing lubuntu. I would be grateful for any suggestions on how to fix this.

James

---

### Post by yancek on 2014-10-19
You have Lubuntu installed on sdb5 which is the second hard drive (sdb) and have Grub in the master boot record.  Also, all the files seem to be where they should be and your grub.cfg file has correct menentries for Lubuntu as well as xp.  Did you do as suggested in the last line of the bootrepair output and set the computer to boot from the second drive, sdb which is the 160GB drive?  Watch the screen on boot for the key to "enter setup".

You also have Grub installed on the master boot record of sda, the drive on which you have only one partition which is windows.  Not sure why you did that or if that was from a previous install?

---

### Post by James_Frayne on 2014-10-19
Yes I did set the computer to boot from sdb. I don't know why Grub is on sda as well as sdb.

When I try to boot I get error: no such partition entering rescue mode grub rescue>

---

### Post by oldfred on 2014-10-19
Your system may be old enough to have the far from start of drive issue.
You show some of your boot files at 146GB and some old BIOS in IDE mode will not boot from a file beyond 137GB.
Better to have /boot or smaller / (root) fully within the first 100GB of drive.

Better to install to sdb with / root) of 20 or 25GB and use rest of drive as /home and swap. 

Boot-Repair did its auto fix of installing grub to both drives. Suggest using advanced mode on only install grub to same drive as Ubuntu and set BIOS to boot that drive as default.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by James_Frayne on 2014-10-20
I have run boot-repair and selected the option to only install grub on sdb. Boot-repair completed but with an error about enabling access to respositories.

I rebooted and get a boot menu now but the only option is Windows XP. This boots successfully. Do I just need to reinstall lubuntu now partioning sdb as suggested above.

Thanks

James

---

### Post by oldfred on 2014-10-20
If no data to save or you have good backups, then re-install may be easiest.

I do prefer to partition in advance with gparted, but you can just use installer. Gparted always seemed a bit easier. But either way you have to use Something Else to specify more than the standard / & swap and standard install of grub boot loader to MBR of sda.

---

### Post by James_Frayne on 2014-10-21
I re-installed partitioning as you suggested and now works perfectly. Can now boot lubuntu and XP.

Many thanks,

James

---

