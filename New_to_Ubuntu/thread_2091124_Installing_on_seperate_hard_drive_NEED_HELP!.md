---
title: "Installing on seperate hard drive NEED HELP!"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by elhancho on 2012-12-04
I am new to Ubuntu and I just got the LiveCD thingy to try it out on my laptop. I like it, so I decided to install it alongside Windows. But, I don't want to partition my hard drive that I have Windows on, so I got an external 250 GB USB hard drive to install ubuntu on. I have no idea how to go around doing this, because when I ran the CD and clicked on "Install", I had no idea what to do. I tried clicking on the "Something else" option and didn't know what to do. Please help!

---

### Post by rDwyP44y on 2012-12-04
You should be able to see the 250 drive if its in connected onto your computer.. just select it and partition it

or if you got a good system with lots of RAM and power, run it virtually in [VirtualBox]("https://www.virtualbox.org/")

---

### Post by oldfred on 2012-12-04
Only with the Something Else or manual install do you get the option to install grub2's boot loader to the MBR of the external drive. And you really want that.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by elhancho on 2012-12-05
> **oldfred said:**
> 
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


Yes! I followed the instructions on the website from the link you put above and now I can run Windows on one hard drive and Ubuntu on another! All I do is select which OS I want to use when I start up the computer, and it works! Thank you so much for your help!

---

### Post by elhancho on 2012-12-07
I recommend doing this if you have one of the following scenarios:

- You have a laptop and you also have a seperate external hard drive and you want to be able to dual-boot Windows and Ubuntu

- You have a small hard drive that's around 200 gb and you think it would be cool if you could carry it around and be able to boot Ubuntu (along with all of your files) on any computer you find it necessary to

- You feel like it (don't we all)

- You have all of the scenarios above (if you're crazy like me)

---

