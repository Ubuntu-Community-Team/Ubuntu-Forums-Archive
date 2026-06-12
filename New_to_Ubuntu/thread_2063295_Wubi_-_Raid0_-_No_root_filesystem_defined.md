---
title: "Wubi - Raid0 - No root filesystem defined"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by gyiu on 2012-09-26
Hello everyone,

First post here, pretty new to linux. I've just tried installing Ubuntu 11.04 via wubi and I got the "No root filesystem defined" error.  I have a Vaio Z which has dual 64gb SSD's in raid0. I have been trying to look up a solution, but have found the solutions either not relevant to my case or not very clear. I'd love for someone to walk me through a fix. This is the RESULTS.txt from my bootinfoscript:

```
                  
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/mapper/isw_ecibiccidb_Volume0.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ecibiccidb_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ecibiccidb_Volume02: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ecibiccidb_Volume03: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    23,156,735    23,154,688  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     23,156,736    23,361,535       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          23,361,536   250,079,231   226,717,696   7 NTFS / exFAT / HPFS

/dev/sda3 ends after the last sector of /dev/sda

Drive: isw_ecibiccidb_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_ecibiccidb_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ecibiccidb_Volume01              2,048    23,156,735    23,154,688  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_ecibiccidb_Volume02   *     23,156,736    23,361,535       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ecibiccidb_Volume03         23,361,536   250,079,231   226,717,696   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 11.04 amd64
/dev/loop1                                              squashfs   
/dev/mapper/isw_ecibiccidb_Volume0p1 220E1A560E1A2379                       ntfs       Recovery
/dev/mapper/isw_ecibiccidb_Volume0p2 40C8D4F7C8D4EC62                       ntfs       System Reserved
/dev/mapper/isw_ecibiccidb_Volume0p3 B41ED6001ED5BB94                       ntfs       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_ecibiccidb_Volume0
isw_ecibiccidb_Volume0p1
isw_ecibiccidb_Volume0p2
isw_ecibiccidb_Volume0p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_ecibiccidb_Volume0p3 /isodevice               fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on isw_ecibiccidb_Volume01


Unknown BootLoader on isw_ecibiccidb_Volume02


Unknown BootLoader on isw_ecibiccidb_Volume03



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume01: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume02: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume03: No such file or directory
hexdump: /dev/mapper/isw_ecibiccidb_Volume03: No such file or directory

```

---

### Post by bcbc on 2012-09-26
This ([http://www.petur.eu/blog/?p=480](http://www.petur.eu/blog/?p=480)) indicates you need to install mdadm and remove dmraid. Which might explain why the installer and the live environment cannot view your partitions.
 
That link is for a normal install - not sure how you'd do this from a Wubi install, but if you can connect to the net and then drop to a terminal Ctrl+Alt+F1, I suppose it might work. Then Ctrl+Alt+F7 to return back to the installer.

I have no experience with Raid... :popcorn:

---

### Post by gyiu on 2012-09-26
I actually can't drop to a terminal during normal installation - everything freezes immediately if I hit those hotkeys. I can only get to it if I start with "ACPI workaround". Will this be a problem (I don't know what ACPI is)? Anybody else know about Raid drives and wubi? Would my bootinfoscript be different because I ran from that mode?

---

### Post by bcbc on 2012-09-26
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

Using acpi workarounds (i.e. kernel boot option noacpi (and some others) won't make a difference to bootinfoscript and what that link described. But it does fix lockups if your computer isn't fully acpi compliant.

This link might help you fine tune the issues (using noacpi is like a sledgehammer and removes important functions so you shouldn't use it permanently): [https://wiki.ubuntu.com/sonyvaioz](https://wiki.ubuntu.com/sonyvaioz) (I can't vouch for any of the contents).

---

### Post by critin on 2012-09-26
Wubi doesn't support raid, but some have managed work-a-rounds.  You'll need to search for those or hope someone on the forums here know what they are.
> 
**Unsupported set-ups**

**Software raid arrays**

 Although  installing Wubi to RAID is not officially supported there have been  reports of users who have done so successfully. This has not been  thoroughly tested


[https://wiki.ubuntu.com/WubiGuide/](https://wiki.ubuntu.com/WubiGuide/)

---

### Post by bcbc on 2012-09-26
The problem is more support for fakeraid in general than wubi, evidenced by the bootinfoscript. Here's a blog post I like to mention that shows the workaround for a normal Ubuntu install with fakeraid 10: [http://www.advogato.org/person/robertc/diary/158.html](http://www.advogato.org/person/robertc/diary/158.html)

The point of raid0 is what? improved performance? So installing an OS on a virtual disk (as Wubi does) is probably not ideal anyway. But for trying out it should be okay provided you can do the required workarounds.

---

