---
title: "Windows 8 installation after Ubuntu, dual boot"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by Muez_HdD on 2014-04-29
i did 3 partitions two are ntfs and the other is ext4 witch Ubuntu 14.04 LTS is installed in.
i want to install windows 8 in an ntfs partition and a dual boot with ubuntu.
i have windows 8 in flash drive and set to install but i don't know what would goes wrong like access only to windows 8 and i can't dual boot.

                                             Plz help .

---

### Post by oldfred on 2014-04-29
Is hard drive MBR(msdos) or gpt partitioned?
Is system BIOS or UEFI?

Best to see your current partitions. from terminal
sudo parted -l

If drive is MBR, Windows will only install to a NTFS formatted primary partition with the boot flag. Or to unallocated space, but then it normally creates a hidden 100MB boot partition and the main install.

IF UEFI then Windows only installs with gpt partitioning.

---

### Post by Chris_Sanders on 2014-04-29
Are you trying to install Ubuntu before windows?

---

### Post by Muez_HdD on 2014-04-30
Yess

---

### Post by Muez_HdD on 2014-04-30
Model: ATA TOSHIBA MK7575GS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  94.0GB  94.0GB  primary   ext4            boot
 3      94.0GB  314GB   220GB   primary   ntfs
 4      314GB   746GB   432GB   primary   ntfs
 2      746GB   750GB   4238MB  extended
 5      746GB   750GB   4238MB  logical   linux-swap(v1)
 
i don't know what UEFI means but when i start the pc and press the F10 button im in Bios then .
My pc is hp pavillion g6 by the way .

---

### Post by zemega on 2014-04-30
You should read on Windows 8 actual shut down mode vs hibernate shut down as well. Because from your partioning, looks like you plan to use one partition as a data partition for both OS. In any case, it has always better to install Windows first then Ubuntu.

---

### Post by oldrocker99 on 2014-04-30
> **zemega said:**
> <snip>In any case, it has always better to install Windows first then Ubuntu.

Exactly what he said. Ubuntu plays nicely with an existing Windows installation. Windows (big shock) doesn't recognize the existence of Ubuntu (or any other GNU/Linux distro, for that matter). 

In Windows, a third party program is needed to keep Windows offering to format an ext4 partition, which Windows (dumb as it is) sees as an unformatted partition.

---

### Post by oldfred on 2014-04-30
You have a BIOS based system with MBR partitioning. Only if your hardware is new might it also be UEFI also.

Windows & Ubuntu only boot in BIOS mode from MBR partitioned drives.

I do not see a Linux formatted ext4 partition ?

Partitioning is very personal as differnent users use systems for different things. I do prefer smaller system partitions and larger data partitions for both Windows & Ubuntu. But even then Windows typically needs more system space.

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
for MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Windows fast boot or always hibernated creates all sorts of dual boot issues, best just to turn it off.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by drink1297 on 2014-04-30
> **zemega said:**
> You should read on Windows 8 actual shut down mode vs hibernate shut down as well. Because from your partioning, looks like you plan to use one partition as a data partition for both OS. In any case, it has always better to install Windows first then Ubuntu.

You can do this, you just have to be sure that you update GRUB, and use GRUB, not Windows bootloader.  It is infact the Windows Bootloader that refuses to 'play' with linux, but Grub will boot anything.

Agree with the quote, unless your experienced with unix, best to load windows first, then linux as grub will take control

---

### Post by Chris_Sanders on 2014-05-01
Well there is always the option to install grub from windows which is not optimal of what I remember. It's been a few years but I remember having to do it on XP oh say 5 years ago. Also their may be a utility to do so in Hiren's boot CD that has also saved me a few times after blowing up the MBR and partition records, yet once again I cannot remember so well been with out a working R/W drive for a few years as well and have not taken the time to put Hiren's on a CD.

---

