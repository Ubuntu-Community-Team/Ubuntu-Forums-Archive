---
title: "Installation Issue - Change MBR without Grub?"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by MikeInDetroit on 2012-01-12
This is my first time trying to do this so I'm plodding around the forums trying to guess at the right keywords to use to see if there's a problem. 

I did the installation using Wubi on my XP, got a problem I've found others have, but I can't use the solution (selecting Esc, Insert, to get into grub) because Sophos is the primary boot loader.  Also, when I use LiveCD I cannot find the hard drive probably because it's encrypted.  So I want to change the MBR record but I'm not sure how to do it.  I'm not even sure a Wubi install over the XP encrypted drive will work and if I should instead try to create a separate partition rather than Wubi it in. 


Short Version of: [http://ubuntuforums.org/showthread.php?t=1907540](http://ubuntuforums.org/showthread.php?t=1907540)

1. Used Wubi 
2. Inside XP
3. Single drive partition type: HPFS/NTFS/exFAT
4. Likely encrypted drive
5. Sophos, not GRUB, primary boot loader 
6. Upon startup Ubuntu drops into common error (below). Cannot find root drive
7. Wanted to edit MBR to point to sda1 (correct name)
8. Cannot use GRUB as Sophos controlling
9. LiveCD does not seem to find the root drive !!!

Questions:
1. On encrypted HD (laptop) would Wubi install work?
2. Can I change the MBR any other way either directly from XP or copying it to another Ubuntu installation and editing it there?

(Obviously I don't want to run any of the tools that fix a grub installation as it will just clobber the XP Sophos boot loader or just pooch things up so...)





The Ubuntu startup issue:

Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb1 does not exist. Dropping to a shell!
(initramfs)

---

### Post by Mark Phelps on 2012-01-12
First off, a Wubi installation does NOT change the MBR -- because it uses the Windows boot loader to manage OS selection.

Second, do NOT install GRUB.  This will only break something.

If your Windows OS menu does not include an entry for Ubuntu, then something went wrong during the installation.

Don't use Wubi, so don't know if the Wubi installer will work when encryption is in the way.

---

### Post by bcbc on 2012-01-12
If a live CD cannot see the drive, then neither will Wubi. This isn't a hardware based encryption (or BIOS) so only by running the Sophos software (in Windows) can you unlock it (it states on the Website that it requires Windows to run). 

And Wubi doesn't run in Windows (the installer wubi.exe does, but after that it's like a normal dual boot).

So, you can use an external drive or second hard drive that isn't encrypted - or else you're left with installing Ubuntu in a virtual machine.

---

### Post by MikeInDetroit on 2012-01-13
I've attached below the results of running the boot script. 

I guess I'm not sure what I should try mounting, is it sda1 or sdb1 or something else?  I tried sda1 with a number of different types but just got different errors.


                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,295,439   156,295,377   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        1F02-0A4D                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


******************************************************************

This is the FDISK result:

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c32b726

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156295439    78147688+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    c  W95 FAT32 (LBA)
/dev/sdb3           24897       24897           0    0  Empty


*****************************************************

These are some mount attempts using sda1


ubuntu@ubuntu:/$ sudo mount -t ntfs /dev/sda1 /media/exfat
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

ubuntu@ubuntu:/$ sudo mount -t hpfs /dev/sda1 /media/exfat
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/$ sudo mount -t vfat /dev/sda1 /media/exfat
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by oldfred on 2012-01-14
Again if it is encrypted by Windows, it will not mount with Linux. You need the Windows software to un-encrypt it.

Boot script is just showing it cannot mount sda1. Partition table says it is NTFS, but script tries to parse NTFS partition boot sector to confirm it is NTFS. But your encryption must also include partition boot sector.

---

### Post by MikeInDetroit on 2012-01-16
I found this link:

[http://community.sophos.com/t5/Sophos-SafeGuard-products/dual-boot-Win7-Ubuntu-WUBI/td-p/15281](http://community.sophos.com/t5/Sophos-SafeGuard-products/dual-boot-Win7-Ubuntu-WUBI/td-p/15281)

So, it confirms what you've said.   I guess at this point, if I can't unencrypt the HD, I should assume there is no HD and run from a USB connected drive (or just forget it).   Is that would you would do?

---

### Post by oldfred on 2012-01-16
I do not use encyption, so I do not know.

Another suggestion:
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

