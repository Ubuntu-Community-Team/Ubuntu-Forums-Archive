---
title: "Grub selection cause reboot"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by rldwallace on 2011-10-03
Hi,

If when I pick my Windows XP from the grub menu list, it just causes the computer to reboot and goes back to grub what can I do to get things installed in the right places?

Here is my ```
fdisk -l:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19538bf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+  82  Linux swap / Solaris
/dev/sda2             609       18183   141171187+   5  Extended
/dev/sda4           18184       38913   166513725   83  Linux
/dev/sda5             609       18183   141171156   83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd779d779

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    7  HPFS/NTFS
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1904 MB, 1904738304 bytes
173 heads, 56 sectors/track, 96 cylinders
Units = cylinders of 9688 * 2048 = 19841024 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0xde48f3d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          96     1860070    6  FAT16
Partition 1 does not start on physical sector boundary.

This is what I get when I do an update-grub:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sda4
Found Microsoft Windows XP Professional on /dev/sdb1
done


I guess I've made a mess of things :(

---

### Post by drs305 on 2011-10-03
It sounds like the problem described in this thread, which deals with solving the problem when Grub gets installed in the Windows partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If this doesn't solve things, please download and run the boot info script and post the contents of RESULTS.txt  You can get to the script site by clicking the "BIS" link in my signature line.

---

### Post by rldwallace on 2011-10-03
> **drs305 said:**
> It sounds like the problem described in this thread, which deals with solving the problem when Grub gets installed in the Windows partition:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

If this doesn't solve things, please download and run the boot info script and post the contents of RESULTS.txt  You can get to the script site by clicking the "BIS" link in my signature line.

Wow! Thanks for the quick reply! Here I go. Wish me luck!

---

### Post by rldwallace on 2011-10-03
OK... I ran into problems and I'm real nervous about monkeying around with the options so I'm going with your plan B.

Results.txt=

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Lilo is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda4 and looks at sector 10100663 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/menu.lst /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 10185783 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. According to the info in the boot 
                       sector, sdb1 has 78155216 sectors, but according to 
                       the info from fdisk, it has 78156161 sectors.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63     9,767,519     9,767,457  82 Linux swap / Solaris
/dev/sda2           9,767,520   292,109,894   282,342,375   5 Extended
/dev/sda5           9,767,583   292,109,894   282,342,312  83 Linux
/dev/sda4         292,109,895   625,137,344   333,027,450  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    78,156,224    78,156,162   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 1904 MB, 1904738304 bytes
173 heads, 56 sectors/track, 96 cylinders, total 930048 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  13       930,047       930,035   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a7d6ee70-b61e-453f-9a47-2b90a1a7f91c   swap       
/dev/sda4        ed6d5f24-5055-458a-9f7d-597bbec72ebe   ext3       
/dev/sda5        943b40db-b5aa-424b-baec-50e310fa7963   ext4       
/dev/sdb1        18D0D270D0D2541A                       ntfs       
/dev/sdc1        3433-3231                              vfat       WALKMAN

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/WALKMAN           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


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
search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=943b40db-b5aa-424b-baec-50e310fa7963 ro vga=792  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=943b40db-b5aa-424b-baec-50e310fa7963 ro single vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=943b40db-b5aa-424b-baec-50e310fa7963 ro vga=792  quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=943b40db-b5aa-424b-baec-50e310fa7963 ro single vga=792
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 943b40db-b5aa-424b-baec-50e310fa7963
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu karmic (development branch), kernel 2.6.31-14-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root ed6d5f24-5055-458a-9f7d-597bbec72ebe
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro vga=792 splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root ed6d5f24-5055-458a-9f7d-597bbec72ebe
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu karmic (development branch), kernel 2.6.28-15-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root ed6d5f24-5055-458a-9f7d-597bbec72ebe
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro vga=792 splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu karmic (development branch), kernel 2.6.28-15-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root ed6d5f24-5055-458a-9f7d-597bbec72ebe
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu karmic (development branch), memtest86+ (on /dev/sda4)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set=root ed6d5f24-5055-458a-9f7d-597bbec72ebe
	linux /boot/memtest86+.bin 
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 18D0D270D0D2541A
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
proc            /proc           proc    defaults        0       0
UUID=943b40db-b5aa-424b-baec-50e310fa7963 /               ext4    errors=remount-ro 0       1
UUID=a7d6ee70-b61e-453f-9a47-2b90a1a7f91c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.790141582 = 5.143375360    boot/grub/core.img                             1
  28.157359600 = 30.233734656   boot/grub/grub.cfg                             1
 110.470046520 = 118.616309248  boot/initrd.img-2.6.38-10-generic              3
  86.991252422 = 93.406146048   boot/initrd.img-2.6.38-11-generic              3
 109.103168011 = 117.148634624  boot/vmlinuz-2.6.38-10-generic                 1
  70.454730511 = 75.650190848   boot/vmlinuz-2.6.38-11-generic                 2
  86.991252422 = 93.406146048   initrd.img                                     3
 110.470046520 = 118.616309248  initrd.img.old                                 3
  70.454730511 = 75.650190848   vmlinuz                                        2
 109.103168011 = 117.148634624  vmlinuz.old                                    1

=========================== sda4/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

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

timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
#splashimage=(hd0,3)/boot/grub/splashimages/00001.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=vga=792 splash

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
# howmany=2

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

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro vga=792 splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.31-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu karmic (development branch), kernel 2.6.28-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro vga=792 splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu karmic (development branch), kernel 2.6.28-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu karmic (development branch), memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d3d1b7dd-fc7a-4bd0-a749-a464aa47aac8 ro splash 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=d3d1b7dd-fc7a-4bd0-a749-a464aa47aac8 ro single 
initrd		/boot/initrd.img-2.6.22-15-generic
savedefault
boot

--------------------------------------------------------------------------------

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=ed6d5f24-5055-458a-9f7d-597bbec72ebe /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=D230A75430A73E7B /media/sda1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda3
UUID=d3d1b7dd-fc7a-4bd0-a749-a464aa47aac8 /media/sda3     ext3    defaults,relatime        0       2
# /dev/sda5
UUID=0230ABCD30ABC64F /media/sda5     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda6
UUID=D410F14A10F133D8 /media/sda6     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda7
UUID=02202fbe-2e1b-02e5-bf22-1fd4d7950b29 none            swap    sw              0       0
# /dev/sda8
UUID=3e98bb72-d664-4889-8e89-315e71156fc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 179.137599468 = 192.347532800  boot/grub/menu.lst                             1
 174.007709026 = 186.839354880  boot/grub/stage2                               2
 173.929606915 = 186.755493376  boot/initrd.img-2.6.22-14-generic              5
 174.042857647 = 186.877095424  boot/initrd.img-2.6.22-14-generic.bak          5
 174.047423840 = 186.881998336  boot/initrd.img-2.6.27-11-generic              5
 173.944339275 = 186.771312128  boot/initrd.img-2.6.28-15-generic              4
 178.892375469 = 192.084225536  boot/initrd.img-2.6.31-14-generic             13
 173.970382214 = 186.799275520  boot/vmlinuz-2.6.22-14-generic                 2
 174.023135662 = 186.855919104  boot/vmlinuz-2.6.27-11-generic                 3
 178.881316662 = 192.072351232  boot/vmlinuz-2.6.28-15-generic                 4
 179.129207134 = 192.338521600  boot/vmlinuz-2.6.31-14-generic                 8
 178.892375469 = 192.084225536  initrd.img                                    13
 173.944339275 = 186.771312128  initrd.img.old                                 4
 179.129207134 = 192.338521600  vmlinuz                                        8
 178.881316662 = 192.072351232  vmlinuz.old                                    4

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by drs305 on 2011-10-03
It may not mean a lot to you, but if you look at sdb1, your Windows partition, it shows Grub 2 installed. It overwrote Windows boot information, which is what we suspected.

So you need to repair Windows. I'm not a Windows user, but forum member *oldfred* has worked with a lot of users with Windows boot problems. You may be able to fix it using the links in one of his posts:
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

If you still can't work it out, I can try to get in touch with him tomorrow and ask him to take a look.

---

### Post by rldwallace on 2011-10-04
I'm concerned that I'll loose the good Grub (mmm...good grub) if I run the MS recovery tools and I can't do without my Ubuntu even if I get the WinXP going. I'm wondering if the tool will leave sda alone? If I loose it, will I need a copy of 11.04 to put it back in the right place? If I'm just re-installing Grub, can I just put a much smaller set of files on a USB memory key? Can Grub be installed from Windows?

I have some old XP disks around here somewhere but they don't match the OEM license of sdb1, which came with the computer. They may not even be "Professional". Would that even matter?

---

### Post by drs305 on 2011-10-04
Disclaimer: As I've mentioned, I don't know Windows; the following is my basic understanding but hopefully either you or a Windows user will have more specific knowledge.

I believe any repair or installation disk of the same version of Windows will work in the 'recovery/repair' mode. 

When you repair Windows, you shouldn't lose Grub 2 as long as your repairs are performed on the Windows drive. Your Windows repairs should take place on the sdb drive. Verify you are working with the correct drive when you make the changes, since the 'sda' and 'sdb' designations may change. I'd temporarily set the BIOS boot order to boot the Windows drive first, then use the Windows repair CD.

Which repair option you select determines if what you do writes to the MBR. Even if it wrote to the wrong drive, I believe 'fixboot' would leave the Grub MBR information intact, and think that is the option you want. If you need to use 'fixmbr', that should be done to the Windows drive only.


For Windows repair (sdb1), you don't have a 'boot flag' on the Windows partition, which I think you need if you ever boot Windows independently. By that, I mean if you have things correctly set up, you can have the sdb MBR set up for Windows, and the sda set up for booting Grub. You would have BIOS boot sda (Ubuntu) and will get the Grub menu. If you change the boot order to boot sdb first, you would get a pure Windows boot menu. But you will need to repair Windows and get the boot flag back on sdb1 to do this.

Once Windows is repaired, with the boot option set to sdb, you should be able to boot Windows. After it's fixed and boots properly, change the BIOS boot order back to sda (Ubuntu) and you should get the Grub menu back and have both OS's available and working in the menu.

Reinstalling Grub is not difficult if you have to do it. As long as you have a bootable Ubuntu LiveCD of the same release as your installation (Maverick, Natty, etc). You boot the CD, mount your Ubuntu partition, and then run a command or two to rewrite Grub to the MBR:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by rldwallace on 2011-10-04
I just had a look at my BIOS, and it seems to be an oversimplified HP creation not allowing a choice of HDD to boot from...just "Hard Drive". I think I'm actually going to have to pull the cable! I probably won't have a chance to get to it until Thursday but I wanted to express my appreciation to you drs305 for your help. You're awesome!

---

### Post by rldwallace on 2011-10-10
I didn't have to pull the cable after all. I set the emulation type on the drive with Ubuntu and Grub to 'none' and that seemed to stop it from booting. 

When I booted with the Windows XP disk, I did everything I could to engage some sort of repair mode, but that just didn't seem to be an option. I ended up installing a second instance of Windows, which in turn repaired the boot record of the drive and made the original XP installation menu selectable.

I'll be much more careful of the Grub upgrade defaults in the future. 

Thanks for you help,
David

---

