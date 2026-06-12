---
title: "how do i configure dual boot options"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by koll on 2012-05-21
i have set up an ubuntu 12.04 and xp on seprate partitions and now i cant figure how to boot from the xp partition in on a dell laptop latatude d 600 laptop please help

---

### Post by wilee-nilee on 2012-05-21
> **koll said:**
> i have set up an ubuntu 12.04 and xp on seprate partitions and now i cant figure how to boot from the xp partition in on a dell laptop latatude d 600 laptop please help

Try in ubuntu

```
sudo update-grub
```

---

### Post by koll on 2012-05-21
thanks that got grub working now how do i get windows partition into the grub options

---

### Post by wilee-nilee on 2012-05-21
If XP is not showing in the grub menu then run these commands and a results.txt will be in home. Open it and copy all the text, open a reply to this thread, hit the # in the reply panel and paste all the text between the code tags.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by koll on 2012-05-21
#

                 ```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 40965813. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  Windows XP
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    40,965,749    40,965,687  83 Linux
/dev/sda2          40,965,811    78,140,159    37,174,349   f W95 Extended (LBA)
/dev/sda5          40,965,813    73,738,349    32,772,537   b W95 FAT32
/dev/sda6          73,738,413    78,140,159     4,401,747  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        fcc25ab8-a734-43bb-9622-09324f1ec17f   xfs        
/dev/sda5        101B-583C                              vfat       
/dev/sda6        12ba9aba-5601-41de-9a6e-724ef56a21ee   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        xfs        (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fcc25ab8-a734-43bb-9622-09324f1ec17f

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 12.04 LTS, kernel 3.2.0-24-generic
uuid		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/vmlinuz-3.2.0-24-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro quiet splash 
initrd		/boot/initrd.img-3.2.0-24-generic

title		Ubuntu 12.04 LTS, kernel 3.2.0-24-generic (recovery mode)
uuid		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/vmlinuz-3.2.0-24-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro  single
initrd		/boot/initrd.img-3.2.0-24-generic

title		Ubuntu 12.04 LTS, kernel 3.0.0-12-generic
uuid		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro quiet splash 
initrd		/boot/initrd.img-3.0.0-12-generic

title		Ubuntu 12.04 LTS, kernel 3.0.0-12-generic (recovery mode)
uuid		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro  single
initrd		/boot/initrd.img-3.0.0-12-generic

title		Chainload into GRUB 2
root		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/grub/core.img

title		Ubuntu 12.04 LTS, memtest86+
uuid		fcc25ab8-a734-43bb-9622-09324f1ec17f
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=========================== sda1/boot/grub/grub.cfg: ===========================

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
insmod xfs
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod xfs
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod xfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fcc25ab8-a734-43bb-9622-09324f1ec17f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fcc25ab8-a734-43bb-9622-09324f1ec17f /               xfs     defaults        0       1
# swap was on /dev/sda6 during installation
UUID=f787d6da-c1bf-454f-945f-e4f3cc20dc95 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.2.0-24-generic               1
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  cb 3a 72 1c c2 98 22 02  91 d8 38 4c ab f0 76 14  |.:r..."...8L..v.|
00000010  c9 83 1f ea a2 72 e3 00  cf 11 96 07 80 61 78 31  |.....r.......ax1|
00000020  19 70 31 f0 84 a4 18 d7  83 20 36 09 46 db c6 c1  |.p1...... 6.F...|
00000030  21 74 a1 71 e1 f0 1d 05  ba 20 8b 89 4c 16 a8 25  |!t.q..... ..L..%|
00000040  35 59 81 18 08 01 c0 04  83 38 02 4b 80 2c 19 e0  |5Y.......8.K.,..|
00000050  6e 59 c8 02 53 56 d2 c4  19 93 10 af 16 1a df 57  |nY..SV.........W|
00000060  c6 f2 1e 4c 16 82 00 94  0c e2 f5 40 3c 1f 02 01  |...L.......@<...|
00000070  1f 86 40 51 9a 38 2f 0b  04 c1 04 0d 40 26 02 b8  |..@Q.8/.....@&..|
00000080  98 10 c0 68 33 c0 20 0d  8d 41 80 f0 06 87 db 98  |...h3. ..A......|
00000090  a4 16 86 01 93 09 38 3b  1f 61 58 25 1f 00 c4 ba  |......8;.aX%....|
000000a0  91 28 30 50 33 07 80 81  d4 10 c0 b6 29 06 0a c9  |.(0P3.......)...|
000000b0  12 55 29 c3 26 89 0a d4  19 03 65 c0 55 19 11 8d  |.U).&.....e.U...|
000000c0  f1 4f 81 68 d2 83 00 81  83 02 e0 2c 0d b3 2a 25  |.O.h.......,..*%|
000000d0  4b 8d 62 96 ca b0 18 25  fb b8 38 1c 8d 8c 0d 01  |K.b....%..8.....|
000000e0  8b c1 be a5 bf a4 55 a0  55 40 dc 18 4c a9 1a 1c  |......U.U@..L...|
000000f0  99 71 f8 ff 12 2a 52 08  c6 00 d8 c0 14 60 c2 58  |.q...*R......`.X|
00000100  80 06 12 03 05 46 44 20  55 84 15 63 70 10 73 15  |.....FD U..cp.s.|
00000110  6b 7a 56 0c 4e 2b 06 1f  09 58 d2 a5 21 61 2a 31  |kzV.N+...X..!a*1|
00000120  53 40 90 37 a9 55 8f db  2b d0 10 14 c2 60 0e 06  |S@.7.U..+....`..|
00000130  d0 43 56 0c 40 0a 05 42  f0 52 05 25 f7 ec 2a cd  |.CV.@..B.R.%..*.|
00000140  b0 ad f3 8e 06 78 14 c6  00 90 70 04 ad 6f fc 21  |.....x....p..o.!|
00000150  2b aa bf e6 f9 9b 40 b9  d5 1f 56 a8 18 cf c1 f0  |+.....@...V.....|
00000160  7f f3 55 65 57 e6 c0 4c  50 1f b8 19 e0 6c 14 c0  |..UeW..LP....l..|
00000170  70 4b 0f c7 0d e8 31 20  70 37 cd 51 a1 a1 51 94  |pK....1 p7.Q..Q.|
00000180  1b 0e f7 3e 1c e6 82 30  5a a8 84 d6 b0 de 03 ca  |...>...0Z.......|
00000190  ff fa a4 18 28 86 da d0  e0 18 0a 36 0c 19 61 91  |....(......6..a.|
000001a0  74 a5 5a 60 65 50 09 03  fd af b6 0c 69 a1 17 54  |t.Z`eP......i..T|
000001b0  03 0d 1e a8 06 15 36 f3  47 40 f1 ff fa eb 00 01  |......6.G@......|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 b9 11 f4 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff bb 11  f4 01 92 2a 43 00 00 00  |...........*C...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
mdadm: No arrays found in config file or automatically
```

#

---

### Post by wilee-nilee on 2012-05-21
So several problems, has XP booted at all? 

Xp is in a extended it needs to be in a primary to run.

The Ubuntu install has both grub-legacy and grub 2 this can be fixed.

---

### Post by oldfred on 2012-05-21
Besides being in a logical partition, you have no boot files. Was XP booting from another install of Windows that was a primary partition. 

XP is an older install as it is in a FAT partition and the FAT partition PBR - partition boot sector does not match the partition table.

Since you have available primary partitions, you can switch the XP partition back to a primary with fixparts. 
But you need a XP install disk to run fixBoot, chkdsk and maybe some other repairs to recreate boot.ini.

Copies of most of the boot files are in backup locations in the XP install.

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 


How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

### Post by YannBuntu on 2012-05-24
Hello
Please try the "Recommended repair" of [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") and indicate the URL that will appear.

FYI, it should:
- purge and reinstall GRUB (will remove GRUB Legacy)
- fix the /boot.ini /ntldr /NTDETECT.COM files (if there are not too many other damaged files)

---

### Post by koll on 2012-06-03
thank you every on for all your help. now i have got setting up the dual boot systems down.

---

