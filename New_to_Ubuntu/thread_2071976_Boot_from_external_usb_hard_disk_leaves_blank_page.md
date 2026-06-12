---
title: "Boot from external usb hard disk leaves blank page"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Almax on 2012-10-16
Hello. 

I am trying to install (and did so) Ubuntu 12.04 on an external hard drive which I partitioned accordingly. My laptop is running on W.7, and I would rather not change anything on the OS or the partitioning system..that why I chose to install on an external HDD.

I partitioned the external HDD in a first ntfs partition, one for the ubuntu install and one for swap.

However even if the installation is complete and I set BIOS to boot from that external hard drive, when I boot all I get is a blank page and nothing happens. 

I tried to run Ubuntu on a live CD and ran boot-repair with the results that will be following. 



```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info October 12th 2012]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Hewlett-Packard/BIOSUpdate/CryptRSA.efi 
                       /Hewlett-Packard/BIOSUpdate/CryptRSA32.efi 
                       /Hewlett-Packard/BIOSUpdate/HpBiosUpdate.efi 
                       /Hewlett-Packard/BIOSUpdate/HpBiosUpdate32.efi 
                       /Hewlett-Packard/QuickWeb/CryptRSA.efi 
                       /Hewlett-Packard/QuickWeb/CryptRSA32.efi 
                       /Hewlett-Packard/SystemDiags/CryptRSA.efi 
                       /Hewlett-Packard/SystemDiags/CryptRSA32.efi 
                       /Hewlett-Packard/SystemDiags/SystemDiags.efi 
                       /Hewlett-Packard/SystemDiags/SystemDiags32.efi

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600   923,185,151   922,775,552   7 NTFS / exFAT / HPFS
/dev/sda3         923,185,152   968,450,047    45,264,896   7 NTFS / exFAT / HPFS
/dev/sda4         968,450,048   976,771,071     8,321,024   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,236,658,175 1,236,656,128   7 NTFS / exFAT / HPFS
/dev/sdc2       1,236,658,176 1,498,343,423   261,685,248   7 NTFS / exFAT / HPFS
/dev/sdc3    *  1,498,343,424 1,936,664,575   438,321,152  83 Linux
/dev/sdc4       1,936,664,576 1,953,458,175    16,793,600  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8AAAFA95AAFA7CCF                       ntfs       SYSTEM
/dev/sda2        1E4440CB4440A77D                       ntfs       
/dev/sda3        FCFA6F33FA6EE8FA                       ntfs       Recovery
/dev/sda4        5634-256A                              vfat       HP_TOOLS
/dev/sdc1        4E1AEA7B1AEA6007                       ntfs       My Passport
/dev/sdc2        385695255694E542                       ntfs       New Volume
/dev/sdc3        9bf0abb9-8db9-4f5f-9945-6aa52c04ee0e   ext2       
/dev/sdc4        56aee074-0a5f-43e0-bbae-80079f2c473f   swap       
/dev/sr0                                                iso9660    Ubuntu 12.04.1 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/My Passport       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc2        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc3        /media/9bf0abb9-8db9-4f5f-9945-6aa52c04ee0e ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdc3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

```

What should I do?

---

### Post by oldfred on 2012-10-16
Please use code tags. Highlight like a copy & click # in edit panel to automatically add them.

You did not post entire script. Better to post the link that BootInfo gives.

Do you get grub menu? Or from grub menu does it go blank/purple which may be a video issue.

---

### Post by Almax on 2012-10-17
Thank you for your reply, this is the link that I got:

[http://pastebin.ubuntu.com/1284016/](http://pastebin.ubuntu.com/1284016/)

I don't get anything, the screen is just blank, and I do not get any options. On an intuitive level I believe it has something to do with where I installed the boot loader (during the installation I installed it on the external HDD). It seems to me that when I boot the computer doesn't see anything to boot from.

---

### Post by oldfred on 2012-10-17
Usually grub gives an error message if it is grub. And grub found Windows so it sees two operating systems to boot and then should show menu.

With one system it skips menu and then could be a video issue or other boot parameter.

Just as a test, from BIOS screen where you check to boot from USB drive hold down shift key, that also should show menu.

We have seen on larger drives (maybe more so with USB drives?) an issue where if grub & boot files are far from the front of the drive it does not work. Only some systems. 
I am not sure if it is a BIOS setting, grub bug or maybe USB interface bug or some combination. We have some users that work without issue and others just do not. There was a BIOS issues years ago (over 6) where some IDE BIOS could not boot past 137GB.

---

