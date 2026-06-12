---
title: "fresh install, no grub menu"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by cliny on 2011-11-22
Hey guys,

I just installed ubuntu 64bit from a usb stick, alongside my already installed 64bit windows 7.

It installed fine, but when I turn the pc on it goes straight to windows, and there is no option to boot into linux.

Is there a *simple* fix to this?

---

### Post by sadaruwan12 on 2011-11-22
Welcome to the forum.

What option you selected when you where asked to partition the hard disk and please describe the you did when installing.

---

### Post by cliny on 2011-11-22
Thank you. I just slid the middle-bar thing so that there was about 50GB for the linux partition. When I look at the partitions via windows, theres a 43GB ext4 partition, and a 4GB swap partition.

Installing I followed most of the default options. Anything in particular you'd like to know?

---

### Post by sadaruwan12 on 2011-11-22
OK, now did you selected to install ubuntu along side windows. Any way if you've selected the defaults then there want be any issues but  it seems like the GRUB boot loader didn't got installed.

That s why you're getting pushed to the windows system. After installing ubuntu did you repaired your windows installation if you have done something like that then it might have over written the ubuntu boot loader.

The best and easy way to do this for you do a re-installation of the ubntu system.

---

### Post by fantab on 2011-11-22
> **cliny said:**
> Thank you. I just slid the middle-bar thing so that there was about 50GB for the linux partition. When I look at the partitions via windows, theres a 43GB ext4 partition, and a 4GB swap partition.

Installing I followed most of the default options. Anything in particular you'd like to know?

Any ideas?

Can you post a Screenshot of the HDD partions....?

And post the results from [**Boot Info Script**]("http://bootinfoscript.sourceforge.net/").

---

### Post by audiomick on 2011-11-22
> **sadaruwan12 said:**
> ... do a re-installation of the ubntu system.
It isn't that hard to just retrospectively install grub.

Do the business with the boot-info-script. This provides comprehensive info about what is actually on the machine. It will tell you if it is just grub that is missing, or if the install didn't work at a different level.

---

### Post by cliny on 2011-11-22
here's a screenshot of my partitions:
[http://i.imgur.com/f9RuZ.jpg](http://i.imgur.com/f9RuZ.jpg)

> Boot info script results:
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 1210097152 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 30478 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,151,106,555 1,150,899,708   7 NTFS / exFAT / HPFS
/dev/sda3       1,151,107,070 1,250,263,039    99,155,970   5 Extended
/dev/sda5       1,151,107,072 1,242,056,703    90,949,632  83 Linux
/dev/sda6       1,242,058,752 1,250,263,039     8,204,288  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4005 MB, 4005560320 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,823,359     7,823,297   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A64A97DD4A97A897                       ntfs       System Reserved
/dev/sda2        00AC9AC3AC9AB320                       ntfs       internal
/dev/sda5        d567845a-2812-4bf6-b1c6-6749322b583c   ext4       
/dev/sda6        0d3810ce-1b9c-4d05-8a43-08bb973909a9   swap       
/dev/sdb1        18E1-1869                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/internal          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
    search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d567845a-2812-4bf6-b1c6-6749322b583c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d567845a-2812-4bf6-b1c6-6749322b583c ro recovery nomodeset 
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
    search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root d567845a-2812-4bf6-b1c6-6749322b583c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root A64A97DD4A97A897
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
UUID=d567845a-2812-4bf6-b1c6-6749322b583c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0d3810ce-1b9c-4d05-8a43-08bb973909a9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic              11
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                    11
               =                vmlinuz                                        1

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

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

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

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected



Also, is YesWeCan's solution relevant?:
[http://ubuntuforums.org/showthread.php?t=1798230](http://ubuntuforums.org/showthread.php?t=1798230)

---

### Post by audiomick on 2011-11-22
You could just go ahead and try re-installing grub, but I would have a look at the results of the boot info script first. It looks daunting when you first look at it, but if you nut it out, it isn't that hard, actually. You would be looking for words like "grub is installed in xxx and looks for xxx at xxx". Post the output here, using code tags.

The method in this post from YesWeCan
[http://ubuntuforums.org/showpost.php?p=11020985&postcount=8](http://ubuntuforums.org/showpost.php?p=11020985&postcount=8)
should work, I think.

If you look here, it seems there is a graphical tool available. Perhaps you might want to look at that first.
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

Otherwise, there are several other methods there too.

---

### Post by cliny on 2011-11-22
I got a grub menu! I just installed and ran the app 'boot-repair'.

Cheers for all the help guys :)

---

### Post by audiomick on 2011-11-22
Cool thing! 

Did you mark the thread as solved? The button is in the "thread tools" drop-down menu.

---

