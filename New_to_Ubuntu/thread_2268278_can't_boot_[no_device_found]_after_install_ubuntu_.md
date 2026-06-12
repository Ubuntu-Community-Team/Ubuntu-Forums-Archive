---
title: "can't boot [no device found] after install ubuntu dual boot on windows 7"
date: 2015-03-07
forum: New to Ubuntu
---

### Post by nick176 on 2015-03-07
hello,

this is my first time trying to install ubuntu and i got stuck.

i was installing ubuntu dual boot on windows 7 64 bit home to sony vaio svt13112fxs from iso usb.

after installation successful, i tried to restart the laptop... there said only no device found, entering rescue mode, grub rescue>.

i can use live usb to start ubuntu on usb, and i still see all partitions and files, but when i try to restore windows with startup disk, it sees no drive...

all "F#" button cannot trigger windows.

please help.

thank you.

---

### Post by nick176 on 2015-03-07
now... even i want to reinstall ubuntu, i cannot see any drive in the "installation type" page...

---

### Post by Mark Phelps on 2015-03-07
Just so we can see what's there, boot from the Ubuntu LiveUSB, select the Try option, open a terminal and enter "sudo fdisk 'lu" (lowercase L, not a one).  This will list out the partitions on the drive.

---

### Post by nick176 on 2015-03-07
this is what i got...

----------
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x13c4a646

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  27934719  27932672  13.3G 27 Hidden NTFS WinRE
/dev/sda2  *     27934720  28651519    716800   350M  7 HPFS/NTFS/exFAT
/dev/sda3        28651520 771966975 743315456 354.5G  7 HPFS/NTFS/exFAT
/dev/sda4       771966976 976764927 204797952  97.7G  f W95 Ext'd (LBA)
/dev/sda5       771969024 976764927 204795904  97.7G  7 HPFS/NTFS/exFAT

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9cb32413

Device     Boot    Start      End  Sectors  Size Id Type
/dev/sdb1           2048 23519231 23517184 11.2G 84 OS/2 hidden C: drive
/dev/sdb2       23521278 62531583 39010306 18.6G  5 Extended
/dev/sdb5  *    23521280 54345727 30824448 14.7G 83 Linux
/dev/sdb6       54347776 62531583  8183808  3.9G 82 Linux swap / Solaris

Disk /dev/sdc: 15.1 GiB, 16228810752 bytes, 31696896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc3072e18

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *    18192 31696895 31678704 15.1G  c W95 FAT32 (LBA)

---

### Post by yancek on 2015-03-07
The only Linux partition you have is sdb5 so where did you install the Ubuntu Grub bootloader, which drive?  Which drive is set to frist boot priority?  You might do an online search for 'boot repair' and download it to your Ubuntu instalation medium and run it, select the option to Create BootInfo Summary and post it here.

---

### Post by nick176 on 2015-03-07
here from the boot-info first 2 sections...

----------
============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 844c6378-943a-45b8-83b7-295a0f2636a3 root hd1,msdos5 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 61808 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,934,719    27,932,672  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,934,720    28,651,519       716,800   7 NTFS / exFAT / HPFS
/dev/sda3          28,651,520   771,966,975   743,315,456   7 NTFS / exFAT / HPFS
/dev/sda4         771,966,976   976,764,927   204,797,952   f W95 Extended (LBA)
/dev/sda5         771,969,024   976,764,927   204,795,904   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    23,519,231    23,517,184  84 OS/2 hidden C: drive
/dev/sdb2          23,521,278    62,531,583    39,010,306   5 Extended
/dev/sdb5    *     23,521,280    54,345,727    30,824,448  83 Linux
/dev/sdb6          54,347,776    62,531,583     8,183,808  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 15.1 GiB, 16228810752 bytes, 31696896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *         18,192    31,696,895    31,678,704   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:                                                   
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:1 F01077A110776E0A                       ntfs       Recovery
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:2 600EA7910EA75F32                       ntfs       System Reserved
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:3 D236A8EC36A8D2B1                       ntfs       
/dev/mapper/isw_dihbjgbhcj_71AT5921ZGSKGVXY\x87N8:5 8674890E74890263                       ntfs       Ubuntu
/dev/sda1        F01077A110776E0A                       ntfs       Recovery
/dev/sda2        600EA7910EA75F32                       ntfs       System Reserved
/dev/sda3        D236A8EC36A8D2B1                       ntfs       
/dev/sda5        8674890E74890263                       ntfs       Ubuntu
/dev/sdb1                                                          
/dev/sdb5        844c6378-943a-45b8-83b7-295a0f2636a3   ext4       
/dev/sdb6        bba22369-8f67-4110-9a05-797ef3ab8a82   swap       
/dev/sdc1        1D13-2124                              vfat       UUI

---

