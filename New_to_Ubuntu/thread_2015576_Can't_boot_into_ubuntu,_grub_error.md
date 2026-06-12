---
title: "Can't boot into ubuntu, grub error"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by banda on 2012-07-03
I just installed ubuntu 12.04 on an external hard disk but grub was not configured properly dusring install so i have been unable to boot into ubuntu yet. 

I manually partitioned the external 1tb hard disk as follows --

970GB -- ntfs
200MB -- /boot
25GB  -- /
2GB   -- swap
3GB   -- unpartitioned

I tried using Boot-Repair but it did not fix the problem. Grub gives the error "no such partition", halts at gub recovery>

this is the info gathered by boot-repair -- [http://paste.ubuntu.com/1073568/](http://paste.ubuntu.com/1073568/)

```
           Boot Info Script 0.61-git      [15 June 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30542 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sdc7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    34,812,854    34,810,807  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     34,812,855   191,093,174   156,280,320   7 NTFS / exFAT / HPFS
/dev/sda3         191,093,175   625,137,344   434,044,170   f W95 Extended (LBA)
/dev/sda5         191,093,238   625,137,344   434,044,107   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             38     7,839,719     7,839,682   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204138496 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523708 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 1,894,533,297 1,894,531,250   7 NTFS / exFAT / HPFS
/dev/sdc2       1,894,535,166 1,947,662,335    53,127,170   5 Extended
/dev/sdc5       1,894,535,168 1,894,924,287       389,120  83 Linux
/dev/sdc6       1,894,926,336 1,943,752,703    48,826,368  83 Linux
/dev/sdc7       1,943,754,752 1,947,662,335     3,907,584  82 Linux swap / Solaris


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3C98-AC5D                              vfat       RECOVERY
/dev/sda2        E422537022534728                       ntfs       OS
/dev/sda5        9E0C01CADC9BBFD0                       ntfs       DATA
/dev/sdb1        1A15-0C10                              vfat       PENDRIVE
/dev/sdc1        8C5C95595C953F40                       ntfs       Hitachi
/dev/sdc5        b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b   ext4       
/dev/sdc6        93ff6b80-b975-47f1-817c-4f10227e2a5e   ext4       
/dev/sdc7        eb31e9ae-9d6a-4f18-b790-b82313724e91   swap       
/dev/sdd1        3E4E-9973                              vfat       8GB MICROSD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Hitachi           fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc5        /media/b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6        /media/93ff6b80-b975-47f1-817c-4f10227e2a5e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1        /media/8GB MICROSD       vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
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

============================= sdc5/grub/grub.cfg: ==============================

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
set root='(hd2,msdos6)'
search --no-floppy --fs-uuid --set=root 93ff6b80-b975-47f1-817c-4f10227e2a5e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos5)'
  search --no-floppy --fs-uuid --set=root b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
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
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
	linux	/vmlinuz-3.2.0-23-generic root=UUID=93ff6b80-b975-47f1-817c-4f10227e2a5e ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/vmlinuz-3.2.0-23-generic root=UUID=93ff6b80-b975-47f1-817c-4f10227e2a5e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3C98-AC5D
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root E422537022534728
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

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 903.398982048 = 970.017270784  grub/core.img                                  1
 903.396490097 = 970.014595072  grub/grub.cfg                                  1
 903.454607964 = 970.076998656  initrd.img-3.2.0-23-generic                    2
 903.405016899 = 970.023750656  vmlinuz-3.2.0-23-generic                       1

=============================== sdc6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=93ff6b80-b975-47f1-817c-4f10227e2a5e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdc5 during installation
#UUID=b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b /boot           ext4    defaults        0       2
# swap was on /dev/sdc7 during installation
UUID=eb31e9ae-9d6a-4f18-b790-b82313724e91 none            swap    sw              0       0
UUID=b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b	/boot	ext4	defaults	1	2
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  eb 58 90 46 52 44 4f 53  34 2e 31 00 02 10 20 00  |.X.FRDOS4.1... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 b7 d9 63 0b  |........?.....c.|
00000020  3b 8b 38 01 08 27 00 00  00 00 00 00 12 05 00 00  |;.8..'..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 f2 2c 9e 58 4e  4f 20 4e 41 4d 45 20 20  |..).,.XNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fc fa 29 c0 8e d8  |  FAT32   ..)...|
00000060  bd 00 7c b8 e0 1f 8e c0  89 ee 89 ef b9 00 01 f3  |..|.............|
00000070  a5 ea 7a 7c e0 1f 00 00  60 00 8e d8 8e d0 8d 66  |..z|....`......f|
00000080  e0 fb 88 56 40 be c1 7d  e8 f4 00 66 31 c0 66 89  |...V@..}...f1.f.|
00000090  46 44 8b 46 0e 66 03 46  1c 66 89 46 48 66 89 46  |FD.F.f.F.f.FHf.F|
000000a0  4c 66 8b 46 10 66 f7 6e  24 66 01 46 4c b8 00 02  |Lf.F.f.n$f.FL...|
000000b0  3b 46 0b 74 08 01 c0 ff  06 34 7d eb f3 66 8b 46  |;F.t.....4}..f.F|
000000c0  2c 66 50 e8 94 00 72 4d  c4 5e 76 e8 b7 00 31 ff  |,fP...rM.^v...1.|
000000d0  b9 0b 00 be f1 7d f3 a6  74 15 83 c7 20 83 e7 e0  |.....}..t... ...|
000000e0  3b 7e 0b 75 eb 4a 75 e0  66 58 e8 34 00 eb d2 26  |;~.u.Ju.fX.4...&|
000000f0  ff 75 09 26 ff 75 0f 66  58 29 db 66 50 e8 5a 00  |.u.&.u.fX).fP.Z.|
00000100  72 0d e8 80 00 4a 75 fa  66 58 e8 14 00 eb ec 8a  |r....Ju.fX......|
00000110  5e 40 ff 6e 76 be ee 7d  e8 64 00 30 e4 cd 16 cd  |^@.nv..}.d.0....|
00000120  19 06 57 53 89 c7 c1 e7  02 50 8b 46 0b 48 21 c7  |..WS.....P.F.H!.|
00000130  58 66 c1 e8 07 66 03 46  48 bb 00 20 8e c3 29 db  |Xf...f.FH.. ..).|
00000140  66 3b 46 44 74 07 66 89  46 44 e8 38 00 26 80 65  |f;FDt.f.FD.8.&.e|
00000150  03 0f 26 66 8b 05 5b 5f  07 c3 66 3d f8 ff ff 0f  |..&f..[_..f=....|
00000160  73 15 66 48 66 48 66 0f  b6 56 0d 66 52 66 f7 e2  |s.fHfHf..V.fRf..|
00000170  66 5a 66 03 46 4c c3 f9  c3 31 db b4 0e cd 10 ac  |fZf.FL...1......|
00000180  3c 00 75 f5 c3 52 56 57  66 50 89 e7 6a 00 6a 00  |<.u..RVWfP..j.j.|
00000190  66 50 06 53 6a 01 6a 10  89 e6 8a 56 40 b4 42 cd  |fP.Sj.j....V@.B.|
000001a0  13 89 fc 66 58 73 08 50  30 e4 cd 13 58 eb d9 66  |...fXs.P0...X..f|
000001b0  40 03 5e 0b 73 07 8c c2  80 c6 10 8e c2 5f 00 fe  |@.^.s........_..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 cb fc de 19 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-07-03__18h48 ===================
boot-repair version : 3.18-0ppa34~precise
boot-sav version : 3.19-0ppa84~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
boot-repair is executed in live-session (Ubuntu 12.04 LTS , precise , Ubuntu , x86_64)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sda1:Windows Recovery Environment (loader):Windows:chain
/dev/sda2:Windows 8 (loader):Windows1:chain
/dev/sdc6:Ubuntu 12.04 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="RECOVERY" UUID="3C98-AC5D" TYPE="vfat"
/dev/sda2: LABEL="OS" UUID="E422537022534728" TYPE="ntfs"
/dev/sda5: LABEL="DATA" UUID="9E0C01CADC9BBFD0" TYPE="ntfs"
/dev/sdb1: LABEL="PENDRIVE" UUID="1A15-0C10" TYPE="vfat"
/dev/sdc1: LABEL="Hitachi" UUID="8C5C95595C953F40" TYPE="ntfs"
/dev/sdc5: UUID="b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b" TYPE="ext4"
/dev/sdc6: UUID="93ff6b80-b975-47f1-817c-4f10227e2a5e" TYPE="ext4"
/dev/sdc7: UUID="eb31e9ae-9d6a-4f18-b790-b82313724e91" TYPE="swap"
/dev/sdd1: LABEL="8GB MICROSD" UUID="3E4E-9973" TYPE="vfat"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /media/93ff6b80-b975-47f1-817c-4f10227e2a5e/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /media/93ff6b80-b975-47f1-817c-4f10227e2a5e/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Apr 25 16:07 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 18:20 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 17:57 05_debian_theme
-rwxr-xr-x 1 root root 7399 Apr 17 18:20 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 18:20 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 18:20 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 18:20 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 18:20 41_custom
-rw-r--r-- 1 root root  483 Apr 17 18:20 README



/boot detected in the fstab of sdc6: UUID=b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b (sdc5)

=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	bootmgr,	no-grldr,	boot/bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	no-grldr,	Boot/BCD,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda2.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/mnt/boot-sav/sda5.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/media/Hitachi.
sdc5	: sdc,	is-sepboot,	grubenv-ok	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/media/b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b.
sdc6	: sdc,	not-sepboot,	no-grubenv	grub2,	grub-pc,	update-grub,	64,	no-kernel,	is-os,	not--efi--part,	fstab-has-goodBOOT,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	/media/93ff6b80-b975-47f1-817c-4f10227e2a5e.
sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	no-grldr,	no-b-bcd,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	/media/8GB MICROSD.

sda	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	2048 sectors * 512 bytes
sdc	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	2048 sectors * 512 bytes
sdd	: MSDos,	not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	usb-disk,	2048 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD3200BEVT-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      1049kB  17.8GB  17.8GB  primary   fat32        hidden, lba
2      17.8GB  97.8GB  80.0GB  primary   ntfs         boot
3      97.8GB  320GB   222GB   extended               lba
5      97.8GB  320GB   222GB   logical   ntfs


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdb: 4022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      19.5kB  4014MB  4014MB  primary  fat32        boot, lba


Model: HitachiG ST (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  970GB  970GB   primary   ntfs            boot
2      970GB   997GB  27.2GB  extended
5      970GB   970GB  199MB   logical   ext4
6      970GB   995GB  25.0GB  logical   ext4
7      995GB   997GB  2001MB  logical   linux-swap(v1)


Model: Multiple Card Reader (scsi)
Disk /dev/sdd: 7948MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4194kB  7948MB  7944MB  primary  fat32


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdd1 on /media/8GB MICROSD type vfat (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc5 on /media/b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6 on /media/93ff6b80-b975-47f1-817c-4f10227e2a5e type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1 on /media/Hitachi type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc5 sdc6 sdc7 size slaves stat subsystem trace uevent
/sys/block/sdd:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda5 sdb sdb1 sdc sdc1 sdc2 sdc5 sdc6 sdc7 sdd sdd1 serial sg0 sg1 sg2 sg3 shm snapshot snd stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 usbmon8 v4l vga_arbiter video0 zero
/dev/mapper:  control
/mnt/boot-sav/sda2:  AdobeReader.log ASUS.DAT ASUS.SYS Boot bootmgr BOOTNXT boot-sav BOOTSECT.BAK CCProxy cygwin devlist.txt Documents and Settings downloads Finish.log Flashtool hiberfil.sys if.log inetpub inject.log.txt Intel MSOCache OFFICE2007_L.TXT pagefile.sys Pass.txt Patch_Win7.log PerfLogs ProgramData Program Files Program Files (x86) Recovery RECOVERY.DAT $RECYCLE.BIN RHDSetup.log setup.log SumHidd.txt SumOS.txt swapfile.sys System Volume Information UL30A.bin UL30A_WIN7.100 Users v82.txt Windows

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.5G  142M  1.4G  10% /
udev           devtmpfs   1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs      596M  944K  595M   1% /run
/dev/sdb1      vfat       3.8G  698M  3.1G  19% /cdrom
/dev/loop0     squashfs   664M  664M     0 100% /rofs
tmpfs          tmpfs      1.5G   32K  1.5G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.5G   80K  1.5G   1% /run/shm
/dev/sdd1      vfat       7.4G  4.9G  2.6G  66% /media/8GB MICROSD
/dev/sdc5      ext4       189M   34M  146M  19% /media/b5fa15db-bd0b-47ca-ba13-f5b573d0fa8b
/dev/sdc6      ext4        24G  2.6G   20G  12% /media/93ff6b80-b975-47f1-817c-4f10227e2a5e
/dev/sdc1      fuseblk    904G  165G  740G  19% /media/Hitachi
/dev/sda1      vfat        17G   13G  3.9G  78% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     75G   73G  2.2G  98% /mnt/boot-sav/sda2
/dev/sda5      fuseblk    207G  207G  572M 100% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    34812854    17405403+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    34812855   191093174    78140160    7  HPFS/NTFS/exFAT
/dev/sda3       191093175   625137344   217022085    f  W95 Ext'd (LBA)
/dev/sda5       191093238   625137344   217022053+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          38     7839719     3919841    c  W95 FAT32 (LBA)

Disk /dev/sdc: 1000.2 GB, 1000204138496 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523708 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdfe6cd68

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1894533297   947265625    7  HPFS/NTFS/exFAT
/dev/sdc2      1894535166  1947662335    26563585    5  Extended
/dev/sdc5      1894535168  1894924287      194560   83  Linux
/dev/sdc6      1894926336  1943752703    24413184   83  Linux
/dev/sdc7      1943754752  1947662335     1953792   82  Linux swap / Solaris

Disk /dev/sdd: 7948 MB, 7948206080 bytes
81 heads, 10 sectors/track, 19165 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            8192    15523839     7757824    b  W95 FAT32


/boot detected. Please check the options.

=================== Default settings
recommendedrepair
This setting would reinstall the grub2 of sdc6 into the MBR of sdc, using the following options:       sdc5/boot,
Additional repair would be performed: unhide-bootmenu

=================== Settings chosen by the user
customrepair
This setting will reinstall the grub2 of sdc6 into the MBR of sdc, using the following options:       sdc5/boot,
Additional repair will be performed: unhide-bootmenu


sdc6/fstab changed for /boot
sda2 is 98 % full
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

The sda2 (Windows 8) partition is still full. This can prevent to start it (e.g. you may get a Power Manager error).
Already mounted /dev/sdc6 on /media/93ff6b80-b975-47f1-817c-4f10227e2a5e
Mounted /dev/sdc5 on /media/93ff6b80-b975-47f1-817c-4f10227e2a5e/boot
Reinstall the GRUB of sdc6 into the MBR of sdc
chroot /media/93ff6b80-b975-47f1-817c-4f10227e2a5e update-grub
Generating grub.cfg ...
Shutting down nautilus-gdu extension
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 8 (loader) on /dev/sda2
grub-install (GRUB) 1.99-21ubuntu3
grub-install --recheck /dev/sdc: Installation finished. No error reported.
exit code of grub-install /dev/sdc:0

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdc (1000GB) disk!
pastebinit  packages needed
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/main i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/ precise/restricted i386 Packages (/var/lib/apt/lists/Ubuntu%2012.04%20LTS%20%5fPrecise%20Pangolin%5f%20-%20Release%20amd64%20(20120425)_dists_precise_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
dpkg-preconfigure: unable to re-open stdin: No such file or directory
```

My main operating system is windows 8 CP, don't know if that matters.

---

### Post by oldfred on 2012-07-03
Script is showing several issues but grub looks like it is installed ok. Did you tick the option that you have a separate /boot? Most desktop installs do not have that so you have to tell Boot-repair that sdc5 is a /boot and sdc6 is your install.

What mode is BIOS set to. Is it in AHCI or some older IDE emulation? There are older BIOS that only boot from the first 137GB of  a drive and some BIOS settings can make a newer system behave that way. If that is the issue most solve it by moving /boot to somewhere inside the first 137GB of the drive.

It says your Windows 8 is full? May have to do with Windows 8 defaulting to hibernation? Normally NTFS partitions need 20 to 30% free to work well.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by banda on 2012-07-03
i did tick the option for different /boot, 

If i need to put /boot in the first partition on the external drive, how can i do it? . its an ntfs partition.

Also i am running ubuntu live cd via another usb flash drive which gets detected as sdb mking the eternal hard disk sdc. I suspect that when i to boot from eternal hard disk  instead of the flash drive it actually is sdb inctead of sdc because i unplug the usb drive or edit the boot order in bios. Could that be the problem?

---

### Post by oldfred on 2012-07-03
Ubuntu uses UUID so drive order is not supposed to make any difference.

The only way to have /boot at the beginning of the drive is to move the NTFS partition right and insert a new partition at the beginning of the drive. 

But what is BIOS setting before doing that. Moving partitions can take a long time and has some risk. Any power failure in the middle of a move causes corruption and then you can only restore from backups.

---

### Post by YannBuntu on 2012-07-04
Hello
> **oldfred said:**
> Ubuntu uses UUID so drive order is not supposed to make any difference.

The only way to have /boot at the beginning of the drive is to move the NTFS partition right and insert a new partition at the beginning of the drive. 

But what is BIOS setting before doing that. Moving partitions can take a long time and has some risk. Any power failure in the middle of a move causes corruption and then you can only restore from backups.

+1
See [this]("http://ubuntuforums.org/showthread.php?t=1998257") for more information.

@fred: in the log we can see that the separate /boot was correctly selected by default, and was not unticked by the user:

```
=================== Default settings
recommendedrepair
This setting would reinstall the grub2 of sdc6 into the MBR of sdc,
using the following options:       **sdc5/boot**,
Additional repair would be performed: unhide-bootmenu

=================== Settings chosen by the user
customrepair
This setting will reinstall the grub2 of sdc6 into the MBR of sdc,
using the following options:       **sdc5/boot**,
Additional repair will be performed: unhide-bootmenu
```

---

### Post by banda on 2012-07-05
I tried the 'ATA disk support' option in boot-repair but it did not fix the problem. The error changed to 'no such device: 29106...'. The device id for the partition was correct tho. 
I also hunted for the option change the hDD mode in the bios but could not find it. My laptop is a 1 yerar old Asus UL30A

I finally resized the 970gb partition on the external HDD to make room for another 200mb partition in the beginigng of the drive. Created new /boot partition in the begining of the drive and reloaded grub with boot-repair. Ubuntu boots perfectly now.

moral of the story: Leave a couple hundred mb unallocated in the beginging of any new hard disks before creating main partition just in case.

---

### Post by YannBuntu on 2012-07-06
good job :)

---

