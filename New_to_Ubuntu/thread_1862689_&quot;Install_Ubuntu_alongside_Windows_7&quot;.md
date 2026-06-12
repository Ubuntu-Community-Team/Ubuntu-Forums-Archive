---
title: "&quot;Install Ubuntu alongside Windows 7&quot;"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Nubiee on 2011-10-17
Hello there community.
This is my first post weeeew!! :popcorn:

Okay so here is it, with the new release of Ubuntu 11.10 i said to my self . . . Hmmm this looks interesting, it's been a long time since the last time i tried Ubuntu, let's give it a shot. So i immediately downloaded it and created a bootable USB with Ubuntu 11.10. 
Now after a few days i've tried so many things that i don't even remember what i've done :D and i still cannot get the boot loader to show me a dual booting option to choose Ubuntu or Windows 7. 
Before this i had dual boot Windows 7 (Dummy OS + Real proper locked down OS) but i wanted to give Ubuntu a try and formatted my dummy OS. After reinstalling Ubuntu countless times and formatting the partition i've came up to the conclusion that i just cannot do it without you guys ;)

Before registering here i created a thread on another forum i visit a lot and they recommended me to run a few commands on terminal to get some information about my partition but they just couldn't help since the UNIX community there is almost non existent, so here i am.

PARTED L
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500AAKS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   88.0GB  87.9GB  primary   ntfs
 3      88.0GB  169GB   80.5GB  extended               lba
 5      88.0GB  169GB   80.5GB  logical   ext4
 4      169GB   250GB   81.5GB  primary   ntfs


Model: ATA WDC WD400BB-00DE (scsi)
Disk /dev/sdb: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  ntfs         boot


Model: Kingston DT 101 II (scsi)
Disk /dev/sdc: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2004MB  2004MB  fat16


Error: /dev/sr0: unrecognised disk label   
```

FDISK L
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf968a70e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   171968511    85880832    7  HPFS/NTFS/exFAT
/dev/sda3       171970558   329254911    78642177    f  W95 Ext'd (LBA)
/dev/sda4       329254912   488392703    79568896    7  HPFS/NTFS/exFAT
/dev/sda5       171970560   329254911    78642176   83  Linux

Disk /dev/sdb: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x25ad25ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    78140159    39070048+   7  HPFS/NTFS/exFAT

Disk /dev/sdc: 2003 MB, 2003795968 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3913664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdc2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdc3   ?           0           0           0   6f  Unknown
/dev/sdc4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order
```

This is what i did over there, if there is anything else i need to do just tell me.

Basically my main problem is that i cannot get the boot loader to dual boot Windows 7 and Ubuntu. When i install Ubuntu i do NOT get the option to install alongside Windows 7 so i always use the something else mode which results in my PC booting directly to Windows 7 as if there was nothing installed. Any suggestions?

[http://imageshack.us/photo/my-images/838/screenshotat20111016023.png/](http://imageshack.us/photo/my-images/838/screenshotat20111016023.png/)

Really Thankies
Nubiee :KS

---

### Post by Quackers on 2011-10-17
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by Rubi1200 on 2011-10-17
+1 to the boot info script suggested by Quackers as it will hopefully help us determine what is going on.

And welcome to the forums :-)

---

### Post by Nubiee on 2011-10-18
```
    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 319151432 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 512 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   171,968,511   171,761,664   7 NTFS / exFAT / HPFS
/dev/sda3         171,970,558   329,254,911   157,284,354   f W95 Extended (LBA)
/dev/sda5         171,970,560   329,254,911   157,284,352  83 Linux
/dev/sda4         329,254,912   488,392,703   159,137,792   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40019582464 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78163247 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        B6E8AE22E8ADE13B                       ntfs       System Reserved
/dev/sda2        4AD29568D2955951                       ntfs       
/dev/sda4        980055FC0055E234                       ntfs       
/dev/sda5        c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e   ext4       
/dev/sdb1        EC642F39642F05C4                       ntfs       
/dev/sdc         86EF-8F12                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc         /cdrom                   vfat        (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,umask=0077,uhelper=udisks)


=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root B6E8AE22E8ADE13B
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root EC642F39642F05C4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

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
UUID=c25ed753-92e0-46a9-a6fe-e4d9ead4dd3e /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sdc/boot/grub/grub.cfg: ============================

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================== sdc/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option  to install or run from USB at startup, remove # from the following  line. This line was commented out (by request of many) to allow the old  menu to be presented and to enable booting straight into the Live  Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

==================== sdc: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================== sdc: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdc: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Here is it, i hope we can get it for today so i start enjoying and learning Ubuntu!! :popcorn:

---

### Post by vasa1 on 2011-10-18
> **Nubiee said:**
> ...
Here is it, i hope we can get it for today so i start enjoying and learning Ubuntu!! :popcorn:

Thought we lost you :D

(The same vasa1)

---

### Post by Quackers on 2011-10-18
You appear to have installed grub to the /dev/sda5 partition. Grub needs to be in the mbr of the drive (not a partition) to show a grub menu that you can boot different OSes from.

Firstly I would suggest that you create a set of recovery dvd's of your Windows system and a Windows repair disc.
It is possible that you may need one of them at some time.

To put grub in the mbr of the hard drive (presumably /dev/sda if that is the drive you are booting from) please boot from the Ubuntu live cd/usb (if you can't boot the installed Ubuntu system) and select "try Ubuntu".
When the desktop loads please open up a terminal and copy/paste these commands in one at a time, pressing enter after each line
```
sudo mount /dev/sda5 /mnt  
sudo grub-install --boot-directory=/mnt /dev/sda
``` which should report "Finished. No errors".
Then reboot and you should boot into Ubuntu directly. if so, open up a terminal again and run ```
sudo update-grub
``` and watch as grub.cfg is run. You should see the Windows Loader recognised. If so, reboot and you should then get a shiny new grub menu giving you the choice of which system to boot.

---

### Post by Nubiee on 2011-10-18
> **Quackers said:**
> You appear to have installed grub to the /dev/sda5 partition. Grub needs to be in the mbr of the drive (not a partition) to show a grub menu that you can boot different OSes from.

Firstly I would suggest that you create a set of recovery dvd's of your Windows system and a Windows repair disc.
It is possible that you may need one of them at some time.

To put grub in the mbr of the hard drive (presumably /dev/sda if that is the drive you are booting from) please boot from the Ubuntu live cd/usb (if you can't boot the installed Ubuntu system) and select "try Ubuntu".
When the desktop loads please open up a terminal and copy/paste these commands in one at a time, pressing enter after each line
```
sudo mount /dev/sda5 /mnt  
sudo grub-install --boot-directory=/mnt /dev/sda
``` which should report "Finished. No errors".
Then reboot and you should boot into Ubuntu directly. if so, open up a terminal again and run ```
sudo update-grub
``` and watch as grub.cfg is run. You should see the Windows Loader recognised. If so, reboot and you should then get a shiny new grub menu giving you the choice of which system to boot.
I'm gonna try it immediately when i'm at home. :p

> **vasa1 said:**
> Thought we lost you :D
(The same vasa1)
Hey Vasa1!!
Of course not, i never give up so easily (But i do get bored) ;)

---

### Post by Nubiee on 2011-10-19
I never thought this would screw up my PC and guess what i didn't make a backup HAHAHAHAHA
After i tried this my just won't boot naymore, had to reformat with Windows :p

---

