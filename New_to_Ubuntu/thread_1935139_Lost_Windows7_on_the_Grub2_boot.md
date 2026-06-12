---
title: "Lost Windows7 on the Grub2 boot"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mrbaloob on 2012-03-03
Hi,

Can somebody pleasehelp me with mine. I lost Windows7 on the Grub2 boot. This is what the Result.txt shows :
Thanks in anticipation.

 ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda7 
                       and looks at sector 143521240 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /extlinux/extlinux.conf 
                       /grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    61,432,559    61,430,512   7 NTFS / exFAT / HPFS
/dev/sda2          61,442,048   103,647,356    42,205,309  83 Linux
/dev/sda3         103,649,278   156,296,384    52,647,107   f W95 Extended (LBA)
/dev/sda5         103,649,280   132,757,503    29,108,224  83 Linux
/dev/sda6         132,759,552   134,832,127     2,072,576  83 Linux
/dev/sda7         134,833,608   149,516,954    14,683,347  83 Linux
/dev/sda8         149,517,018   156,296,384     6,779,367  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        01CB9BCE0B9E67D0                       ntfs       
/dev/sda2        418aaa18-a29d-4729-93cc-9773e4e3d19d   ext4       
/dev/sda5        785970a0-4cbb-4832-9a1b-26e8624e8591   ext4       
/dev/sda6        5c799c83-769e-42cf-aacf-5191aec80076   ext4       
/dev/sda7        2a37fbbb-672d-493a-a813-ca505bab1a5d   ext4       
/dev/sda8        6181c882-c2bb-4e8e-ae9e-2eb8d72c6579   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)
/dev/sda7        /boot                    ext4       (rw,commit=0)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by oldos2er on 2012-03-03
Post moved to its own thread.

---

