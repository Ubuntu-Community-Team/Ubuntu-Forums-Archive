---
title: "Dual booting issues"
date: 2014-11-16
forum: New to Ubuntu
---

### Post by thomasvisco on 2014-11-16
Hi y'all,

I'm attempting to install unbutu along with my windows 7 install. Installation went fine on the individual partitions and what not. My issue is that the grub menu did not show up after the initial restart upon installation and is still not showing up. 

I've tried using gpart to change which parition is booting, but all that does is boot straight to the unbutu usb install menu. 

Any guidance y'all could offer would be great. I'm entirely new to linux, and I've been struggling with it all night. 

RESULTS from boot info script pasted below: 

                     ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 129 for .
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
    Boot sector info:  According to the info in the boot sector, sda2 has 
                       390624992 sectors, but according to the info from 
                       fdisk, it has 423131615 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

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
    Operating System:  Ubuntu 14.10
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 30478 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The 2 ADV sectors are not the same 
                       (corrupt). No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2    *        206,848   423,338,463   423,131,616   7 NTFS / exFAT / HPFS
/dev/sda3         423,340,030   547,016,703   123,676,674   5 Extended
/dev/sda5         442,871,808   462,401,535    19,529,728  82 Linux swap / Solaris
/dev/sda6         423,340,032   442,871,807    19,531,776  83 Linux
/dev/sda7         462,403,584   547,016,703    84,613,120  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3.7 GiB, 4004511744 bytes, 7821312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     7,821,311     7,821,280   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        18FEDB48FEDB1D36                       ntfs       System Reserved
/dev/sda2        66E8DC36E8DC0669                       ntfs       
/dev/sda5        eedd05f3-e836-4565-8a33-7295378e420b   swap       
/dev/sda6        d59e2366-3d59-4ee9-a1f2-7d3944e9f50e   ext4       
/dev/sda7        7e4376cf-a7af-4474-8c28-4617f8c379f1   ext4       
/dev/sdb1        1D10-4253                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev             /mnt/boot-sav/sda6/dev   none       (rw,bind)
/dev/pts         /mnt/boot-sav/sda6/dev/pts none       (rw,bind)
/dev/sda6        /mnt/boot-sav/sda6       ext4       (rw)
/dev/sda7        /mnt/boot-sav/sda7       ext4       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=d59e2366-3d59-4ee9-a1f2-7d3944e9f50e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7e4376cf-a7af-4474-8c28-4617f8c379f1 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=eedd05f3-e836-4565-8a33-7295378e420b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such device or address
hexdump: /dev/sda3: No such device or address
cat: /tmp/BootInfo-8ZRWVlcZ/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-8ZRWVlcZ/Tmp_Log: No such file or directory
  No volume groups found
```

---

### Post by thomasvisco on 2014-11-16
I've run boot-repair and get this error message "Please enable a repository containing the [linux] packages in the software sources of Ubuntu 14.10 (sda6). Then try again."

---

### Post by yancek on 2014-11-16
I see a mention of a wubi install with files on sda2, your windows partition.  Your fstab file shows that ubuntu installed the filesystem on sda6 but it doesn't show the standard files which should be there.  You also don't have the Grub files, most particularly the grub.cfg file which is your boot menu.  This means Grub did not install properly.  Which Ubuntu release are you using?  The link below explains some options you can use to repair the system and install Grub.

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by thomasvisco on 2014-11-16
I'm using ubuntu 14.10.

I used gpart to boot back from my Windows/NTFS partition, but now upon boot it brings me to a grub> command line.

I used the instructions to install grub via the termina. I get Installation finished. No error reported.

So I used gparted to change the boot partition back to my ubuntu install, but I get the same grub> command line.

the full screen says:

GNU GRUB version 2.02`beta2-15

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

Any ideas?

---

### Post by yancek on 2014-11-16
Your output doesn't show any Ubuntu installation and it does not show any boot files for Grub and no grub.cfg (Grub menu).  I don't know what happened but I think you will have to reinstall because the first one obviously did not work.

---

### Post by oldfred on 2014-11-16
Please use code tags on longer text output.

If Ubuntu fully install and just grub did not install, you may be able to use Boot-Repairs advanced mode and the full uninstall/reinstall of grub. But Internet has to be working for the system to download new grub packages.

Otherwise a full new install using Something Else to reuse existing partitions. Otherwise you may overwrite entire system or create still another install.

Does live installer work ok in live mode?

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

