---
title: "Windows 7 dual boot problem"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by ExpDisease on 2011-10-01
I have windows 7 installed, I'm trying to install ubuntu 11.04 with manual partitioning i create partitions for /,home,boot,swap and giving the bootloader installation to sda0(Entire HDD I think). 

But grub doesn't appear. Then I reinstalled 11.04 with the bootloader option to the partition of the boot but grub doesn't appear. 

What am I doing wrong ?

---

### Post by coffeecat on 2011-10-01
Welcome to the forum.

First thing, "sda0" has no meaning. The first drive itself is referred to as sda. The first partition on the first drive is sda1, the second sda2, and so on. You need to install grub to /dev/sda. This is the default in the installer, so don't do anything to change the grub installation. This puts the first part of the grub code on the drive mbr, replacing the Windows mbr. Don't worry about replacing the Windows mbr. If you ever need to revert your machine to a Windows single-boot, it is very easy to re-install the Windows mbr with the Windows installation disc, and if you do not have a Windows installation disc, it is equally easy to reinstall code for Windows booting with an Ubuntu live CD.

Don't install grub to the boot partition, and above all do not install grub to the Windows partition otherwise you will render Windows unbootable and you would need a Windows installation disc to repair that.

You may not have to re-install Ubuntu as you are now. Hopefully, you will need only to re-install grub from the live CD. So that we can see what your setup is like now, and what you would need to do, boot up with the Ubuntu live CD, choose "try Ubuntu", and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and then post the contents of your RESULTS.txt file between [noparse]```
 and [/noparse]
``` tags for legibility.

---

### Post by Prince Valiant on 2011-10-01
Hello!

Personally, I've not found it necessary to install Ubuntu with a separate bootloader partition.  Just have GRUB install to sda.  I think that's an unnecessary complication to have more than swap, Ubuntu, and Windows partitions.  

That's the other thing: I'm pretty sure that 'sda0' is just another partition, and you want to install to 'sda'.  I could be wrong.  

If you don't mind installing again, I'd recommend that you use GParted (comes with the Ubuntu live install) to erase the bootloader, home, and / partitions (i.e., start with a clean slate), and then reinstall with GRUB being installed to the HDD.  There should be a clear indication of that option in the installation process.  

Hope this helps!  I've done a lot of Ubuntu reinstallations (at least, I think so), and this is the best I can think of.  

Have fun!
-Val

---

### Post by ExpDisease on 2011-10-01
While i opened the topic i installed 11.04 with the option "Install ubuntu with win 7 side by side" so i did nothing about the bootloader but still it doesn't see the grub. Here's the text results of the sh file

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......G..V...0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1445088 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   375,597,055   375,390,208   7 NTFS / exFAT / HPFS
/dev/sda3         375,599,102   933,466,111   557,867,010   f W95 Extended (LBA)
/dev/sda5         375,599,104   654,531,583   278,932,480   7 NTFS / exFAT / HPFS
/dev/sda6         654,532,608   925,118,463   270,585,856  83 Linux
/dev/sda7         925,120,512   933,466,111     8,345,600  82 Linux swap / Solaris
/dev/sda4         933,466,112   976,769,023    43,302,912  27 Hidden NTFS (Recovery Environment)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AC341C50341C203E                       ntfs       SYSTEM
/dev/sda2        F8008E41008E06BA                       ntfs       
/dev/sda4        889E33BD9E33A29C                       ntfs       SAMSUNG_REC
/dev/sda5        C6B84DE7B84DD699                       ntfs       DiseasedBackup
/dev/sda6        647590d5-67aa-431a-8055-d63a5bbc2422   ext4       
/dev/sda7        6c5fbc60-9f9c-46c1-ba94-2e339b6ef361   swap       
/dev/sdb1        06D7-7E1E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=647590d5-67aa-431a-8055-d63a5bbc2422 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=647590d5-67aa-431a-8055-d63a5bbc2422 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 647590d5-67aa-431a-8055-d63a5bbc2422
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root AC341C50341C203E
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 889E33BD9E33A29C
    drivemap -s (hd0) ${root}
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=647590d5-67aa-431a-8055-d63a5bbc2422 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6c5fbc60-9f9c-46c1-ba94-2e339b6ef361 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 320.268623352 = 343.885815808  boot/grub/grub.cfg                             1
 313.797386169 = 336.937377792  boot/initrd.img-2.6.38-8-generic               1
 364.238285065 = 391.097880576  boot/vmlinuz-2.6.38-8-generic                  1
 313.797386169 = 336.937377792  initrd.img                                     1
 364.238285065 = 391.097880576  vmlinuz                                        1

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

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by coffeecat on 2011-10-01
I don't know why grub wasn't installed to the mbr - that's most unusual. You still have the Windows bootloader in the mbr. Easily fixed. Fortunately you don't have a separate boot partition, which makes things easier. Boot up the Ubuntu live 11.04 CD or USB and choose "try Ubuntu". Open a terminal, and run these two commands:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and you should see the grub menu from your hard drive Ubuntu installation complete with entries for Windows and the Windows recovery partition. You might want to avoid choosing the recovery option.

Let us know how you get on.

---

### Post by ExpDisease on 2011-10-01
Thank god it worked :D. Before I read your post i installed boot repair and use recommended repair. Then I saw your post and without testing boot-repair worked i used your solution. One more question can boot-repair broke windows 7. I loaded window 7 without problems but I don't know anything more

---

### Post by coffeecat on 2011-10-01
What is "boot-repair"? Is that a Windows program?

---

### Post by Blasphemist on 2011-10-01
I'm really quite surprised this is working now. Please post a url for us to see from boot-repair's summary. I can't tell for sure from the bootinfoscript results but I thought this looked like there were dynamic partitions. 

Are both ubuntu and windows now booting successfully?

---

### Post by Blasphemist on 2011-10-01
> **coffeecat said:**
> What is "boot-repair"? Is that a Windows program?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coffeecat on 2011-10-01
> **Blasphemist said:**
> I'm really quite surprised this is working now. Please post a url for us to see from boot-repair's summary. I can't tell for sure from the bootinfoscript results but I thought this looked like there were dynamic partitions. 

There are no dynamic partitions in the boot script output.

---

### Post by coffeecat on 2011-10-01
Sorry - I was trying to deal with other things at the same time. I should have added that dynamic partitions usually show "SFS" where the OP's bootscript output (fdisk) shows "NTFS / exFAT / HPFS" for the NTFS partitions.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   375,597,055   375,390,208   7 NTFS / exFAT / HPFS
/dev/sda3         375,599,102   933,466,111   557,867,010   f W95 Extended (LBA)
/dev/sda5         375,599,104   654,531,583   278,932,480   7 NTFS / exFAT / HPFS
/dev/sda6         654,532,608   925,118,463   270,585,856  83 Linux
/dev/sda7         925,120,512   933,466,111     8,345,600  82 Linux swap / Solaris
/dev/sda4         933,466,112   976,769,023    43,302,912  27 Hidden NTFS (Recovery Environment)

```

---

### Post by ExpDisease on 2011-11-14
Hi

Today I installed ubuntu 11.10 to my external drive and I had the same problem that win7 is starting without showing grub. bootinfo gave this output.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

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
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab

sdb4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30460 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   325,591,039   325,384,192   7 NTFS / exFAT / HPFS
/dev/sda3         325,591,040   976,769,023   651,177,984   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda121 4,064,890,282,601,682,330302,946,552,007,129,646-3,761,943,730,594,552,683 -
/dev/sda122 982,667,620,801,759,4852,866,294,309,786,758,9661,883,626,688,984,999,482 -
/dev/sda123 2,649,587,237,047,147,9703,017,793,047,432,984,721368,205,810,385,836,752 -
/dev/sda124 1,818,710,556,321,286,1182,513,874,884,735,595,418695,164,328,414,309,301 -

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   312,581,807   312,581,807  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34     1,000,034     1,000,001 Data partition (Windows/Linux)
/dev/sdb2       1,000,035    17,000,035    16,000,001 Swap partition (Linux)
/dev/sdb3      17,000,036   163,484,411   146,484,376 Data partition (Windows/Linux)
/dev/sdb4     163,484,412   312,580,115   149,095,704 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders, total 7823296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             62     7,818,695     7,818,634   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6ED6677AD6674187                       ntfs       Sistem Ayr&#305;ld&#305;
/dev/sda2        1ED06CB1D06C90B7                       ntfs       
/dev/sda3        9C46FABC46FA966C                       ntfs       DiseasedBackup
/dev/sdb1        47acfc90-5ba4-422b-b4c6-ff45089a3a46   ext4       
/dev/sdb2        6b26ca9a-6fc5-47c0-9f11-60fdb734ddd4   swap       
/dev/sdb3        f28449b7-5e23-4de4-92dc-3d95228a8b91   ext4       
/dev/sdb4        9f4054ef-d450-4d24-836e-898c6a787f9a   ext4       
/dev/sdc1        15DB-1E3A                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/47acfc90-5ba4-422b-b4c6-ff45089a3a46 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb3        /media/f28449b7-5e23-4de4-92dc-3d95228a8b91 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb4        /media/9f4054ef-d450-4d24-836e-898c6a787f9a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sdb1/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd2,gpt3)'
search --no-floppy --fs-uuid --set=root f28449b7-5e23-4de4-92dc-3d95228a8b91
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd2,gpt1)'
  search --no-floppy --fs-uuid --set=root 47acfc90-5ba4-422b-b4c6-ff45089a3a46
  set locale_dir=($root)/grub/locale
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
    insmod part_gpt
    insmod ext2
    set root='(hd2,gpt1)'
    search --no-floppy --fs-uuid --set=root 47acfc90-5ba4-422b-b4c6-ff45089a3a46
    linux    /vmlinuz-3.0.0-12-generic root=UUID=f28449b7-5e23-4de4-92dc-3d95228a8b91 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd2,gpt1)'
    search --no-floppy --fs-uuid --set=root 47acfc90-5ba4-422b-b4c6-ff45089a3a46
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=f28449b7-5e23-4de4-92dc-3d95228a8b91 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd2,gpt1)'
    search --no-floppy --fs-uuid --set=root 47acfc90-5ba4-422b-b4c6-ff45089a3a46
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd2,gpt1)'
    search --no-floppy --fs-uuid --set=root 47acfc90-5ba4-422b-b4c6-ff45089a3a46
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 6ED6677AD6674187
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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.0.0-12-generic                    3
               =                vmlinuz-3.0.0-12-generic                       1

=============================== sdb3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc3 during installation
UUID=f28449b7-5e23-4de4-92dc-3d95228a8b91 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc1 during installation
UUID=47acfc90-5ba4-422b-b4c6-ff45089a3a46 /boot           ext4    defaults        0       2
# /home was on /dev/sdc4 during installation
UUID=9f4054ef-d450-4d24-836e-898c6a787f9a /home           ext4    defaults        0       2
# swap was on /dev/sdc2 during installation
UUID=6b26ca9a-6fc5-47c0-9f11-60fdb734ddd4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

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

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
d441a0f50300030039a41d02f492a954
Unknown GPT Partiton Type
09ca7e9bed54551e61eb4a59af21137c
Unknown GPT Partiton Type
5aa6fe622ae3697995c40c6ce1e720ab
Unknown GPT Partiton Type
34f6504e6d2a906157bc02bbf60bdb28

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

