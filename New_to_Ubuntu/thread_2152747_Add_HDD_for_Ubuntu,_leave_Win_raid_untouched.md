---
title: "Add HDD for Ubuntu, leave Win raid untouched"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by awest5605 on 2013-06-08
[HR][/HR]I have a PC with two SATA hard drives in raid with Windows installed.  I want to throw in an additional IDE drive and install Ubuntu on it.  I would like it if I could only boot Ubuntu by selecting it using my BIOS boot menu key when starting the PC.  I don't want the Ubuntu install to mess with my current raid volume at all.  Do I just install from USB/CD like normal?  It will not install grub or mess with my raid volume or mbr at all?

---

### Post by oldfred on 2013-06-09
It is important to use Something Else or manual install and then be sure to select to install the grub2 boot loader to the MBR of the new drive not any of the existing drives. (see last png link below for typical screen).

Installer may not see RAID drives as the RAID drivers are not on the standard desktop installer. You can add them after the install.

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by awest5605 on 2013-06-09
Okay I see.  I was only worried about it messing with my raid volume, I understand now.  I'm not bothered if the raid volume isn't accessible from Ubuntu, this isn't a problem for me.

Thanks for the help, do I need to edit this topic as solved or something now?

---

### Post by oldfred on 2013-06-09
If it works then post as solved. Otherwise wait until you try it so you can add more info or clarify any issues. Then others can find thread if they have similar issues.

---

