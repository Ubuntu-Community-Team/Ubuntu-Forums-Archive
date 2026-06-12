---
title: "GRUB doesn't recognize/load Windows 7"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by pooyakhp on 2012-08-05
Same problem here, but windows 7 cannot repair!

```
the bootinfoscript results:


  ###             Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:  Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 306216 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 1 for /grub.
    Operating System:  
    Boot files:        /grub/menu.lst /grub/grub.cfg /grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /etc/fstab

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    61,432,559    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda2          61,432,560   312,560,639   251,128,080   f W95 Extended (LBA)
/dev/sda5          61,432,623   143,347,994    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda6         143,348,058   225,263,429    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda7         225,263,493   312,560,639    87,297,147   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     2,000,895     1,998,848  83 Linux
/dev/sdb2           2,002,942   312,560,639   310,557,698   f W95 Extended (LBA)
/dev/sdb5         102,398,373   204,796,619   102,398,247   7 NTFS / exFAT / HPFS
/dev/sdb6         204,796,683   312,560,639   107,763,957   7 NTFS / exFAT / HPFS
/dev/sdb7           2,002,944     9,814,015     7,811,072  82 Linux swap / Solaris
/dev/sdb8           9,816,064    29,345,791    19,529,728  83 Linux
/dev/sdb9          29,347,840    62,547,967    33,200,128  83 Linux
/dev/sdb10         62,550,016   102,397,951    39,847,936  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        683471FD3471CF16                       ntfs       
/dev/sda5        FEDC35BBDC356ED1                       ntfs       Programs
/dev/sda6        F42426D824269D9C                       ntfs       Pooya
/dev/sda7        2CA4FEFDA4FEC87A                       ntfs       Payam
/dev/sdb1        473c8443-559a-4b6e-9449-3dd54d504f2b   ext4       
/dev/sdb10       ff2d4a1e-a95c-45e5-8175-5123107156c0   ext4       Files
/dev/sdb5        626CF4976CF46767                       ntfs       
/dev/sdb6        5EE4EA7AE4EA53B5                       ntfs       
/dev/sdb7        58ce3b80-e194-4d60-b709-fd0ce026e1be   swap       
/dev/sdb8        6c2e60a5-e121-4ab6-b42e-14c7d067f86f   ext4       
/dev/sdb9        c1187f14-d9c7-4312-ae7c-6f097f1e3762   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /media/Pooya             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Payam             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb10       /media/Files             ext4       (rw)
/dev/sdb1        /boot                    ext4       (rw)
/dev/sdb8        /                        ext4       (rw,errors=remount-ro)
/dev/sdb9        /home                    ext4       (rw)


============================= sdb1/grub/menu.lst: ==============================

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
# kopt=root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=473c8443-559a-4b6e-9449-3dd54d504f2b

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

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic
uuid		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/vmlinuz-2.6.32-41-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro quiet splash 
initrd		/initrd.img-2.6.32-41-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-41-generic (recovery mode)
uuid		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/vmlinuz-2.6.32-41-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro  single
initrd		/initrd.img-2.6.32-41-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-21-generic
uuid		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/vmlinuz-2.6.32-21-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro quiet splash 
initrd		/initrd.img-2.6.32-21-generic

title		Ubuntu 10.04.4 LTS, kernel 2.6.32-21-generic (recovery mode)
uuid		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/vmlinuz-2.6.32-21-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro  single
initrd		/initrd.img-2.6.32-21-generic

title		Chainload into GRUB 2
root		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/boot/grub/core.img

title		Ubuntu 10.04.4 LTS, memtest86+
uuid		473c8443-559a-4b6e-9449-3dd54d504f2b
kernel		/memtest86+.bin

[COLOR="Red"]title		WIndows 7
rootnoverify 	(hd1,1)
chainloader +1[/COLOR]
### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,8)'
search --no-floppy --fs-uuid --set 6c2e60a5-e121-4ab6-b42e-14c7d067f86f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	linux	/vmlinuz-2.6.32-41-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro   quiet splash
	initrd	/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	echo	'Loading Linux 2.6.32-41-generic ...'
	linux	/vmlinuz-2.6.32-41-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-41-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	linux	/vmlinuz-2.6.32-21-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 473c8443-559a-4b6e-9449-3dd54d504f2b
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.146041870 = 0.156811264    grub/core.img                                  1
   0.147468567 = 0.158343168    grub/grub.cfg                                  2
   0.139671326 = 0.149970944    grub/menu.lst                                  1
   0.164627075 = 0.176766976    initrd.img-2.6.32-21-generic                   1
   0.179496765 = 0.192733184    initrd.img-2.6.32-41-generic                   1
   0.132404327 = 0.142168064    vmlinuz-2.6.32-21-generic                      1
   0.136188507 = 0.146231296    vmlinuz-2.6.32-41-generic                      1

=============================== sdb8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb8 during installation
UUID=6c2e60a5-e121-4ab6-b42e-14c7d067f86f /               ext4    errors=remount-ro 0       1
/dev/sdb1       /boot           ext4    defaults        0       2
# /home was on /dev/sdb9 during installation
UUID=c1187f14-d9c7-4312-ae7c-6f097f1e3762 /home           ext4    defaults        0       2
# /media/Files was on /dev/sdb10 during installation
UUID=ff2d4a1e-a95c-45e5-8175-5123107156c0 /media/Files    ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=58ce3b80-e194-4d60-b709-fd0ce026e1be none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.859184265 = 5.217509376    initrd.img                                     1
   4.844314575 = 5.201543168    initrd.img.old                                 1
   4.815876007 = 5.171007488    vmlinuz                                        1
   4.812091827 = 5.166944256    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  0a 01 fa 0f 6f 00 01 f0  0f 6f 08 01 f0 0f 6f 51  |....o....o....oQ|
00000010  10 0f 6f 59 18 0f ef c6  0f ef ce 0f ef d6 0f ef  |..oY............|
00000020  de 0f 0f c2 bf 0f 0f cb  bf 0f ef c6 0f ef ce 0f  |................|
00000030  7f 02 01 fa 0f 7f 0a 01  fa 83 c1 20 83 eb 04 75  |........... ...u|
00000040  8d 8d 54 24 20 b8 09 00  00 00 89 d1 0f ef ff 0f  |..T$ ...........|
00000050  6f 45 00 0f 6f 4d 00 0f  60 c7 0f 68 cf 0f 7f 01  |oE..oM..`..h....|
00000060  0f 7f 49 48 83 c1 08 01  fd 48 75 e3 8d 0c 36 b8  |..IH.....Hu...6.|
00000070  04 00 00 00 8b bc 24 60  01 00 00 8d 1c 31 01 db  |......$`.....1..|
00000080  29 d8 bb 02 00 00 00 0f  6f 02 0f 6f 4a 08 0f 6f  |).......o..oJ..o|
00000090  52 10 0f 6f 5a 18 0f fd  c1 0f 6f 25 48 52 d2 62  |R..oZ.....o%HR.b|
000000a0  0f d5 e0 0f 6f 42 20 0f  6f 6a 10 0f fd e8 0f f9  |....oB .oj......|
000000b0  e5 0f 6f 6a 08 0f 6f 32  0f fd eb 0f fd f2 0f fd  |..oj..o2........|
000000c0  f6 0f f9 ee 0f d5 2d 40  52 d2 62 0f fd 25 08 52  |......-@R.b..%.R|
000000d0  d2 62 0f fd ec 0f 71 e5  05 0f 67 ed 0f 7e 2f 0f  |.b....q...g..~/.|
000000e0  fd ca 0f 6f 25 48 52 d2  62 0f d5 e1 0f 6f 4a 28  |...o%HR.b....oJ(|
000000f0  0f 6f 6a 08 0f fd e9 0f  f9 e5 0f 6f 2a 0f 6f 32  |.oj........o*.o2|
00000100  0f fd e8 0f fd f3 0f fd  f6 0f f9 ee 0f d5 2d 40  |..............-@|
00000110  52 d2 62 0f fd 25 08 52  d2 62 0f fd ec 0f 71 e5  |R.b..%.R.b....q.|
00000120  05 0f 67 ed 0f 7e 2c 37  01 cf 0f fd d3 0f 6f 25  |..g..~,7......o%|
00000130  48 52 d2 62 0f d5 e2 0f  6f 52 30 0f 6f 2a 0f fd  |HR.b....oR0.o*..|
00000140  ea 0f f9 e5 0f 6f 2a 0f  6f 72 08 0f fd e9 0f fd  |.....o*.or......|
00000150  f0 0f fd f6 0f f9 ee 0f  d5 2d 40 52 d2 62 0f fd  |.........-@R.b..|
00000160  25 08 52 d2 62 0f fd ec  0f 71 e5 05 0f 67 ed 0f  |%.R.b....q...g..|
00000170  7e 2f 0f fd d8 0f 6f 25  48 52 d2 62 0f d5 e3 0f  |~/....o%HR.b....|
00000180  6f 5a 38 0f 6f 2a 0f fd  eb 0f f9 e5 0f 6f 6a 08  |oZ8.o*.......oj.|
00000190  0f 6f 72 10 0f fd ea 0f  fd f1 0f fd f6 0f f9 ee  |.or.............|
000001a0  0f d5 2d 40 52 d2 62 0f  fd 25 08 52 d2 62 0f fd  |..-@R.b..%.R.b..|
000001b0  ec 0f 71 e5 05 0f 67 ed  0f 7e 2c 37 01 cf 00 fe  |..q...g..~,7....|
000001c0  ff ff 07 fe ff ff a7 e9  fb 05 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff ce 62  16 0c 34 59 6c 06 00 00  |.......b..4Yl...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
###
-----------------------------------------------------------------
```

I need the <snip> windows for some apps, otherwise in a month or two I'm gonna get rid of it for good! Guys pleaase help!

---

### Post by pooyakhp on 2012-08-05
Also (and I forgot to mention), the red lines are the things I added to the whatever-is-called file when I was trying to solve the problem!

---

### Post by coffeecat on 2012-08-05
Moved to own thread. 

Please do not revive old threads.

---

### Post by jtarin on 2012-08-05
I don't see a windows install on your second disk as you have indicated by the Grub Boot stanza in red. If Windows is on your first disk it should be "hd0"

title           WIndows 7
rootnoverify 	(hd1,1)
chainloader +1

---

### Post by oldfred on 2012-08-06
You do not have the Windows boot files on your system. It looks like you have an install in sdb5, but installs into extended partitions only can boot from boot files (usually another install) in a primary NTFS partition.

Your install in sdb5 is also copied from a first partition as the internal NTFS partition boot sector (PBR) says it starts at sector 63. And many of your other NTFS partitions also seem to be copies as they all say they start at sector 63. Windows PBR has to have the correct start and size info in them. Repairs on extended partitions may not work as Windows wants the boot flag on the partition to repair but does not recognize logical partitions with a boot flag. You may be able to run a Windows repair CD and run chkdsk on sdb5 from that, but still have to create a Primary NTFS with the boot flag and install the Windows boot files.

See manual repair of Vista instructions:
How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You are missing the first two files that probably was in a primary 100MB NTFS (hidden) boot/repair partition before:
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe

---

### Post by pooyakhp on 2012-08-12
Thank you guys, but...

Well, I dont really know about my windows being copied, actually I dont understand how an OS can be a copy, further elaborations will be appreciated. But, what I do know is that the partition which is now divided to linux partitions, was used for a 64bit Win7 as the first windows I installed on this drive, and then a (32bit) win7 was installed as the secondary OS on the neighbor partition (now sdb5). So, I'm guessing when I formatted and installed the ubuntu, the MBR was erased. Then, acoording to the above info, could there be any quicker, easier way to fix it?

---

### Post by I2k4 on 2012-08-12
I'd give Boot Repair a shot - it saved me from a dumb mistake I made trying to reconfigure GRUB:

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by pooyakhp on 2012-08-12
Boot repair, destructed my grub once, and I fixed the grub folder by renaming grub.bak to grub, it does not necessarily work with every situation I guess.

---

### Post by oldfred on 2012-08-12
Boot-Repair cannot fix the missing Windows files. You can install the boot files to sda1 and run chkdsk on sda5. But you need a Windows repairCD to do those fixes.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

