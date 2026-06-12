---
title: "I used the windows installer to get Ubuntu. Which file system is it using?"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-14
I'm thinking of trying to shrink the widows part of my partition and increase the Ubuntu portion because I just accepted the 18GB default while installing. From what I understand, with the windows installer, a NTFS partition was created? 

Is there a way with either windows or Ubuntu to examine all that? It would be nice to give Ubuntu a lot more room to play with.

---

### Post by monkeybrain2012 on 2013-04-14
If you want to give Ubuntu a lot more room and allow it to run with full power don't use WUBI. Give its own partition and do a real dual boot (or install it in a spare external hard drive)

---

### Post by alhefner on 2013-04-14
Here's what disk management in windows shows me:

[IMG]http://www.afreshpath.com/images/disk_screen_shot.jpg[/IMG]

---

### Post by cwsnyder on 2013-04-14
You could re-install Ubuntu, since it presently occupies a folder under the Windows NTFS C:\ drive, installed there by WUBI.  After installing Ubuntu for dual-boot, you could then copy the /home folder from your old WUBI folder to your /home folder in the new Ubuntu partition from Ubuntu.  This would work as long as the username is the same for both installations.

---

### Post by oldfred on 2013-04-14
Wubi is just a file inside the NTFS Windows partition. It uses the Windows boot loader to boot, then shows a grub menu like a normal install and boots like a normal install. It is good for an extended test to see if you like Ubuntu, but is not for long term use. It is easy to uninstall, just like any Windows applications.

 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by alhefner on 2013-04-14
cwsnyder and oldfred, thank you! I'll get to work on that as soon as I get to an internet connection that Ubuntu can use (currently on Verizon wireless and Ubuntu don't like it) such as WiFi or ethernet wired.

Looks like I need to shrink the NTFS main partition and make one for Linux. Can I do that properly from the windows disk management or should I use some other program?

---

### Post by oldfred on 2013-04-14
Always best to use Windows disk tools to shrink the Windows NTFS partition, but only use the installer or gparted to create new Linux partitions. Windows does not see Linux partitions and often rewrites partition tables incorrectly. Windows also may convert to dynamic partitions if you try to create more than 4 and dynamic does not work with Linux. Also reboot Windows before installing Ubuntu so it can run chkdsk and make fixes it needs for its new size.

       Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by alhefner on 2013-04-14
Hmmm... I got a 1TB external... might have to repartition that one and try it that way...

---

### Post by alhefner on 2013-04-14
> **alhefner said:**
> Hmmm... I got a 1TB external... might have to repartition that one and try it that way...

Darn it all! I got all scared after I got the partition shrunk on that external. Wasn't sure of just what steps to go through in GRUB (I think it was GRUB) to get that newly freed up space properly designated and formatted... I stopped when it asked about where it should be mounted! I saw that big list of things from / to /root/ to /user/ to all sorts of stuff and backed out ...

I swear, sometimes I need more detailed instructions than a 4 bit microprocessor trying to display a character on a screen does in assembly language...

---

### Post by oldfred on 2013-04-14
Even better as then each system is totally sperate. But you have to use manual install to get the choice on where to install the grub2 boot loader. It defaults to sda with all the auto install options. And sda is usually the internal drive which you want to keep as the Windows boot loader. It can be repaired but best to install correctly.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If drive is large and connected with USB, you may need the separate /boot. Some BIOS have issues with large / (root) partitions or boot files beyond 100GB on drive. I normally suggest 25GB for root at the start of a drive, but if you already have data on drive, you may make root at end of drive. Some work ok, but some will need the small separate /boot near the beginning of the drive.

---

### Post by alhefner on 2013-04-14
You guys are fantastic! Got Ubuntu 12.10 on a few hundred gigs of my USB hard drive now! I'll mark this one solved and post my next question in a separate thread!

---

