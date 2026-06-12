---
title: "Windows XP selection from Grub after UBUNTU install just reboots PC (back to Grub)"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by dave200 on 2012-05-07
Hello All, 

I am a completely new user to UBUNTU having just installed it on my PC.  I installed UBUNTU 12 from an installation CD alongside Windows XP but unfortunately think I must have done something wrong as I am now unable to boot to Windows XP from the GRUB screen.

I firstly had a problem with my display as it was not showing the grub screen but solved this from other posts by editing the GRUB file.

I can boot UBUNTU fine but when I select Windows XP it just reboots.  I have read similar posts but don't really understand them and they dont seem to be exactly the same.

I have run a boot script that I found in another post and paste the contents below hoping that it will help.

Thank you in advance to anyone who can give me a bit of help.

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 12.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   326,864,159   326,864,097   7 HPFS/NTFS
/dev/sda2         326,864,894   390,721,535    63,856,642   5 Extended
/dev/sda5         326,864,896   388,759,551    61,894,656  83 Linux
/dev/sda6         388,761,600   390,721,535     1,959,936  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   2   976,773,166   976,773,165   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="DED446CDD446A79B" TYPE="ntfs" 
/dev/sda5: UUID="9d7c8897-3238-4203-a4fd-a2af7b4bdb07" TYPE="ext4" 
/dev/sda6: UUID="12a863af-0c22-40dc-a0dc-b3d223d069d4" TYPE="swap" 
/dev/sdb1: LABEL="BLUEDRIVE" UUID="EFDE-1BF7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdb1 on /media/BLUEDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DED446CDD446A79B
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12a863af-0c22-40dc-a0dc-b3d223d069d4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 167.3GB: boot/grub/grub.cfg
 167.3GB: boot/initrd.img-3.2.0-23-generic-pae
 167.3GB: boot/vmlinuz-3.2.0-23-generic-pae
 167.3GB: initrd.img
 167.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e1 71 79 83 43 52 5e 50  24 7f e0 d2 0c 03 39 00  |.qy.CR^P$.....9.|
00000010  13 30 00 a4 b1 20 3d 17  06 ec 4b fd 2c 72 0d 34  |.0... =...K.,r.4|
00000020  ca e0 68 22 33 9d 60 68  f9 d6 75 65 f8 31 45 81  |..h"3.`h..ue.1E.|
00000030  ab 01 6e ae 9e 19 30 0f  73 a2 d7 d0 a9 06 c3 95  |..n...0.s.......|
00000040  10 bf 01 c1 f3 8a 27 2e  9d 20 3e 62 1d 76 57 6f  |......'.. >b.vWo|
00000050  24 a5 2e 21 94 8f d0 bf  79 90 78 1e 7c 28 74 79  |$..!....y.x.|(ty|
00000060  c3 f1 00 3a 87 5a c0 5c  04 18 bc 41 98 45 9f 00  |...:.Z.\...A.E..|
00000070  b2 89 a2 80 cc e0 a6 0c  0f 86 c2 f3 21 7e 32 43  |............!~2C|
00000080  81 80 99 24 90 01 60 1b  9e 60 3e 41 e0 42 b8 f5  |...$..`..`>A.B..|
00000090  0e 34 22 01 e6 1e 2e 9c  a5 66 53 99 7e 16 38 06  |.4"......fS.~.8.|
000000a0  54 e9 d1 1f 81 69 07 b4  67 16 a1 fe 46 58 d6 01  |T....i..g...FX..|
000000b0  27 1f dc 89 4e d6 67 c2  1c 9e 61 d3 98 fc 59 f0  |'...N.g...a...Y.|
000000c0  22 00 2b 90 24 7c 31 d6  09 5f fa 34 83 3a f7 51  |".+.$|1.._.4.:.Q|
000000d0  24 a6 39 cc 25 12 56 02  38 bf b1 c0 49 37 72 9d  |$.9.%.V.8...I7r.|
000000e0  b4 a5 8c 20 c2 6f 02 ef  b3 8f 54 97 02 cc e2 5b  |... .o....T....[|
000000f0  8a 8e 40 a8 ae 05 c7 6b  60 08 00 7a 1e 74 cb ca  |..@....k`..z.t..|
00000100  23 01 bb c7 22 a0 8b 0f  d2 cc 8c 8d 03 6d 7a f7  |#..."........mz.|
00000110  50 62 8f ae c9 cc bc 1c  96 db 1f 16 33 61 e3 e8  |Pb..........3a..|
00000120  31 c3 11 f0 59 27 cb 7e  33 38 d2 89 a8 67 04 90  |1...Y'.~38...g..|
00000130  04 24 cc 3c 8a 22 ec 88  f9 11 f3 23 65 74 a0 c7  |.$.<.".....#et..|
00000140  92 07 8a 48 b3 b8 d5 66  15 3a bf 54 53 8c 3c d1  |...H...f.:.TS.<.|
00000150  61 c7 41 a5 3a 50 51 6e  72 f0 41 e6 9f 4e b1 06  |a.A.:PQnr.A..N..|
00000160  64 83 21 8e 9f 14 9c e8  27 35 1a e1 51 bd 88 92  |d.!.....'5..Q...|
00000170  32 96 6f c3 af 58 c6 4c  5f 58 7b 5f 13 24 d2 74  |2.o..X.L_X{_.$.t|
00000180  c5 21 29 da fd 1e b1 06  ae 9d 2d 62 68 40 42 36  |.!).......-bh@B6|
00000190  c4 69 ec f9 80 f6 a7 03  d3 38 d1 55 47 9d 18 06  |.i.......8.UG...|
000001a0  e0 3e 71 19 64 4a 75 27  98 91 18 2f 40 51 09 00  |.>q.dJu'.../@Q..|
000001b0  3d 2d 08 6c 2d dc 0e 0d  20 58 ab 50 31 7f 00 fe  |=-.l-... X.P1...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 b0 03 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 02 70  b0 03 00 f0 1d 00 00 00  |.......p........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```Hello All, 

I am a completely new user to UBUNTU having just installed it on my PC.   I installed UBUNTU 12 from an installation CD alongside Windows XP but  unfortunately think I must have done something wrong as I am now unable  to boot to Windows XP from the GRUB screen.

I firstly had a problem with my display as it was not showing the grub  screen but solved this from other posts by editing the GRUB file.

I can boot UBUNTU fine but when I select Windows XP it just reboots.  I  have read similar posts but don't really understand them and they dont  seem to be exactly the same.

I have run a boot script that I found in another post and paste the contents below hoping that it will help.

Thank you in advance to anyone who can give me a bit of help.

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks at sector 129760372 
    on boot drive #-111 for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 12.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   326,864,159   326,864,097   7 HPFS/NTFS
/dev/sda2         326,864,894   390,721,535    63,856,642   5 Extended
/dev/sda5         326,864,896   388,759,551    61,894,656  83 Linux
/dev/sda6         388,761,600   390,721,535     1,959,936  82 Linux swap / Solaris


Drive: sdb ___________________ __________________________________________________  ___

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   2   976,773,166   976,773,165   b W95 FAT32


blkid -c /dev/null: __________________________________________________  __________

/dev/sda1: UUID="DED446CDD446A79B" TYPE="ntfs" 
/dev/sda5: UUID="9d7c8897-3238-4203-a4fd-a2af7b4bdb07" TYPE="ext4" 
/dev/sda6: UUID="12a863af-0c22-40dc-a0dc-b3d223d069d4" TYPE="swap" 
/dev/sdb1: LABEL="BLUEDRIVE" UUID="EFDE-1BF7" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdb1 on /media/BLUEDRIVE type vfat  (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed   ,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW  S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro  soft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 9d7c8897-3238-4203-a4fd-a2af7b4bdb07
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DED446CDD446A79B
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=9d7c8897-3238-4203-a4fd-a2af7b4bdb07 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=12a863af-0c22-40dc-a0dc-b3d223d069d4 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 167.3GB: boot/grub/grub.cfg
 167.3GB: boot/initrd.img-3.2.0-23-generic-pae
 167.3GB: boot/vmlinuz-3.2.0-23-generic-pae
 167.3GB: initrd.img
 167.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  e1 71 79 83 43 52 5e 50  24 7f e0 d2 0c 03 39 00  |.qy.CR^P$.....9.|
00000010  13 30 00 a4 b1 20 3d 17  06 ec 4b fd 2c 72 0d 34  |.0... =...K.,r.4|
00000020  ca e0 68 22 33 9d 60 68  f9 d6 75 65 f8 31 45 81  |..h"3.`h..ue.1E.|
00000030  ab 01 6e ae 9e 19 30 0f  73 a2 d7 d0 a9 06 c3 95  |..n...0.s.......|
00000040  10 bf 01 c1 f3 8a 27 2e  9d 20 3e 62 1d 76 57 6f  |......'.. >b.vWo|
00000050  24 a5 2e 21 94 8f d0 bf  79 90 78 1e 7c 28 74 79  |$..!....y.x.|(ty|
00000060  c3 f1 00 3a 87 5a c0 5c  04 18 bc 41 98 45 9f 00  |...:.Z.\...A.E..|
00000070  b2 89 a2 80 cc e0 a6 0c  0f 86 c2 f3 21 7e 32 43  |............!~2C|
00000080  81 80 99 24 90 01 60 1b  9e 60 3e 41 e0 42 b8 f5  |...$..`..`>A.B..|
00000090  0e 34 22 01 e6 1e 2e 9c  a5 66 53 99 7e 16 38 06  |.4"......fS.~.8.|
000000a0  54 e9 d1 1f 81 69 07 b4  67 16 a1 fe 46 58 d6 01  |T....i..g...FX..|
000000b0  27 1f dc 89 4e d6 67 c2  1c 9e 61 d3 98 fc 59 f0  |'...N.g...a...Y.|
000000c0  22 00 2b 90 24 7c 31 d6  09 5f fa 34 83 3a f7 51  |".+.$|1.._.4.:.Q|
000000d0  24 a6 39 cc 25 12 56 02  38 bf b1 c0 49 37 72 9d  |$.9.%.V.8...I7r.|
000000e0  b4 a5 8c 20 c2 6f 02 ef  b3 8f 54 97 02 cc e2 5b  |... .o....T....[|
000000f0  8a 8e 40 a8 ae 05 c7 6b  60 08 00 7a 1e 74 cb ca  |..@....k`..z.t..|
00000100  23 01 bb c7 22 a0 8b 0f  d2 cc 8c 8d 03 6d 7a f7  |#..."........mz.|
00000110  50 62 8f ae c9 cc bc 1c  96 db 1f 16 33 61 e3 e8  |Pb..........3a..|
00000120  31 c3 11 f0 59 27 cb 7e  33 38 d2 89 a8 67 04 90  |1...Y'.~38...g..|
00000130  04 24 cc 3c 8a 22 ec 88  f9 11 f3 23 65 74 a0 c7  |.$.<.".....#et..|
00000140  92 07 8a 48 b3 b8 d5 66  15 3a bf 54 53 8c 3c d1  |...H...f.:.TS.<.|
00000150  61 c7 41 a5 3a 50 51 6e  72 f0 41 e6 9f 4e b1 06  |a.A.:razz:Qnr.A..N..|
00000160  64 83 21 8e 9f 14 9c e8  27 35 1a e1 51 bd 88 92  |d.!.....'5..Q...|
00000170  32 96 6f c3 af 58 c6 4c  5f 58 7b 5f 13 24 d2 74  |2.o..X.L_X{_.$.t|
00000180  c5 21 29 da fd 1e b1 06  ae 9d 2d 62 68 40 42 36  |.!).......-bh@B6|
00000190  c4 69 ec f9 80 f6 a7 03  d3 38 d1 55 47 9d 18 06  |.i.......8.UG...|
000001a0  e0 3e 71 19 64 4a 75 27  98 91 18 2f 40 51 09 00  |.>q.dJu'.../@Q..|
000001b0  3d 2d 08 6c 2d dc 0e 0d  20 58 ab 50 31 7f 00 fe  |=-.l-... X.P1...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 70 b0 03 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 02 70  b0 03 00 f0 1d 00 00 00  |.......p........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by oldfred on 2012-05-07
Added code tags - highlight like copying & click # in edit menu above post.

I do not see how you are booting? You show grub 1.97 in the MBR and 12.04 is using grub2 version 1.99 and they are not compatible.

Your Windows partition, boot stanza and boot.ini look ok. Script does not always parse the internals, which are a Windows issue. You may need a chkdsk or other Windows repairs.

I suggest you totally uninstall grub2 and reinstall.

If you can boot into your install, you can skip the chroot part.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by darkod on 2012-05-07
With this setup I am surprised you can boot ubuntu at all. The bootloader on /dev/sda is all weird.

What editing did you do in the GRUB file exactly? Are you talking about direct editing of grub.cfg or what?

To install correctly grub2 on the MBR of /dev/sda you should boot ubuntu and in terminal try:
sudo grub-install /dev/sda

---

### Post by oldfred on 2012-05-07
Sorry, I tried to merge posts, thinking it would leave both separate, it combined into one.
Please do not create duplicate threads.

---

