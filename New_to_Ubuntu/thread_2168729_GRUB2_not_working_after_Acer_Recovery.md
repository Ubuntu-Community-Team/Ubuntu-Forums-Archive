---
title: "GRUB2 not working after Acer Recovery"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by F8rwMmQ on 2013-08-19
Hi guys, I have the same problem as with the guys in this thread:

[http://ubuntuforums.org/showthread.php?t=1836303](http://ubuntuforums.org/showthread.php?t=1836303)

However, the thread is already closed so I decided to make a new thread instead.

I have both Windows 7 and Ubuntu 12.04 in different partitions in my hard drive. I accidentally ran Acer's Recovery thing, as it was right next to the Windows 7 option in the Grub bootloader. After exiting the recovery thing, My laptop now boots to a "error: no partition." in grub rescue.

To diagnose the problem, I loaded Ubuntu using a 12.04 Ubuntu CD on 'try Ubuntu'. The guys in the thread said to use bootinfoscript:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and they were able to help the OP using the RESULTS.txt output. This is my RESULTS.txt output:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

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
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    28,674,047    28,672,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     28,674,048    28,878,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          28,878,848 1,269,845,650 1,240,966,803   7 NTFS / exFAT / HPFS
/dev/sda4       1,269,846,014 1,465,147,391   195,301,378   5 Extended
/dev/sda5       1,448,701,952 1,465,147,391    16,445,440  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E23C18B13C188329                       ntfs       PQSERVICE
/dev/sda2        1A90622890620B19                       ntfs       SYSTEM RESERVED
/dev/sda3        86726E68726E5D45                       ntfs       ACER
/dev/sda5        94644d12-5908-4cac-9c25-fbb3636a73c3   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.2 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 20  a9 0a 00 f0 fa 00 00 00  |....... ........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt



```

Can you guys help me with understanding the results? What are the next steps for me in order to make GRUB run again?

---

### Post by westie457 on 2013-08-19
Hi welcome to the forum.

The short answer is 'reinstall'.
Your Linux partition has been wiped and Grub has gone as well.

The long answer is to use a LiveCD\USB in Try mode. Open the Software Centre, search for and install Testdisk.
Open a terminal and run ```
sudo testdisk
```
Follow the prompts to search for deleted partitions and recover them.

This will find the old partitions however there is no guarantee that all of the files will be recovered at the same time because some of them will have been written over by the Windows\Acer Recovery process.

Hope this helps.

---

### Post by oldfred on 2013-08-19
If you exited the recovery process quickly, it was just the rewrite of the partition table which deleted the Linux partition in the extended partition. Testdisk then should be able to recover that. I would try that before the reinstall. If you resized several times testdisk may show multiple Linux partitions of slightly different sizes, probably only one is correct and it may be difficult to tell which is correct unless you know you start & size of your root partition.

You probably should remove the recovery from you grub menu.

---

### Post by DerpishCat on 2013-08-19
> **oldfred said:**
> You probably should remove the recovery from you grub menu.
As I understood it, it's being next to the boot option, before getting to the grub menu.
Where you'd choose what harddrive to boot from.

---

### Post by oldfred on 2013-08-19
Some systems it will be a BIOS entry or maybe a key board entry. 
But grub usually adds an entry also if it sees boot files in a partition. Somehow it knows it is not all the boot files and calls it recovery, but sometimes it makes mistakes on assumptions.

---

