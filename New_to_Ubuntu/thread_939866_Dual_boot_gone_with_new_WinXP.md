---
title: "Dual boot gone with new WinXP"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by lookout4lpe on 2008-10-06
Dual boot gone with new WinXP
=============================

My new install of WinXP took out the dual boot I had going to Ubuntu 8.04.  I decided to try the Auto SuperGrubDisk.  I ran the program and completed to the first reboot.  The new boot menu showed windows xp and Super GRUB Disk.  Selecting SGD the following was presented:

===========================================================

Booting 'GRUB => MBR & !LINUX! (1)      AUTO      ;-)'

find /grub/stage1 /boot/grub/stage1
root (hd0,8)
 Filesystem type is ext2fs, partition type 0x83
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)" ... _

==========================================================
Last cursor position is blinking.

It allows no entry, "enter" is not accepted, and "Ctrl-Alt-Delete" will not cause a reboot.  I can restart in WinXP.  

I continued to search for a solution since I could not get the Auto-SGD to run.  I loaded a Ubuntu LiveCD to get to the terminal.  I first looked into setting up grub.

=============================================================
grub> find /boot/grub/stage1
 (hd0,8)
grub> root (hd0,8)
grub> Setup (hd0,8)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage5" exists... yes
 Running "embed /boot/grub/e2fs_stage5 (hd0,8)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage5 (hd0,8)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,8) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested
grub>
============================================================

At a loss for a next step, I learned how to get a partition list.

===========================================================
fdisk l
omitting empty partition (5)

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units - cylinders of 16065 * 512 = 8225280 bytes
Device	Boot	Start	End	Blocks	Id	System
/dev/sda1  *	1	10171	81698526  7	HPFS/NTFS
/dev/sda2	10172	10426	2048287+ 83	Linux
/dev/sda3	10427	20342	79650270  5	Extended
/dev/sda4	19966	20342	3028221	 82	Linux swap/Solaris
/dev/sda5	10427	10725	2401654+ 83	Linux
/dev/sda6	10726	10980	2048256	 83	Linux
/dev/sda7	10981	13096	16996738+83	Linux
/dev/sda8  *	13097	15313	17808021 83	Linux
/dev/sda9	15314	15426	827316	 82	Linux swap/Solaris
/dev/sda10	15417	19772	34989538+83	Linux
/dev/sda11	19773	19965	1550241	 82	Linux swap/Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units - cylinders of 16065 * 512 = 8225280 bytes
Device	Boot	Start	End	Blocks	Id	System
/dev/sdb1  	1	 3648	29302528+ 7	HPFS/NTFS
/dev/sdb2	3649	36483	263747137+7	W95 Ext'd (LBA)
/dev/sdb5	3649	 7296	29302528+ 7	HPFS/NTFS
/dev/sdb6	7297	10944	29302528+ 7	HPFS/NTFS
/dev/sdb7	10945	14592	29302528+ 7	HPFS/NTFS
/dev/sdb8  	14593	18240	29302528+ 7	HPFS/NTFS
/dev/sdb9	18241	36483	146536866 7	HPFS/NTFS
===========================================================

This information doesn't do much for me.  I hope someone will be able to help.  

I look forward to getting this "bump" behind me.  Thanks for your help.

---

### Post by shifty_powers on 2008-10-06
[how to restore grub with an ubuntu live cd](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

---

### Post by Troll_the_Great on 2008-10-06
Try this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)
I had the same problem and it worked for me.
Cheers!

---

### Post by lookout4lpe on 2008-10-06
Just to confirm.  After I get LiveCD running ubuntu, the following commands:

Applications --> Accessories --> Terminal

(Then from above my installation partition is "sda8")

cd/

sudo -s -H

mount -t ext3 /dev/sda8 /mnt

Mount -t proc /mnt/proc

mount -t sysfs sys /mnt/sys

mount -o bind /dev /mnt/dev

chroot /mnt /bin/bash

grub-install /dev/sda

If my read is correct, I will proceed.  Thanks.

---

### Post by shifty_powers on 2008-10-06
```
  cd /
  
 
  sudo -s -H

  mount -t ext3 /dev/sda8 /mnt

  mount -t proc proc /mnt/proc

  mount -t sysfs sys /mnt/sys

  mount -o bind /dev /mnt/dev

  chroot /mnt  /bin/bash
```

is what you want, nearly right :D

---

### Post by glotz on 2008-10-06
If you don't want the smilies in your post, you need to disable them. Click edit > go advanced and scroll down to disable smilies.

---

### Post by caljohnsmith on 2008-10-06
There's actually no need to go through all the trouble of mounting all those system directories and running the grub-install command since you all ready have all your Grub files in place in your /boot/grub directory; it could work, but it's an overkill. :) Just do the following from your Live CD:
```
sudo grub
grub> root (hd0,8)
grub> setup (hd0)
grub> quit
```
In other words, you had it right before except you need to run "setup (hd0)" to install Grub to the MBR (Master Boot Record) instead of (hd0,8 ), which will install Grub to the boot sector of sda9 or (hd0,8 ). Let me know how it goes.

---

### Post by lookout4lpe on 2008-10-06
Shifty_powers, I tried 3 times, no go.
caljohnsmith, I tried the direct way twice and no go.  The response was error 12 - invalid device requested.  Thanks for the suggestions, is there any where else to go?

---

### Post by caljohnsmith on 2008-10-06
Yes, I've seen Grub give an error like that while installing with the "root" and "setup" commands when there was a problem with the HDD's partition table. I think it would definitely be worth checking your HDD's partition table in case that is the issue. Post the output of:
```
sudo fdisk -l
```
Then enable all your repositories in System > Prefs > Software Sources, and download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we'll work from there. :)

---

### Post by lookout4lpe on 2008-10-06
Ran fdisk and the results were the same as shown in post #1.  testdisk would not run.  Response was ... could not open lock file... unable to lock file... and are you root?  Is there a password on a liveCD run?

---

### Post by caljohnsmith on 2008-10-06
> **lookout4lpe said:**
> Ran fdisk and the results were the same as shown in post #1.  testdisk would not run.  Response was ... could not open lock file... unable to lock file... and are you root?  Is there a password on a liveCD run?
That "could not open lock file" error, did you get that after doing the apt-get command or the testdisk command? If you get it with apt-get, it means you've got Synaptic or some other package manager open, so you need to close them before using apt-get. Can you post exactly what happens when you run those two commands?

---

### Post by lookout4lpe on 2008-10-06
Iam running from liveCD, if that inclides Synaptic I need to know how to close.  The result of testdisk run was:

sudo apt-get install testdisk
reading package lists ... done
building dependency tree
reading state information ... done
E: couldn't find package testdisk
sudo testdisk
sudo: testdisk: command not found

This is different from the last try.  The variable results concern me.  Am I entering the sudo commands correctly?  Am I in the right directory/file?  Let me know what's next.  I'll stick with you.

---

### Post by caljohnsmith on 2008-10-06
Do you have an internet connection when you run the Live CD? You'll need that to download the testdisk package. If you do have an internet connection while using the Live CD, try downloading the testdisk package from packages.ubuntu.com to your Ubuntu desktop, and then do:
```
sudo dpkg -i ~/Desktop/test*.deb
sudo testdisk
```
Or if you don't have an internet connection, you could download the [SystemRescueCD]("http://www.sysresccd.org/") from another computer and use that since it all ready has testdisk included. Let me know how that goes.

---

### Post by egalvan on 2008-10-06
Parted Magic liveCD includes TestDisk.

Try it instead of Ubuntu LiveCD.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It's a fairly small download.

I prefer PartedMagic to any other.

I like it so I donated to the authors.

ErnestG

---

### Post by lookout4lpe on 2008-10-07
I have internet connection with liveCD.

I could not find testdisk at package.ubuntu.com for download.

I downloaded rescue disk from CGSecurity that contained testdisk.

Copied testdisk file to desktop.

Ran the sudo commands and the reply was file not found.

Downloaded SystemRescueCD but could not find testdisk file.

Looked briefly at Parted and found no comment about testdisk.  Would have to download files to confirm testdisk is available and can be found once copied to desktop.

---

### Post by caljohnsmith on 2008-10-07
Well I don't have that SystemRescueCD around at the moment to help you use it, so how about from your Live CD, just click one of the following links to download testdisk:
[LIST]
[*][testdisk for 64-bit]("http://mirrors.cs.wmich.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.8-1_amd64.deb")
[*][testdisk for 32-bit (i386)]("http://mirrors.cs.wmich.edu/ubuntu/pool/universe/t/testdisk/testdisk_6.8-1_i386.deb")
[/LIST]
Be sure to save it to your desktop, and then follow the steps from post #13.

---

### Post by lookout4lpe on 2008-10-08
I downloaded i386 version to the desktop and found it on the file list.
The following commands were run at the Terminal:
============
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo dpkg -i ~/desktop/test*.deb
dpkg: error processing /home/ubuntu/desktop/test*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ubuntu/desktop/test*.deb
ubuntu@ubuntu:~$ sudo dpkg -i ~/desktop/testdisk_6.8-1_i386.deb
dpkg: error processing /home/ubuntu/desktop/testdisk_6.8-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ubuntu/desktop/testdisk_6.8-1_i386.deb
ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ ls /desktop
ls: cannot access /desktop: No such file or directory
ubuntu@ubuntu:~$ ls /ubuntu/desktop
ls: cannot access /ubuntu/desktop: No such file or directory
ubuntu@ubuntu:~$ 
=======================
I do have the file on the desktop.  Notice that I tried the full file name and also the full path.  Something isn't working.

---

### Post by caljohnsmith on 2008-10-08
When you type those commands in the terminal, they are case-sensitive, so you need to make sure you get them exactly right. You have to use a capital "D" when accessing the desktop directory:
```
sudo dpkg -i ~/[COLOR="Red"]D[/COLOR]esktop/test*.deb
```
Give it another shot and let me know how it goes. :)

---

### Post by lookout4lpe on 2008-10-08
I am learning fast!  This is the output of the processes in post 9 to 13:
===================================
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf18bf18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10171    81698526    7  HPFS/NTFS
/dev/sda2           10172       10426     2048287+  83  Linux
/dev/sda3           10427       20342    79650270    5  Extended
/dev/sda4           19966       20342     3028221   82  Linux swap / Solaris
/dev/sda5           10427       10725     2401654+  83  Linux
/dev/sda6           10726       10980     2048256   83  Linux
/dev/sda7           10981       13096    16996738+  83  Linux
/dev/sda8   *       13097       15313    17808021   83  Linux
/dev/sda9           15314       15416      827316   82  Linux swap / Solaris
/dev/sda10          15417       19772    34989538+  83  Linux
/dev/sda11          19773       19965     1550241   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x244ae8cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29302528+   7  HPFS/NTFS
/dev/sdb2            3649       36483   263747137+   f  W95 Ext'd (LBA)
/dev/sdb5            3649        7296    29302528+   7  HPFS/NTFS
/dev/sdb6            7297       10944    29302528+   7  HPFS/NTFS
/dev/sdb7           10945       14592    29302528+   7  HPFS/NTFS
/dev/sdb8           14593       18240    29302528+   7  HPFS/NTFS
/dev/sdb9           18241       36483   146536866    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found
ubuntu@ubuntu:~$ sudo dpkg -i ~/Desktop/test*.deb
Selecting previously deselected package testdisk.
(Reading database ... 98423 files and directories currently installed.)
Unpacking testdisk (from .../testdisk_6.8-1_i386.deb) ...
Setting up testdisk (6.8-1) ...
ubuntu@ubuntu:~$ sudo testdisk
TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
TestDisk exited normally.
ubuntu@ubuntu:~$ 
======================================

I have attached the testdisk output in file testdisk.doc.  Since I didn't know what I was looking for, I selected options that appeared safe and non-destructive.

I hope this tells you something.  Thanks, Len

---

### Post by caljohnsmith on 2008-10-08
Unfortunately your partition table for sda has multiple problems according to testdisk, so that would explain why you can't reinstall Grub to the MBR of sda. You have many, many linux partitions on sda; do you know what they all are? Also, you have three swap partitions, when you only need to have one since different distros can share the same swap partition. Was your original intention to have just Hardy and Windows dual-boot on that drive? 

Both your Hardy and XP installations are relatively new, is that correct? If that is true, I would recommend backing up your important files in Hardy and Win XP, wipe the drive clean, and start again fresh. First use Ubuntu's partition editor to make your partitions, then install Windows XP, and then install Ubuntu. 

Let me know if you want to start fresh on that drive, and I can help guide you through it if you like.

---

### Post by lookout4lpe on 2008-10-08
Yes, I would like to have help getting this all cleaned up. Can I just redo sda, the first hard disk?  Can I use the second hard disk to backup the files I need to keep?  I think that (backup) would be the first step.  Then I would set the first hard disk for WinXP and Ubuntu and their application programs and keep all data on the second hard disk.  Would appreciate your thoughts on the best order of steps that need to be taken.  Thanks, Len

---

### Post by caljohnsmith on 2008-10-08
> **lookout4lpe said:**
> Yes, I would like to have help getting this all cleaned up. Can I just redo sda, the first hard disk?  Can I use the second hard disk to backup the files I need to keep?  I think that (backup) would be the first step.  Then I would set the first hard disk for WinXP and Ubuntu and their application programs and keep all data on the second hard disk.  Would appreciate your thoughts on the best order of steps that need to be taken.  Thanks, Len
Yes, definitely do your backup first, and you could use your second sdb drive to store your files. Once you are sure that everything important is saved to your second sdb drive, I would disconnect it so there is no possibility of anything accidentally happening to it during your reinstallation of Windows and Ubuntu. 

Once sdb is disconnected, I would boot your Live CD, open a terminal, and do:
```
gksudo gparted
```
That will bring up Ubuntu's partition editor gparted. Click on all your partitions and mark them for deletion so you have a completely clean HDD to work with. Then set up three primary partitions: Ubuntu at the beginning of the disk, followed by a small swap partition, followed by the Windows partition which can use the rest of the disk. How much room you want to give Ubuntu and Windows is up to you. It's important to put Ubuntu at the beginning though so that you won't later have Grub problems related to BIOS limitations. 

Once you get the partitions set up, install Win XP, and after that install Ubuntu. Let me know if you run into problems.

---

### Post by lookout4lpe on 2008-10-08
I will check back with you.  Thanks for your tenacity, Len

---

### Post by egalvan on 2008-10-09
> **lookout4lpe said:**
> Downloaded SystemRescueCD but could not find testdisk file.

Looked briefly at Parted and found no comment about testdisk.  Would have to download files to confirm testdisk is available and can be found once copied to desktop.

> **lookout4lpe said:**
> Yes, I would like to have help getting this all cleaned up. Can I just redo sda, the first hard disk?  Can I use the second hard disk to backup the files I need to keep?  I think that (backup) would be the first step.  Then I would set the first hard disk for WinXP and Ubuntu and their application programs and keep all data on the second hard disk.  Would appreciate your thoughts on the best order of steps that need to be taken.  Thanks, Len

You probably have most of this sorted out already, but here is some more info...

This is the list of programs available on PartedMagic LiveCD...

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Programs](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Programs)

Testdisk is listed, third from bottom, under Console Utilities.

PartedMagic is a very small download, well worth the time.

As I've stated before, I have found PartedMagic to be easier to use when testing, partitioning and formatting drives.
 This from a relative newcomer's view of Linux.
So much so that it's the only one I use now, and I sent a donation to the authors.

Also, I use that exact same setup you describe...

One drive to dual-boot XP and Hardy, and a second to hold data (including audio, video, downloads & programs).
 It's big enough (750g) that I use it to hold back-up's of my /home directory with no problem.
And it's formatted ext3, and I use "Ext2 Installable File System for Windows" to access...

[http://www.fs-driver.org/](http://www.fs-driver.org/)

And caljohnsmith is the GRUB-MEISTER for fixing boot problems under Linux! If he's in your corner, you can be sure you'll be running right in no time.

ErnestG

---

### Post by lookout4lpe on 2008-10-09
Thanks egalvan.  I will review your input as I sort out my rebuild plan.

---

