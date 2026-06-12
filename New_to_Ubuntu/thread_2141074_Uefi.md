---
title: "Uefi"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by Arachnaphobe on 2013-05-01
I've been building a new PC and wanted to put Linux straight on it, had a 3tb hard drive, installed Ubuntu 13.04, rebooted "Verifying DMI Pool Data..."
I tracked down the problem to my motherboard automatically making a GPT partition on a drive over 2.2tb. 
Using another machine with Ubuntu 13.04, when I try to format it into more manageable sizes with GParted I get a LibGParted error, went to dash/disks and I'm currently formatting it that way but it is only showing up as an 800gb drive. Anyone can help me find where the rest of it went? :)

---

### Post by oldfred on 2013-05-01
If drive is over 2.2TB you have to use gpt partitioning.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)


 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Ubuntu will boot from gpt drives in either UEFI or BIOS/CSM mode, but Windows will only boot from gpt drives in UEFI mode.
Default install of Ubuntu only creates / (root) and swap. And grub has had issues with very large / partitions. better to create a 25GB / partition and use the rest of the drive as /home or data partition(s).

      
 Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code, and since the EFI System Partition (ESP) is used by EFI with a FAT-32 filesystem for storing EFI files, the two cannot be the same partition.
If you're using UEFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP)
If a new drive, to be safe, create both of these partitions, in addition to your regular Linux partitions. But the efi partition has to be first. Do not configure Linux to use either the ESP or the BIOS Boot Partition; they'll be used automatically by GRUB, if necessary.

---

### Post by Arachnaphobe on 2013-05-02
Thanks for the quick reply, I'm still wading through all those links :)
Is there any reason why the 3tb disk might be showing up as 800gb?
fdisk -l gives me this:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004f6bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   992295642   496146797+  83  Linux
/dev/sda2       992296958  1953523711   480613377    5  Extended
/dev/sda5      1945139200  1953523711     4192256   82  Linux swap / Solaris
/dev/sda6      1921368064  1945135103    11883520   82  Linux swap / Solaris
/dev/sda7       992296960  1921366015   464534528   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 801.6 GB, 801569726464 bytes
255 heads, 63 sectors/track, 97451 cylinders, total 1565565872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  1565565871   782782935+  ee  GPT

```
/dev/sdb being the 3tb disk. This is on my working PC with the disk connected by an external dock, if that's any help at all.

---

### Post by Arachnaphobe on 2013-05-02
edit: double post.

---

### Post by oldfred on 2013-05-02
Not sure if I understand why, but some external drive docks do not work with very large drives. 
Did it see it correctly before. 
Does BIOS see drive correctly?

Usually the new drives are 4K drives not 512? Many show as 512/4k in parted list.
       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by Arachnaphobe on 2013-05-02
I put the disk back into the new pc and it showed up as 2.73tb. I tried to install Ubuntu from USB and when it rebooted I got a grub prompt, tried installing SuSe 12.3 from dvd and it failed to load kernal, tried to install Win 7 but that didn't want to know either.
So for now I've had to put a smaller drive in, disable EFI boot and install win7 :(

---

### Post by oldfred on 2013-05-02
Because it is gpt, Windows has to install in UEFI mode.
Ubuntu will boot from gpt partitioned drives with either BIOS or UEFI.
But I prefer different drives for Linux and Windows. 
But to dual boot both systems have to be UEFI or both BIOS.

---

### Post by Arachnaphobe on 2013-05-02
Originally I had installed Win 8 on it, I had planned a small windows partition for gaming and Linux for real stuff. Win 8 installed fine, then on the second day it told me that the disks I had were only for upgrade, not a clean install. Then it went online, did something and then turned the PC off. That's when all this started, maybe I'll just invest in a new drive, burn the win 8 disks and just use this disk for backups. 

Thanks for your help, please go ahead and mark this solved as I don't think there's a lot more I can do (not technically aware enough to start rebuilding boot sectors and that kind of thing :) )

---

### Post by oldfred on 2013-05-02
I have seen several cases where Windows has done something nasty to the very large gpt drives. It may not fully recognize drives that large. I would think Windows 8 would not have those kind of issues.

---

### Post by Arachnaphobe on 2013-05-03
It was also opening my emails when I used it before. I wondered why I was never getting any new mail, but when I checked there were loads I hadn't seen before... as soon as I uninstalled it I started getting unopened emails again, Win 8 is Satan's work I tell you.

---

