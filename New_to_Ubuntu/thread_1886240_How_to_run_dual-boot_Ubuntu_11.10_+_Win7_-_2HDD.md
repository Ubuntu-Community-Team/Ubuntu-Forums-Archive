---
title: "How to run dual-boot Ubuntu 11.10 + Win7 - 2HDD"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by n16ht5 on 2011-11-24
Hello, I am very inexperienced with linux and would like some guidance, please.

I have a laptop with 2HDD. I have Ubuntu 11.10 x64 installed on the first drive (SDA) with the bootloader on SDA as well. I formatted a 40GB / partition, a 195GB /home partition and a 5GB swap partition. 

I left the SDB drive blank 200GB. I am planning on installing windows at a later time so that I can run left4dead and photoshop, but keeping the system dual boot. BTW, which windows should I run? I have 2000, 2003 server, XP, and 7....

Now hindsight I should have put windows on first, as I did not know that it is a pain to get dual boot to run after ubuntu is on first :confused:  (wtf?)

Now should I install windows on the second drive, then reinstall ubuntu after windows is on through wubi... or??? how should I do this? or reinstall bootloader? I have searched a lot, but the only forum threads I can find are for resizing the same windows partition and splitting it. 

I want to have my separate /home and / partitions and everything on the first hard drive, windows on the other. My scroogle-fu is lacking. I don't spend a whole lot of time on computer, mostly photo and video editing, with the occasional zombie shooting. 

thanks

Chris

---

### Post by gordie69 on 2011-11-24
I'm new to the linux myself but try looking into disk partion either in your system folder or goto software center and find a partion software that others like and download good luck there is a way but I try and help you out

---

### Post by ptrakk on 2011-11-24
just install windows.. boot up a cd(or usb) with a live ubuntu. then run 'update-grub'. if that doesn't work use the 'install-grub' command from a terminal.

---

### Post by n16ht5 on 2011-11-24
> **ptrakk said:**
> just install windows.. boot up a cd(or usb) with a live ubuntu. then run 'update-grub'. if that doesn't work use the 'install-grub' command from a terminal.


thank you!!!

---

### Post by Mark Phelps on 2011-11-24
The BEST solution is to do the following:
1) Remove the Ubuntu drive
2) Hook up the drive to contain Windows, install Win7 on that drive
3) If, when done, you don't want the OS to use the whole Windows drive, then use the Disk Management utility in Win7 to shrink the OS.  Then, create another NTFS partition in the new space.
4) shut down the PC
5) Reconnect the Ubuntu drive, but boot from this drive, not the Windows drive.
6) When inside Ubuntu, open a terminal and enter "sudo update-grub" NOTE the use of "sudo".  IF you don't enter that, it won't work.

When you reboot, you will get a GRUB menu allowing you to choose which OS you want to run.

---

### Post by fantab on 2011-11-24
> **Mark Phelps said:**
> The BEST solution is to do the following:
1) Remove the Ubuntu drive
2) Hook up the drive to contain Windows, install Win7 on that drive
3) If, when done, you don't want the OS to use the whole Windows drive, then use the Disk Management utility in Win7 to shrink the OS.  Then, create another NTFS partition in the new space.
4) shut down the PC
5) Reconnect the Ubuntu drive, but boot from this drive, not the Windows drive.
6) When inside Ubuntu, open a terminal and enter "sudo update-grub" NOTE the use of "sudo".  IF you don't enter that, it won't work.

When you reboot, you will get a GRUB menu allowing you to choose which OS you want to run.

Few more suggestions when Dual Booting with Windows with two HDD in the system.

[LIST]
[*]Always **Install Windows First to the First Partition of the First HDD** ie, /dev/sda1, and that this should be a Primary Partition. Otherwise Widows may have issues. Windows works best when installed to first partition of the first HDD. Be safe than sorry.
[/LIST]


[LIST]
[*]Since there are Two HDD - I suggest you **install Ubuntu and Grub to Second HDD** or /dev/sdb, this way you get to keep the Windows MBR. Just change the Hard Disk Boot Order in BIOS to boot /dev/sdb or your Second HDD First. This enables Grub to Load First. Also if Grub gets corrupted or goes missing you can still boot to Windows by changing the HDD Boot Order in BIOS back to boot /dev/sda.
[/LIST]
If you have an option to reinstall UBUNTU then please do so after installing Windows. If There is an option then I suggest you organize your partitions accordingly with [**GPARTED LiveCD **]("http://gparted.sourceforge.net/livecd.php")before you do your installs**.**[]("http://gparted.sourceforge.net/livecd.php")


Remember Linux can read and write NTFS partitions but Windows can do neither to Linux Partitions. Plan ahead.


Good Luck.
[]("http://gparted.sourceforge.net/livecd.php")

---

### Post by oldfred on 2011-11-24
We have seen users with a Windows install on sdb, but with Windows 7 it installed its (hidden) boot/repair partition on sda. Users then have overwritten that boot partition when installing Ubuntu and wondered why Windows stopped working.

I believe Windows does sense which drive is set at the boot drive in BIOS. So set BIOS to boot from sdb before installing Windows.

If you can easily disconnect the Ubuntu drive that is the best choice for Windows 7. The older versions of Windows are like older versions of Ubuntu and have hard coded drive  numbers - like in XP's boot.ini for instance. So drive order is important or else you have to edit a few files to get Windows to work.

---

