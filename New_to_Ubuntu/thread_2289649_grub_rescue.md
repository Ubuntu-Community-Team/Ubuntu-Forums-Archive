---
title: "grub rescue"
date: 2015-08-05
forum: New to Ubuntu
---

### Post by jgedri on 2015-08-05
Hello. I just got reacquainted with GRUB Rescuce today. Could really use some help.

First of all, what commands does it accept? It obviously doesn't know 'help', so hopefully this forum will be more forthcoming.

Second, the problem occurred after I'd created new partitions on my hard drive and memory stick. I had just gotten Windows to boot again, so this is rather discouraging. 

What happened was, I got frustrated with Gparted and deleted the partition I'd installed Ubuntu on. I reinstalled Ubuntu, then loaded Windows and created a new partition. To make a long story short, I'm now running a live USB and would very much like to be able to boot from my hard drive again.

---

### Post by yancek on 2015-08-05
The first step would be to indicat which version of windows you are using.  What do you mean by "loaded" windows?  Does that mean your also reinstalled it after reinstalling Ubuntu?  Post some info by using the Ubuntu Live USB and use GParted and post an image of your drives/partitions.  You may need to get the boot repair software to gather more info.

---

### Post by jgedri on 2015-08-05
I never uninstalled Windows 7. I just deleted Ubuntu and, presumably, the Grub entry that let me choose an OS. Okay, here's the report from boot-info-script.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 135 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

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
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /grldr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 12878688 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   428,427,076   425,353,029   7 NTFS / exFAT / HPFS
/dev/sda3         596,877,312   625,141,759    28,264,448  17 Hidden NTFS / HPFS
/dev/sda4         522,491,902   596,877,311    74,385,410   5 Extended
/dev/sda5         589,590,528   596,877,311     7,286,784  82 Linux swap / Solaris
/dev/sda6         576,317,440   589,576,191    13,258,752  83 Linux
/dev/sda7         522,491,904   576,315,391    53,823,488   b W95 FAT32


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 32.0 GB, 32015679488 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62530624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    62,530,623    62,530,592   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       2d9f8dbd-06cb-4897-af61-ab1cefe11c12   ext3       
/dev/sda1        C8A4DA57A4DA4798                       ntfs       System
/dev/sda2        FA4400B6440077A1                       ntfs       TI106166W0D
/dev/sda3        D8C61619C615F908                       ntfs       HDDRECOVERY
/dev/sda5        2830b657-47d1-48af-aba4-6d5560bda84d   swap       
/dev/sda6        f501ae22-e72d-46de-ae53-b903ac7fdb2a   ext4       ubuntu
/dev/sda7        35F1-7D3F                              vfat       DOCUMENTS
/dev/sdb1        4074-70B0                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/menu.lst: ================================

--------------------------------------------------------------------------------
###################################################### 
# GvR Sept 30th 2004 
    color black/cyan yellow/cyan 
    timeout=5 
    default=0 
 
title Default Boot on HD 0 
    rootnoverify (hd0,0) 
    chainloader +1 
    boot 
  
###################################################### 
 
--------------------------------------------------------------------------------

========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1

title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
    errorcheck off
    configfile /menu.lst
    configfile /boot/grub/menu.lst
    configfile /grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
    find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
    find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
    errorcheck on
    commandline

title commandline
    commandline

title reboot
    reboot

title halt
    halt


--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- cdrom-detect/try-usb=true noprompt persistent
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- cdrom-detect/try-usb=true noprompt persistent
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true -- cdrom-detect/try-usb=true noprompt persistent
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


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 d8  ff 03 00 30 6f 00 00 fe  |...........0o...|
000001d0  ff ff 05 fe ff ff a4 49  35 03 5e 56 ca 00 00 00  |.......I5.^V....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-KMJLvsUK/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-KMJLvsUK/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-KMJLvsUK/Tmp_Log: No such file or directory
  No volume groups found


```

---

### Post by oldfred on 2015-08-06
Changed quotes to code tags. Easy to add code tags with # in Forum Advanced Editor.

Script does not show grub.cfg, fstab, kernels or really anything in your Linux partition.
Just grub still in MBR.
It does not look like Ubuntu fully installed into sda6. 
If you have no data in it you want to save, may be easier to just reinstall with Something Else and click on change button when on sda6. It will auto find swap and you should be able to reinstall.

Your grub4dos & EasyBCD in Windows may be confusing things also.

---

### Post by jgedri on 2015-08-06
It confuses me, certainly. I've yet to find out what BCD stands for.

---

### Post by oldfred on 2015-08-06
Windows BCD - Boot Configuration Data 
(last Acronym entry in link in my signature below) :)

In Windows XP it was a simple boot.ini which was a simple text file you could edit.
They converted it to a "hive" where every entry has a different structure and all programs store configuration data in it. It just grows and get un-wieldy. And you have to use the Windows editor.

---

### Post by jgedri on 2015-08-06
Oh joy, one more reason to migrate to Linux!

Do you think you could direct me to a thread explaining what UEFI and secure boot are? Somebody?

---

### Post by Bashing-om on 2015-08-06
jgedri; Sure !

> **jgedri said:**
> Oh joy, one more reason to migrate to Linux!

Do you think you could direct me to a thread explaining what UEFI and secure boot are? Somebody?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
[https://iam.tj/kb/pc/boot/#a_bootloader](https://iam.tj/kb/pc/boot/#a_bootloader)


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-08-06
um, oldfred's signature has just about every useful link to UEFI you any need. :)
Although there now are many sites with good info.

---

### Post by jgedri on 2015-08-06
What's secure boot?

---

### Post by yancek on 2015-08-06
> What's secure boot? 		

Brief explanation at the site below.  You can google it and get a lot of sites with more detailed information.  It is basically an addition to UEFI for microsoft systems.

[http://www.techopedia.com/definition/28951/microsoft-secure-boot-windows-8](http://www.techopedia.com/definition/28951/microsoft-secure-boot-windows-8)

---

