---
title: "Installaton Problem"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by kiran_viswm on 2011-11-22
Hi,
i have been working on UGR with natty narwal. I tried to upgrade and it failed. Eventually i cannot log in. The screen gets stuck with 'ugr' screen which is just before login  screen.

When i tried to install ubuntu 11.10 oneric, installer didn't detect  other operating system and even the PARTITIONS. Entire disk have to be formatted. I dont want to do that. 
Please help!

---

### Post by westie457 on 2011-11-22
> **kiran_viswm said:**
> Hi,
i have been working on UGR with natty narwal. I tried to upgrade and it failed. Eventually i cannot log in. The screen gets stuck with 'ugr' screen which is just before login  screen.

When i tried to install ubuntu 11.10 oneric, installer didn't detect  other operating system and even the PARTITIONS. Entire disk have to be formatted. I dont want to do that. 
Please help!

If you have back ups of your personal files then it probably will be better to format and reinstall.

If you do not have back ups stop using the drive.

Get your LiveCD/USB and boot from that to Try mode.

Open a terminal and post the output of ```
sudo fdisk -l
```
The l is a small L.
Also go to [here]("http://bootinfoscript.sourceforge.net/") for bootinfoscript. All necessary instructions for usage and posting are given. 

This will give us a clue of what has happened to your hard drive and possibly a way of recovering it.

---

### Post by kiran_viswm on 2011-11-22
> **westie457 said:**
> If you have back ups of your personal files then it probably will be better to format and reinstall.

If you do not have back ups stop using the drive.

Get your LiveCD/USB and boot from that to Try mode.

Open a terminal and post the output of ```
sudo fdisk -l
```
The l is a small L.
Also go to [here]("http://bootinfoscript.sourceforge.net/") for bootinfoscript. All necessary instructions for usage and posting are given. 

This will give us a clue of what has happened to your hard drive and possibly a way of recovering it.
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>..........V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1790208 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    29,048,831    28,966,912   7 NTFS / exFAT / HPFS
/dev/sda3          29,048,832   202,174,463   173,125,632   7 NTFS / exFAT / HPFS
/dev/sda4         202,178,025   625,135,615   422,957,591   f W95 Extended (LBA)
/dev/sda5         202,178,088   329,734,124   127,556,037   7 NTFS / exFAT / HPFS
/dev/sda6         329,746,432   415,426,559    85,680,128  83 Linux
Invalid MBR Signature found.
Empty Partition.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4001 MB, 4001366016 bytes
124 heads, 62 sectors/track, 1016 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,811,007     7,810,946   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        9056CD9956CD8088                       ntfs       RECOVERY
/dev/sda3        9E80D0FC80D0DBB9                       ntfs       Windows
/dev/sda5        01CC5B96A9D321B0                       ntfs       iPad
/dev/sda6        ed8b5f14-3932-444d-8d2c-fbae73dafc3d   ext4       New Volume
/dev/sdb1        1E4D-C24F                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/1E4D-C24F         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------

default vesamenu.c32
timeout 100

menu background splash.jpg
menu title Welcome to Linux Mint 11 32-bit
menu color border 0 #00eeeeee #00000000
menu color sel 7 #ffffffff #33eeeeee
menu color title 0 #ffeeeeee #00000000
menu color tabmsg 0 #ffeeeeee #00000000
menu color unsel 0 #ffeeeeee #00000000
menu color hotsel 0 #ff000000 #ffffffff
menu color hotkey 7 #ffffffff #ff000000
menu color timeout_msg 0 #ffffffff #00000000
menu color timeout 0 #ffffffff #00000000
menu color cmdline 0 #ffffffff #00000000
menu hidden
menu hiddenrow 6
label live
menu label Start Linux Mint
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz quiet splash --
menu default
label xforcevesa
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/mint.seed boot=casper xforcevesa initrd=/casper/initrd.lz ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
label check
menu label Check the integrity of the DVD
kernel /casper/vmlinuz
append noprompt boot=casper integrity-check initrd=/casper/initrd.lz quiet splash --
label memtest
menu label Memory Test
kernel memtest
label local
menu label Boot from local drive
localboot 0x80
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by kiran_viswm on 2011-11-22
I formatted that Ext4 and now the GRUB is lost!!!

---

### Post by westie457 on 2011-11-22
```
Drive: sda __________________________________________________ ___________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 63 80,324 80,262 de Dell Utility
/dev/sda2 * 81,920 29,048,831 28,966,912 7 NTFS / exFAT / HPFS
/dev/sda3 29,048,832 202,174,463 173,125,632 7 NTFS / exFAT / HPFS
/dev/sda4 202,178,025 625,135,615 422,957,591 f W95 Extended (LBA)
/dev/sda5 202,178,088 329,734,124 127,556,037 7 NTFS / exFAT / HPFS
/dev/sda6 329,746,432 415,426,559 85,680,128 83 Linux
Invalid MBR Signature found.
Empty Partition.
```

It is not as bad as first thoughts suggested.
The partitions are still there. The MBR has been corrupted.
Testdisk available from the repositories is probably the best solution for you to recover the MBR. It is also available [here]("http://www.cgsecurity.org/wiki/TestDisk") also with complete instructions.

By all means wait for confirmation of this advice if you are not sure what to do

---

### Post by westie457 on 2011-11-22
> **kiran_viswm said:**
> I formatted that Ext4 and now the GRUB is lost!!!

Did you format the whole drive?

---

