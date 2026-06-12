---
title: "Boot repair issue, dual boot"
date: 2014-07-30
forum: New to Ubuntu
---

### Post by colin24 on 2014-07-30
So I tried to boot ubuntu onto my windows 7 laptop from a usb stick, it worked and I installed ubuntu. When I tired to go back into BIOS and launch Windows 7 there was no Windows 7 on the boot list. I ran boot repair still no windows 7 on my BIOS screen. The URL from my boot repair is below. Let me know if I can supply any additional information, I am very much a novice at this. 

[http://paste.ubuntu.com/7901290/](http://paste.ubuntu.com/7901290/)

---

### Post by mastablasta on 2014-07-30
did you make a backup image of windows install?

because when installing Ubuntu your wrote over the windows 7 installation and now lost all the data there. 

if you leave it alone you might be able to recover some with photorec, but chances are slim.

good free bare metal backup software:
Redo backup - easy to use for novice users
Clonezilla - more options and more complicated to use (IMO strange kind of UI). but otherwise a very good piece of software.

---

### Post by colin24 on 2014-07-30
I did not make a backup, total noobie move. Looks like I am 100% Ubuntu now. Thank you for taking time to respond.

---

### Post by oldfred on 2014-07-30
The LVM and the encrypted with LVM are both full drive installs and have been for years. It used to only be offered with the alternative installer and it was clear then that it was full drive install.

But they did away with the alternative installer and incorporated LVM into desktop installer. But they mention that LVM is easy partitioning (which is debateable). It is easier for an advanced user and can be done on running system. But do not make it clear now that it still is a full drive install.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by CJ_Hudson on 2014-07-30
I do not know much about booting or installing from a USB stick. I do know that when running Ubuntu live from a CD rom it should not erase your Windows install. I also know that when installing Ubuntu the best way is from a CD ROM because you can choose not to erase a pre installed version of Windows. Ubuntu then mounts the Windows partition like a different drive or something and boot repair re enables boot selection after POST.
If I had the choice I would always employ the CD ROM option rather than a USB data stick because it has a proven track record of success, in my case.

---

### Post by oldfred on 2014-07-30
It actually does not matter now as both DVD and flash drive with 14.04 offer the LVM and encrypted LVM full drive install options. If user does not understand that full drive means entire physical hard drive and not the Windows 'definition' which may be a partition or may be a hard drive.

---

### Post by mastablasta on 2014-07-31
> **colin24 said:**
> I did not make a backup, total noobie move. Looks like I am 100% Ubuntu now. Thank you for taking time to respond.

ha, ha! well you now just jumped in headlong into Ubuntu. if anything does not work be sure to post and we will help. If you want windows 7 back, you need a new windows install disk or possibly your PC manufacturer might have restore disks where you would add the code you received stuck on computer. 

First thing I did when I got home with laptop was to backup the restore system partition. when preparing a dual boot I again imaged the whole disk to external drive. luckily those backups were not needed so far.

Oh and don't worry Ubuntu is a great operating system as long as all hardware works/is supported.

---

