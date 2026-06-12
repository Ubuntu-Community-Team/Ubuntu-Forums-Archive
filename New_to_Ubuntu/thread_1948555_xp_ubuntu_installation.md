---
title: "xp ubuntu installation"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by gil1 on 2012-03-28
Hi,
I installed ubuntu in a partition on a computer that is allready running xp. the installation was from a disc and i followed the instruction one by one.
after I installed ubuntu 11.04 I restarted the computer hopping to start working with ubuntu, but my computer wont show any menu to select this option and just go on running xp without asking me.
what should i do?:mad:

---

### Post by sudodus on 2012-03-28
Welcome to the Ubuntu Forums :-)

Please describe your computer: cpu, ram, graphics driver

And run the following commands in a terminal window
```
sudo fdisk -lu
```
and
```
df
```
and post the output (cut and paste into a new post).

---

### Post by gil1 on 2012-03-28
the computer pentium  4 cpu  2.8 GHZ
1 GB RAM

I tried the command line and i got an error that the file cant be found. (im translating the windwos in hebrew)

---

### Post by gil1 on 2012-03-28
sorry i missunderstood.
thats the result:

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\user>sudo fdisk -lu
'sudo' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\user>df
'df' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\user>

---

### Post by sudodus on 2012-03-28
Sorry, I did not explain clearly what I meant. Please boot from the Ubuntu install drive, select ***test*** (which means that you run a live session instead of installing). And when you have that system running, then get a terminal window and run those two commands. You get the terminal window with
***ctrl + alt + t***

---

### Post by gil1 on 2012-03-28
Im pushing ctrl+alt+t but im not getting any termiinal window

---

### Post by gil1 on 2012-03-28
ok, I figured it out.
this is the result:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa21ba21b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    80485649    40242793+   7  HPFS/NTFS/exFAT
/dev/sda2        80485711   160086015    39800152+   f  W95 Ext'd (LBA)
/dev/sda5        80485713   138641604    29077946    7  HPFS/NTFS/exFAT
/dev/sda6       138643456   158007295     9681920   83  Linux
/dev/sda7       158009344   160086015     1038336   82  Linux swap / Solaris
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/cow                    508556     79832    428724  16% /
udev                    501168         4    501164   1% /dev
tmpfs                   203424       752    202672   1% /run
/dev/sr0                711980    711980         0 100% /cdrom
/dev/loop0              683136    683136         0 100% /rofs
tmpfs                   508556         8    508548   1% /tmp
none                      5120         4      5116   1% /run/lock
none                    508556       116    508440   1% /run/shm
ubuntu@ubuntu:~$

---

### Post by gil1 on 2012-03-28
whtas now?

---

### Post by sudodus on 2012-03-28
> ```
 ubuntu@ubuntu:~$ sudo fdisk -lu
 
 Disk /dev/sda: 82.0 GB, 81964302336 bytes
 255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
 Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0xa21ba21b
 
 Device Boot Start End Blocks Id System
 /dev/sda1 * 63 80485649 40242793+ 7 HPFS/NTFS/exFAT
 /dev/sda2 80485711 160086015 39800152+ f W95 Ext'd (LBA)
 /dev/sda5 80485713 138641604 29077946 7 HPFS/NTFS/exFAT
 /dev/sda6 138643456 158007295 9681920 83 Linux
 /dev/sda7 158009344 160086015 1038336 82 Linux swap / Solaris
 ubuntu@ubuntu:~$
```
Your Ubuntu system is (probably) installed into the partition [FONT="Courier New"][SIZE="3"]/dev/sda6[/SIZE][/FONT]

I think one reason for your problem is that you did not install grub into the beginning of the drive /dev/sda, but that you instead installed it into the partition /dev/sda6, where it is idle, while the Windows bootloader is untouched.

If my guess is correct, you can solve the problem via two routes.

1. Reinstall grub according to this link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275") particularly chapter 13. Reinstalling GRUB2 from the live CD

2. Reinstall the whole Ubuntu operating system (to the same partition as before (selecting 'something else' when asked where and how to install it). And this time be sure to install grub to /dev/sda.

---

