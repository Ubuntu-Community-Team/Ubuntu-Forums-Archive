---
title: "Ubuntu wont start - how to recover data?"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by tululum on 2012-10-25
Hi,

I installed ubuntu from wubi about month ago and now it wont start (GRUB command prompt show up). I googled and found there is something wrong with my /ubuntu/disks/root.disk file (mine has 0 bytes). Everyone suggested chkdsk from win and then recover it from found.000 folder, but that didnt worked for me (chkdsk didnt recovered anything).

I just need to recover my data because i have projects for university there... I mounted live DVD and ran bootinfosript. Here are the results:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/swap.disk

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    33,556,479    33,554,432  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,556,480    33,761,279       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          33,761,280   853,891,071   820,129,792   7 NTFS / exFAT / HPFS
/dev/sda4         853,891,072   976,771,071   122,880,000   f W95 Extended (LBA)
/dev/sda5         853,893,120   976,771,071   122,877,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 20.0 GB, 20014718976 bytes
255 heads, 63 sectors/track, 2433 cylinders, total 39091248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048     8,390,655     8,388,608  84 OS/2 hidden C: drive
/dev/sdb2           8,392,704    39,086,079    30,693,376  73 Unknown


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B0C0039AC0036646                       ntfs       PQSERVICE
/dev/sda2        DA7004AA70049005                       ntfs       SYSTEM RESERVED
/dev/sda3        8A1A06CA1A06B36D                       ntfs       Acer
/dev/sda5        883C62443C622D7E                       ntfs       Linux

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  c9 26 aa e9 ec eb 9d 01  00 00 00 00 00 00 00 00  |.&..............|
00000010  00 00 00 00 00 00 00 00  04 ff ff 1f 00 00 00 00  |................|
00000020  00 00 00 00 00 00 03 00  00 00 00 f0 00 00 00 00  |................|
00000030  00 00 00 00 ff ff 4f 42  2f e0 ff 80 6f f9 0f 50  |......OB/...o..P|
00000040  6a f2 ff ff 1f fe 05 e4  da fe fe ff ff ff 8f 58  |j..............X|
00000050  ba fe ff ff ff ff ff ff  fe f7 de ff ff ff 0f 79  |...............y|
00000060  b8 e6 d6 ff ff ff 8f 79  fc e6 da ff ff ff 0f c0  |.......y........|
00000070  ef ff db ff ff ff 0f 40  fe fe df ff ff ff 4f 00  |.......@......O.|
00000080  ff f2 dc ff ff ff df 74  ec f6 dc ff ff ff 8f 41  |.......t.......A|
00000090  fa f6 de ff ff ff ef b0  77 fc df ff ff ff 1f 3c  |........w......<|
000000a0  9e fa d8 ff ff ff 5f 7f  ee b4 db ff ff ff df 7d  |......_........}|
000000b0  98 67 d8 ff ff ff df 3d  66 f4 d2 ff ff ff ff bf  |.g.....=f.......|
000000c0  0a e9 f6 ff ff ff 9f 09  ff ff ff ff ff ff ff ff  |................|
000000d0  fe ff ff ff ff ff ff ff  fe ff ff ff ff ff ff ff  |................|
*
00000140  fe ff ff ff ff ff ff ff  02 99 df bf ff ff af 76  |...............v|
00000150  04 6d e1 ff ff ff 2f c2  54 09 e1 ff ff ff 2f 82  |.m..../.T...../.|
00000160  04 09 e1 ff ff ff 2f 82  8d 09 e1 ff ff ff 2f 82  |....../......./.|
00000170  15 dd e9 ff ff ff 2f 9f  04 b9 ff 07 1c 00 00 00  |....../.........|
00000180  f0 ff 01 c0 ff ff ff 9f  fe ff ff ff ff ff ff ff  |................|
00000190  fe ff ff ff ff ff ff ff  fe ff ff ff ff ff ff ff  |................|
*
00000200


=============================== StdErr Messages: ===============================

sda5/ubuntu/disks/root.disk: Input/output error
Found Wubi on sda5. But could not create a loop device.

```Please is there any way to recover my data? I have just few files there i really need. Thanks for any help!!

---

### Post by Mark Phelps on 2012-10-26
With a zero-length file, there is no hope of any recovery.  Plus, you have the added complication of a Linux file resting inside a Windows filesystem.

The best Windows data recovery app I've seen is RecoverMyFiles from runtime software. You could download that, install it, run it -- and see if it recovers the file.  You have to purchase it to actually save the file, but at least this way, you can see if it finds anything.

---

