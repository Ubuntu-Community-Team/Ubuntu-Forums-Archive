---
title: "Unable to boot after Grub Load order change then grub-repair attempt"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by numerialized on 2013-04-17
Greetings,
I am pretty new to ubuntu, in fact bt5r3 ubuntu13... Always wanted to give it a try but never had the time.. Anyway, most of the queries I have put on google directed me to ubuntuforums therefore here I am.
To summarize my current situation, I am unable to boot and am getting an error like "Error: file not found" and dropping to grub rescue.
I have come here following the steps I had found on several threads on this forum, as it started...
I had my OS running but without nvidia funcioning properly, so I purged it and installed anew with apt-get... Well that didn't work; therefore I downloaded it from nvidia website and installed it. Then I fixed my atheros 2200 to work with some patches.
After I rebooted, it started telling me "Alert! /dev/... by-uuid=...... not found dropping to a shell" (initramfs)
Then I followed the instructions at another thread and downloaded linux-secure-remix and booted ubuntu again to use grub-repair. It told me that it has failed to install grub2... and after a reboot I came to the screen where I keep getting grub-rescue.
I had written ls at grub rescue screen and got a response (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)
I had written ls at each of them and all of them gave me "error file not found" save for (hd0,4) which listed linux folders including /boot and /root however it didn't have grub, like the rest of them...
I can boot from my Win7 CD which assures me that everything is fine when I run boot repair from there. And detects my win 7 installation just fine; but again it won't boot without grub working properly.
Now I booted up kali from a live USB and am writing from there; I would make a clean install but instead;I will be here for long hours until I solve this for I have important documents scattered around in Windows 7 ntfs in one of those partitions...
I am putting a few things that I had seen on other threads, of what little use they may be, may save time?
Thanks in advance.

A sidenote: I have raid 0 on my 2 750GB disks; used 800GB for windows on a logical partition then I installed my linux on a 500GB logical partition changing the boot manager to grub, then I changed the grub boot order. I also have a few recovery partitions

```

# sudo fdisk -l

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa438c2c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    21536767    10767360   27  Hidden NTFS WinRE
/dev/sda2        21536768    21741567      102400   27  Hidden NTFS WinRE
/dev/sda3   *    21741568  1766868991   872563712    7  HPFS/NTFS/exFAT
/dev/sda4      1766868992  2930289151   581710080   83  Linux

Disk /dev/sdc: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8192     7843839     3917824    c  W95 FAT32 (LBA)

```

```

# sudo blkid
/dev/sdb: TYPE="isw_raid_member" 
/dev/sr0: LABEL="UDF Volume" TYPE="udf" 
/dev/sdc1: LABEL="PENDRIVE" UUID="150A-213D" TYPE="vfat" 
/dev/loop0: TYPE="squashfs"
 
```

# cat /etc/fstab gives no results even with chmod -R 755 /etc
There's an fstab.d folder and nothing else in /etc with | grep fs

insmod and normal commands at grub-rescue give "File not found" error

```
# sudo fsck
fsck from util-linux 2.20.1
```

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for /boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
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

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 30526 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    21,536,767    21,534,720  27 Hidden NTFS (Recovery Environment)
/dev/sda2          21,536,768    21,741,567       204,800  27 Hidden NTFS (Recovery Environment)
/dev/sda3    *     21,741,568 1,766,868,991 1,745,127,424   7 NTFS / exFAT / HPFS
/dev/sda4       1,766,868,992 2,930,289,151 1,163,420,160  83 Linux

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          8,192     7,843,839     7,835,648   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb                                                isw_raid_member 
/dev/sdc1        150A-213D                              vfat       PENDRIVE
/dev/sr0                                                udf        UDF Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /lib/live/mount/rootfs/filesystem.squashfs squashfs   (ro,noatime)
/dev/sdc1        /lib/live/mount/medium   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=utf8,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,relatime,uid=0,gid=0,umask=77,dmode=500,iocharset=utf8,uhelper=udisks)


========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 0
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/hdt.c32                               1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/hdt.c32                   :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  84 d4 ea 84 d4 ea 85 d4  e9 85 d4 e9 85 d4 e9 86  |................|
00000010  d4 e9 86 d4 e9 86 d5 ea  87 d6 eb 88 d6 eb 88 d6  |................|
00000020  eb 88 d6 eb 89 d6 ea 89  d6 ea 89 d6 ea 89 d7 eb  |................|
00000030  8a d8 ec 8a d8 ec 8c d8  ec 8c d8 ec 8c d8 ec 8c  |................|
00000040  d8 ec 8d d8 ec 8d d8 ec  8d d8 ec 8d d7 ec 8e d7  |................|
00000050  ec 8e d7 ec 8e d7 ec 8f  d8 ec 8f d8 ec 8f d8 ec  |................|
00000060  8f d8 ec 8f 00 00 ff ff  ff ff ff ff ff ff ff ff  |................|
00000070  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000140  ff ff ff ff ff ff ff ff  ff ff fe fe fe fe fe fe  |................|
00000150  fe fe fe fe fe fe fe fe  fe fe fe fe fe fe fe fe  |................|
00000160  fe fe fe fe fd fd fe fc  fe ff fd fe ff fd fe ff  |................|
00000170  fd fe ff fd fe ff fd fe  ff fd fe ff fd fe ff fe  |................|
00000180  ff fe fe ff fe fd ff fe  fd ff fe fd ff fe fd ff  |................|
00000190  fe fd ff fd fc fd fe fc  ff fe fd fe fe fc fe ff  |................|
000001a0  fe ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001d0  ff ff ff ff ff ff ff ff  ff fe ff ff fe ff ff fe  |................|
000001e0  ff ff fe ff ff fe ff ff  fe ff ff fe ff ff fe ff  |................|
000001f0  ff fe fe ff fd fe ff fd  fe ff fd fe ff fd fe ff  |................|
00000200

Unknown BootLoader on sda3

00000000  0e 10 00 75 0b 68 c2 ab  06 10 e8 86 fe ff ff 59  |...u.h.........Y|
00000010  6a 08 e8 da 33 01 00 59  85 c0 74 10 8b 0d b4 40  |j...3..Y..t....@|
00000020  0e 10 89 08 8b 4d 08 89  48 04 eb 02 33 c0 a3 b4  |.....M..H...3...|
00000030  40 0e 10 5d c3 8b ff 55  8b ec 8b 45 08 83 78 50  |@..]...U...E..xP|
00000040  00 76 18 83 78 54 10 72  05 8b 41 40 eb 03 83 c0  |.v..xT.r..@@....|
00000050  40 50 6a 00 e8 fd 84 01  00 59 59 5d c3 6a 04 b8  |@Pj......YY].j..|
00000060  f9 23 0a 10 e8 32 74 01  00 8b f1 89 75 f0 c7 46  |.#...2t.....u..F|
00000070  04 01 00 00 00 33 c0 89  45 fc 89 46 08 89 46 0c  |.....3..E..F..F.|
00000080  89 46 10 8a 45 08 68 60  95 0b 10 8d 4e 18 c7 06  |.F..E.h`....N...|
00000090  08 2f 0b 10 88 46 14 e8  e4 01 fe ff 8b c6 e8 97  |./...F..........|
000000a0  74 01 00 c2 04 00 6a 08  b8 26 24 0a 10 e8 e9 73  |t.....j..&$....s|
000000b0  01 00 a1 b8 40 0e 10 8b  f0 85 c0 75 7b 50 8d 4d  |....@......u{P.M|
000000c0  f0 e8 90 fd ff ff a1 b8  40 0e 10 21 75 fc 8b f0  |........@..!u...|
000000d0  85 c0 75 58 6a 34 e8 16  33 01 00 59 8b c8 89 4d  |..uXj4..3..Y...M|
000000e0  ec c6 45 fc 01 85 c9 74  0a 56 e8 6e ff ff ff 8b  |..E....t.V.n....|
000000f0  f0 eb 02 33 f6 56 c6 45  fc 00 e8 39 fe ff ff 8d  |...3.V.E...9....|
00000100  4e 18 c7 46 10 3f 00 00  00 c7 04 24 0c 2f 0b 10  |N..F.?.....$./..|
00000110  e8 3b 01 fe ff 8b ce 89  35 bc 40 0e 10 e8 5e 9f  |.;......5.@...^.|
00000120  fd ff a1 bc 40 0e 10 a3  d4 40 0e 10 83 4d fc ff  |....@....@...M..|
00000130  8d 4d f0 e8 46 fd ff ff  8b c6 e8 fb 73 01 00 c3  |.M..F.......s...|
00000140  8b ff 55 8b ec 6a 00 6a  00 e8 08 84 01 00 59 59  |..U..j.j......YY|
00000150  85 c0 75 05 b8 ba 9b 0b  10 56 8b 75 08 50 8d 4e  |..u......V.u.P.N|
00000160  3c e8 ea 00 fe ff 83 7d  0c 00 74 10 ff 75 0c 6a  |<......}..t..u.j|
00000170  00 e8 e0 83 01 00 59 59  85 c0 75 05 b8 60 95 0b  |......YY..u..`..|
00000180  10 50 8d 4e 58 e8 c6 00  fe ff 5e 5d c3 8b ff 55  |.P.NX.....^]...U|
00000190  8b ec 8b 45 0c 83 78 18  10 56 57 72 05 8b 70 04  |...E..x..VWr..p.|
000001a0  eb 03 8d 70 04 6a 00 6a  00 e8 a8 83 01 00 59 59  |...p.j.j......YY|
000001b0  85 c0 75 05 b8 ba 9b 0b  10 8b 7d 08 50 8d 4f 3c  |..u.......}.P.O<|
000001c0  e8 8b 00 fe ff 85 f6 74  0e 56 6a 00 e8 85 83 01  |.......t.Vj.....|
000001d0  00 59 59 85 c0 75 05 b8  60 95 0b 10 50 8d 4f 58  |.YY..u..`...P.OX|
000001e0  e8 6b 00 fe ff 5f 5e 5d  c3 e8 b8 fe ff ff b8 d4  |.k..._^]........|
000001f0  40 0e 10 c3 8b ff 55 8b  ec 8b 45 14 56 57 85 c0  |@.....U...E.VW..|
00000200

Unknown BootLoader on sda4



========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected



```

---

### Post by fantab on 2013-04-17
First of all, boot with ubuntu Live CD/USB and Backup those important files you have on NTFS. Once you have booted Ubuntu with "Try Ubuntu" option. Choose to open "nautilus" File-Browser/Manager. Then mount the NTFS partiton and it should be accessible and do the back up.

[ATTACH=CONFIG]241474[/ATTACH]

Get back here once you have BACKED UP your important DATA.
Good Luck...

---

### Post by oldfred on 2013-04-17
I do not know RAID and there are many types of RAID implementations. But the grub installer does not see nor install correctly to RAID from a desktop installer. You should use server or alternative that have all the extra RAID drivers.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)


 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by numerialized on 2013-04-17
Thank you, working on it.

---

### Post by numerialized on 2013-04-17
Yes, I am using it for its speed advantage; Grub seemed to be working well until I tried to repair it.

---

### Post by numerialized on 2013-04-17
I have backed up my vital data, thanks to you; rest are my personal files for which I lack a sizeable media to back up.
Now I am on Ubuntu Live... 
Any thoughts on what I should do next? Some results have changed when I swapped from kali, I am putting those here.

```

ubuntu@ubuntu:~$ sudo cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

```

ubuntu@ubuntu:/$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="b31453f2-adf0-3940-80db-ac65fbf37fce" TYPE="ext2" 
/dev/sr0: LABEL="UDF Volume" TYPE="udf" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb1: LABEL="PENDRIVE" UUID="1CEE-2753" TYPE="vfat" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/mapper/isw_beffegcbgh_Volume0p1: LABEL="BIOS_RVY" UUID="E4CA1A30CA19FF8A" TYPE="ntfs" 
/dev/mapper/isw_beffegcbgh_Volume0p2: LABEL="System" UUID="D2FE1CB2FE1C90B9" TYPE="ntfs" 
/dev/mapper/isw_beffegcbgh_Volume0p3: LABEL="OS_Install" UUID="1A5E2F965E2F69A9" TYPE="ntfs" 
/dev/mapper/isw_beffegcbgh_Volume0p4: UUID="5cfe77b7-bd92-4e94-9472-0d88d69a9924" TYPE="ext4" 

```

```

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa438c2c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    21536767    10767360   27  Hidden NTFS WinRE
/dev/sda2        21536768    21741567      102400   27  Hidden NTFS WinRE
/dev/sda3   *    21741568  1766868991   872563712    7  HPFS/NTFS/exFAT
/dev/sda4      1766868992  2930289151   581710080   83  Linux

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7843839     3917824    c  W95 FAT32 (LBA)

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/isw_beffegcbgh_Volume0: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0xa438c2c0

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_beffegcbgh_Volume0p1            2048    21536767    10767360   27  Hidden NTFS WinRE
/dev/mapper/isw_beffegcbgh_Volume0p2        21536768    21741567      102400   27  Hidden NTFS WinRE
/dev/mapper/isw_beffegcbgh_Volume0p3   *    21741568  1766868991   872563712    7  HPFS/NTFS/exFAT
/dev/mapper/isw_beffegcbgh_Volume0p4      1766868992  2930289151   581710080   83  Linux

Disk /dev/mapper/isw_beffegcbgh_Volume0p1: 11.0 GB, 11025776640 bytes
255 heads, 63 sectors/track, 1340 cylinders, total 21534720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_beffegcbgh_Volume0p1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_beffegcbgh_Volume0p2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x73736572

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_beffegcbgh_Volume0p2p1      1920221984  3736432267   908105142   72  Unknown
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p2p2   ?  1936028192  3889681299   976826554   6c  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p2p3   ?           0           0           0    0  Empty
/dev/mapper/isw_beffegcbgh_Volume0p2p4        27722122    27722568         223+   0  Empty
Partition 4 does not start on physical sector boundary.

Disk /dev/mapper/isw_beffegcbgh_Volume0p3: 893.5 GB, 893505241088 bytes
255 heads, 63 sectors/track, 108629 cylinders, total 1745127424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_beffegcbgh_Volume0p3p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p3p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p3p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_beffegcbgh_Volume0p3p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_beffegcbgh_Volume0p4: 595.7 GB, 595671121920 bytes
255 heads, 63 sectors/track, 72419 cylinders, total 1163420160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_beffegcbgh_Volume0p4 doesn't contain a valid partition table
ubuntu@ubuntu:/$ 

```

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of 
    /dev/mapper/isw_beffegcbgh_Volume0 and looks at sector 1 of the same hard 
    drive for core.img. core.img is at this location and looks in partition 4 
    for /boot/grub.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 2012-10-23
    Boot sector info:  Syslinux looks at sector 30526 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

isw_beffegcbgh_Volume01: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_beffegcbgh_Volume02: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_beffegcbgh_Volume03: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_beffegcbgh_Volume04: _______________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,843,839     7,835,648   c W95 FAT32 (LBA)


Drive: isw_beffegcbgh_Volume0 _____________________________________________________________________

Disk /dev/mapper/isw_beffegcbgh_Volume0: 1500.3 GB, 1500308045824 bytes
255 heads, 63 sectors/track, 182402 cylinders, total 2930289152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_beffegcbgh_Volume01              2,048    21,536,767    21,534,720  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_beffegcbgh_Volume02         21,536,768    21,741,567       204,800  27 Hidden NTFS (Recovery Environment)
/dev/mapper/isw_beffegcbgh_Volume03   *     21,741,568 1,766,868,991 1,745,127,424   7 NTFS / exFAT / HPFS
/dev/mapper/isw_beffegcbgh_Volume04      1,766,868,992 2,930,289,151 1,163,420,160  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       b31453f2-adf0-3940-80db-ac65fbf37fce   ext2       casper-rw
/dev/mapper/isw_beffegcbgh_Volume0p1 E4CA1A30CA19FF8A                       ntfs       BIOS_RVY
/dev/mapper/isw_beffegcbgh_Volume0p2 D2FE1CB2FE1C90B9                       ntfs       System
/dev/mapper/isw_beffegcbgh_Volume0p3 1A5E2F965E2F69A9                       ntfs       OS_Install
/dev/mapper/isw_beffegcbgh_Volume0p4 5cfe77b7-bd92-4e94-9472-0d88d69a9924   ext4       
/dev/sda                                                isw_raid_member 
/dev/sdb1        1CEE-2753                              vfat       PENDRIVE
/dev/sdc                                                isw_raid_member 
/dev/sr0                                                udf        UDF Volume

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_beffegcbgh_Volume0
isw_beffegcbgh_Volume0p1
isw_beffegcbgh_Volume0p2
isw_beffegcbgh_Volume0p3
isw_beffegcbgh_Volume0p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/mapper/isw_beffegcbgh_Volume0p3 /media/OS_Install        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/menu.c32                              1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/menu.c32                  :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_beffegcbgh_Volume01


Unknown BootLoader on isw_beffegcbgh_Volume02


Unknown BootLoader on isw_beffegcbgh_Volume03


Unknown BootLoader on isw_beffegcbgh_Volume04



========= Devices which don't seem to have a corresponding hard drive: =========

sdd 

=============================== StdErr Messages: ===============================

./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
hexdump: /dev/mapper/isw_beffegcbgh_Volume01: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume01: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume02: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume02: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume03: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume03: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume04: No such file or directory
hexdump: /dev/mapper/isw_beffegcbgh_Volume04: No such file or directory

```

---

### Post by oldfred on 2013-04-17
This looks correct. Are you trying to boot in BIOS mode not RAID?

>  Grub2 (v1.97-1.98) is installed in the MBR of 
    /dev/mapper/isw_beffegcbgh_Volume0



---

### Post by numerialized on 2013-04-17
> **oldfred said:**
> This looks correct. Are you trying to boot in BIOS mode not RAID?

By default, while booting it goes through
BIOS boot splash
RAID boot screen
BIOS boot splash again

Then it drops to grub-recovery... So I think it might have already passed loading Intel RST(RAID) point by the time boot is handled and GRUB is tried to launch.

Updating my previous post with Live Ubuntu boot fstab...

---

### Post by oldfred on 2013-04-17
Sounds like RAID is not booting, but I know nothing about how grub2 really works with RAID.

---

### Post by numerialized on 2013-04-17
Thanks oldfred. I'd rather not get to RAID's settings either. It worked fine so far and I don't want to tinker with how it is shipped at that level. 
I noticed this... Could it have anything to do with my problem?

 => Grub2 (v1.97-1.98) is installed in the MBR of      /dev/mapper/isw_beffegcbgh_Volume0 and looks at sector 1 of the same hard      drive for core.img. core.img is at this location and looks in partition 4      for /boot/grub.

Now the boot part is at my /dev/mapper/isw_beffegcbgh_Volume03 which is at sector 21,741,568

There is also one more thing... My /boot/grub/(in my linux partition) has only "grubenv" file in it... "grub.bak" has other files... This doesn't sound right, but it's normal after a failed GRUB install I suppose. 
Should I cp the content from backup?/Try to make a GRUB installation again?

Sorry if these questions are a little absurd, I just turned my shiny laptop into a piece of rock so I am just assuming I know nothing about computers while I ask the questions.

---

### Post by oldfred on 2013-04-18
I might try the full reinstall of grub. But you have to chroot into your install to do that and with /mapper I am not sure of all the commands. It is similar to a normal chroot, but you use your /mapper instead of partitions.

I have this in my notes for just reinstalling grub to boot.
 if RAID
For RAID reinstall from live-CD/DVD/USB - install driver
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0
LVM:
sudo apt-get install lvm2
sudo vgchange -ay

But a full chroot requires a lot more, I do not think these show anything with RAID. If using live install be sure to add RAID drives to live installer or else it will not work.

 Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by numerialized on 2013-04-18
I have never done a chroot to be able to perform a slightly different version of it... Rest eludes me already. 
Thanks anyway oldfred. 
I'll wait and keep filling the thread with more findings and see if an idea pops up. 
I really don't want to get into RAID stuff without knowing what I am doing or being perfectly sure that that boot sector is my problem.

---

### Post by numerialized on 2013-04-18
So I had put on a Windows recovery disc, because it wasn't fun anymore, tried to destroy everything with bcdedit rebuildbcd... All commands in bcd menu in fact(sorry, it was long and stressful I don't know what I did)... 
Then rebooted. Now my old MS Windows boots up perfectly without grub menu and all left behind and I have no more to ask of life... 
Linux belongs to my flash drive anddefinitely not my HDD! At least not on a Intel RST RAID laptop...
Thank you everyone who took time to read and tried to help.

---

### Post by oldfred on 2013-04-18
I missed that it was the Intel SRT type RAID.
Most just turn that off, remove meta-data so grub will install correctly and then reimplement Intel SRT if they want it. Many the prefer Ubuntu just install / (root) to SSD and leave SRT off.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

But I also have full installs on flash drive, more as back for my laptop that only has one drive. Then it is just like any install to an external drive, but you have to use Something else to have a choice on where to install grub. All auto install choices will try to install to sda and you really want it on the external. If you have UEFI you need to install in UEFI mode with gpt partitioning and partition in advance to make sure you have efi partition on external.

---

### Post by rocobruno on 2013-04-20
Hi I am not sure if it is the proper place to put this but I believe that my experience on the matter could profit the community.


I recently spent hours trying to figure out how to install Ubuntu Server 12.04 LTS on a so called "fakeraid" (a cheap and common [firmware based RAID]("http://en.wikipedia.org/wiki/RAID#Firmware.2Fdriver-based_RAID") controller builtin onto the motherboard)


The install goes pretty flawlessly until you come up with GRUB install...then everything fails.


After hours of reading numerous posts and collecting puzzle pieces I came up with an hypothesis and applied it with success. I cannot explain linux behavior in regards to the RAID controllers (it is a rookie forum after all) but it has to do with [device mapper]("http://gurkulindia.com/main/2011/11/linux-understand-device-mapper-and-dm-multipath/") which in turn handle RAID volumes in some fashion.


So, you do your install as usual until you come along with the install wizard asking you to enable or not the found RAID contoller to which you will answer **yes**. For the partitioning I go along with the default, that is take all space available to make 2 partitions one for "/" and the other for "/swap".


Later on you will be presented with the results of the proposed partitioning. **Before you go further make sure you take note** of the ***/dev/mapper/isw_somerandomcharacters*** complete path as you will need it later.


Once the install done you wil then be asked to choose a path to install your GRUB. That is where you will choose ***/dev/mapper*** and complete it with the path accordinly. If you entered the path accordingly the install will conclude and the system will restart and you will be presented with the familiar BASH prompt !

---

