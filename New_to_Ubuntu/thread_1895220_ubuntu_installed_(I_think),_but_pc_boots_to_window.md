---
title: "ubuntu installed (I think), but pc boots to windows automatically"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by kongluke on 2011-12-14
Hello everyone,

I'm trying to turn my eee PC into an Ubuntu/Windows dual-boot.  The Eee came with four partitions, so I (maybe rashly) deleted the D:\ partition (used only for my data, as far as I know) before I believe I installed Ubuntu from a USB drive.  However, since that first installation I've not been able to get into Ubuntu again--the computer automatically boots up windows.  I disabled "boot booster" and "express gate" in BIOS, and did "sudo apt-get install grub" but neither worked.  

This is what is yielded by "sudo fdisk -lu":
/dev/sdb1 * 2048 209818247 104857600 7 HPFS/NTFS/exFAT
/dev/sbd2 209717248 241174527 15728649 1b Hidden W95 FAT32
/dev/sbd3 488353792 488395119 26664 ef EFI (FAT-12/16/32)
/dev/sdb4 241176574 488353791 123588689 5 Extended
/dev/sdb5 241176576 486275071 122549248 83 Linux
/dev/sdb6 486277120 488353791 1038336 82 Linux swap / solaris
(There's also a second listing for the USB drive, sda1 (Boot *, Id = b, System = W95 FAT32))

I've been advised to "sudo update-grub" after "sudo chroot [name of partition I mounted Ubuntu to]", but I'm not sure which that is (if I mounted it at all).

Advice much appreciated!
Luke

---

### Post by lechien73 on 2011-12-14
Hi Luke,

The first thing would be to boot from a LiveCD/USB, and then go to [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net). Follow the instructions at that link to download the script and generate a RESULTS.txt file.

When you have the RESULTS.txt file, please post the contents here between CODE tags (the **#** button on the toolbar. That will help us to see what we're dealing with.

It may be as simple as just running:

```
sudo install-grub /dev/sdb
```

But don't run that until we've had chance to look at your boot information :)

---

### Post by Henkdroid on 2011-12-14
If, in windows, you look in the system manager (or similar) there should be something about boot up options, you can easily see if Ubuntu shows up, and if the delay time is set to 0.
When you get used to Ubuntu you could see about BURG, a nice GUI instead of the default plain text GRUB.

---

### Post by Mark Phelps on 2011-12-14
It looks like you installed Ubuntu to its own partitions -- which would not modify the Windows OS selection menu in any way.  Thus, when you boot into Windows, you would not get a selection menu.  This means there is nothing inside Windows you can check to see what went wrong.

We need the results of the script you were provided to see what's wrong.

---

### Post by kongluke on 2011-12-15
Thank you!  Here's the RESULTS.txt:
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 18784 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 NTFS / exFAT / HPFS
/dev/sda2         209,717,248   241,174,527    31,457,280  1b Hidden W95 FAT32
/dev/sda3         488,353,792   488,395,119        41,328  ef EFI (FAT-12/16/32)
/dev/sda4         241,176,574   488,353,791   247,177,218   5 Extended
/dev/sda5         241,176,576   486,275,071   245,098,496  83 Linux
/dev/sda6         486,277,120   488,353,791     2,076,672  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,827,455     7,819,264   b W95 FAT32


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,192    15,564,799    15,556,608   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        186EB4AD6EB48552                       ntfs       
/dev/sda2        86F4-D40A                              vfat       
/dev/sda5        d3ab66f3-a721-4119-8ed5-6d503c06f8c9   ext4       
/dev/sda6        0130dc66-56c6-4ada-b678-d438690949f6   swap       
/dev/sdb1        1860-BD52                              vfat       PENDRIVE
/dev/sdc1        20AE-D41A                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/20AE-D41A         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d3ab66f3-a721-4119-8ed5-6d503c06f8c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0130dc66-56c6-4ada-b678-d438690949f6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                vmlinuz                                        1

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

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 10 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 80 0c  |........?.......|
00000020  f8 ff df 01 f2 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0a d4 f4 86 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sda4

00000000  06 00 00 00 00 00 00 00  9e 68 3f 00 00 00 00 00  |.........h?.....|
00000010  63 a2 13 26 64 aa cb 01  1d 55 34 d7 fa b2 cc 01  |c..&d....U4.....|
00000020  1d 55 34 d7 fa b2 cc 01  1d 55 34 d7 fa b2 cc 01  |.U4......U4.....|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 10 00 00 00 00  63 a2 13 26 64 aa cb 01  |........c..&d...|
00000050  2b 0b 32 d7 fa b2 cc 01  2b 0b 32 d7 fa b2 cc 01  |+.2.....+.2.....|
00000060  2b 0b 32 d7 fa b2 cc 01  00 00 00 00 00 00 00 00  |+.2.............|
00000070  00 00 00 00 00 00 00 00  00 00 00 10 00 00 00 00  |................|
00000080  90 dd 01 18 00 00 00 00  77 dd 01 18 00 00 00 00  |........w.......|
00000090  00 00 00 00 00 00 00 00  28 00 00 00 00 00 00 00  |........(.......|
000000a0  01 00 00 00 40 00 00 00  00 00 00 00 00 00 00 00  |....@...........|
000000b0  1b 00 01 00 28 00 00 00  28 00 00 00 18 00 00 00  |....(...(.......|
000000c0  00 00 00 00 00 00 02 00  00 00 00 00 00 00 00 00  |................|
000000d0  c0 e0 77 a7 20 f3 d4 b9  9b dd 01 18 00 00 00 00  |..w. ...........|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  30 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |0...........@...|
00000100  00 00 00 00 00 00 00 00  16 00 15 00 28 00 08 00  |............(...|
00000110  28 00 08 00 70 00 01 00  00 00 00 00 00 00 00 00  |(...p...........|
00000120  c8 00 00 00 00 00 00 00  db 40 00 00 00 00 00 00  |.........@......|
00000130  41 41 00 00 03 00 00 00  a7 dd 01 18 00 00 00 00  |AA..............|
00000140  9b dd 01 18 00 00 00 00  9b dd 01 18 00 00 00 00  |................|
00000150  88 00 00 00 00 00 00 00  01 00 00 00 40 00 00 00  |............@...|
00000160  00 00 00 00 00 00 00 00  0f 00 0e 00 28 00 00 00  |............(...|
00000170  28 00 60 00 58 08 01 00  00 00 40 00 00 00 08 00  |(.`.X.....@.....|
00000180  01 00 00 00 00 00 00 00  0e 8c 3f 00 00 00 00 00  |..........?.....|
00000190  93 7d 00 00 00 00 01 00  60 00 4e 00 00 00 00 00  |.}......`.N.....|
000001a0  79 7d 00 00 00 00 01 00  e7 ba 36 26 64 aa cb 01  |y}........6&d...|
000001b0  00 dc f5 dd 4e c6 c0 01  8f 1c 37 26 64 aa 00 fe  |....N.....7&d...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e8 9b 0e 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e8  9b 0e 00 b8 1f 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



```

---

### Post by oldfred on 2011-12-15
You have/had a wubi install in sda, not sure if all of that is still there, no root.disk file is shown.

Your install in sda5 shows no grub files, no kernel files and just vmlinuz? While if the rest of the install was correct, it might be repairable, at this point it looks like a reinstall would be the quickest way to fix it.

You need to use manual install and choose sda5 as / (root) with format ext4. Since you have swap it will auto find it and you can finish the install.

Your Linux partition is actually large. I generally suggest 10-25GB for / (root) with separate data and/or /home partitions. I do think with dual booting Windows it is much better to have a shared NTFS (d: in Windows) data partition, so you do not write into the Windows system (c: ) partition as that can lead to issues.  I prefer for both Windows & Linux to keep systems separate from data as much as possible.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by kongluke on 2011-12-18
Thank you! 
Luke

---

