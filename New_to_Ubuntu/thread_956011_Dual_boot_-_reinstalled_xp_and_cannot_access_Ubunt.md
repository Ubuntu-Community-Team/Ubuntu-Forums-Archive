---
title: "Dual boot - reinstalled xp and cannot access Ubuntu"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Sunshine1987 on 2008-10-22
I have a dual boot setup and I reinstalled my XP, but now do not have the GRUB boot loader.  I've tried following several tutorials to install GRUB, but I continue to either get error 22 or 17.

While using the LiveCD, when I type "sudo fdisk -l" I receive the following:

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000716a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1286    10329763+   7  HPFS/NTFS
/dev/sda2            1287       11978    85883490    5  Extended
/dev/sda3           11605       11978     3004123+  82  Linux swap / Solaris
/dev/sda5            1287       11604    82879272   83  Linux

Do I need to delete a duplicate partition?  If so, how?  I *really* need to access my Ubuntu again.  Thanks guys.

---

### Post by earthpigg on 2008-10-22
i had a very similar problem recently.

[thread here.]("http://ubuntuforums.org/showthread.php?t=954617")

in my case, i was able to boot into ubuntu so i just did that. in your case, you would have to do it from a live cd.

please ignore my embarassing moment when i told him his directions did not work (because of a typo that was my fault) lol.

---

### Post by caljohnsmith on 2008-10-23
> **Sunshine1987 said:**
> 
ubuntu@ubuntu:~$ sudo fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000716a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1286    10329763+   7  HPFS/NTFS
/dev/sda2            1287       11978    85883490    5  Extended
/dev/[COLOR="Red"]sda3[/COLOR]           11605       11978     3004123+  82  Linux swap / Solaris
/dev/sda5            1287       11604    82879272   83  Linux

Do I need to delete a duplicate partition?  If so, how?  I *really* need to access my Ubuntu again.  Thanks guys.
It unfortunately looks like a corrupted HDD partition table is the crux of your problem, because notice that sda3 is a primary partition when it is inside your extended partition sda2; therefore sda3 should be a logical partition. Also note that fdisk complains that about an empty partition #5, when sda5 is your linux partition (obviously not empty we hope). 

But the good news is there's a great program called "testdisk" that can usually fix partition table problems. :) From your Live CD, first enable all your repositories in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partition structure. :)

---

