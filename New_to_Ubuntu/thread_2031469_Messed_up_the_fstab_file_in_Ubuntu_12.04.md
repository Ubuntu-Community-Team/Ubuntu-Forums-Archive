---
title: "Messed up the fstab file in Ubuntu 12.04"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2012-07-22
I changed my one of the partition to NTFS, then I started getting this error "Press S to skip or M to manual recovery". Then I tried the NTFS-3g application and pysdm but of no help.
So i Just messed up the fstab file manually. I dont know what exactly changes I made. And I cant boot in normal mode.It says can't mount.And when I try to fix grub error through Recovery mode/It prompts plymouth not found or something like this.
So I Booted via Live cd, downloaded the bootinfoscript to get the result.
I am attaching it. 
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 1901. But according to the info from fdisk, 
                       sda8 starts at sector 231643136.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 32800 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. The integrity check of the ADV area failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   102,767,804   102,767,742   7 NTFS / exFAT / HPFS
/dev/sda2         102,767,866   312,498,175   209,730,310   5 Extended
/dev/sda5         102,767,868   207,640,124   104,872,257   7 NTFS / exFAT / HPFS
/dev/sda6         207,640,188   227,640,187    20,000,000  83 Linux
/dev/sda7         227,641,344   231,641,087     3,999,744  82 Linux swap / Solaris
/dev/sda8         231,643,136   312,498,175    80,855,040   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8036 MB, 8036286464 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,200    15,695,504    15,693,305   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2A80A34780A31879                       ntfs       
/dev/sda5        7228FDC428FD877F                       ntfs       
/dev/sda6        191d2eac-f94d-4b90-9602-f1c66de131b6   ext4       
/dev/sda7        1c6662d6-245b-4ce3-af9b-34e9663bb02c   swap       
/dev/sda8        F6A04FBEA04F83D9                       ntfs       
/dev/sdb1        5CDA-14B4                              vfat       MULTIBOOT
/dev/sr0                                                iso9660    Pathways1Gold1.2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/Pathways1Gold1.2  iso9660    (ro,nosuid,nodev,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=191d2eac-f94d-4b90-9602-f1c66de131b6 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=191d2eac-f94d-4b90-9602-f1c66de131b6 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 191d2eac-f94d-4b90-9602-f1c66de131b6
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 2A80A34780A31879
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
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                    proc     nodev,noexec,nosuid                 0  0  
#Entry for /dev/sda6 :
UUID=191d2eac-f94d-4b90-9602-f1c66de131b6  /                        ext4     errors=remount -ro                           0  1  
#Entry for /dev/sdb5 :
UUID=50747F3E747F263E                      /media/Arif\040Catalyst  ntfs-3g  defaults,nosuid,nodev,locale=en_IN  0  0  
#Entry for /dev/sda1 :
UUID=2A80A34780A31879                      /media/sda1              ntfs-3g  defaults,locale=en_IN               0  0  
#Entry for /dev/sda5 :
UUID=7228FDC428FD877F                      /media/sda5              ntfs-3g  defaults,locale=en_IN               0  0  
#Entry for /dev/sda8 :
UUID=F6A04FBEA04F83D9                      /media/sda8              ntfs-3g  defaults,locale=en_IN               0  0  
UUID=2337-C493                                                                                                   0  1  
#Entry for /dev/sda7 :
UUID=1c6662d6-245b-4ce3-af9b-34e9663bb02c  none                     swap     sw                                  0  0  


/dev/sda6                                  /media/sda6              ext4     defaults                            0  0  
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  24 78 f5 f1 a2 ab 18 c8  89 8f 08 20 44 e7 a7 61  |$x......... D..a|
00000010  03 4e a0 5c 36 02 45 f4  c8 76 2b 89 1c 96 83 27  |.N.\6.E..v+....'|
00000020  c8 d8 37 73 14 07 c8 51  31 ce ea 56 39 07 dc f1  |..7s...Q1..V9...|
00000030  ea c1 89 58 22 13 61 34  1a a4 f4 0b 62 f5 53 71  |...X".a4....b.Sq|
00000040  a0 75 26 ee 08 43 8d ae  9a c0 b8 eb 1f dd 45 1b  |.u&..C........E.|
00000050  e1 1e 5c d9 2d 70 8c 94  8a b0 64 f9 b6 f7 d1 21  |..\.-p....d....!|
00000060  64 a7 3b 7a b8 37 5e 77  7e be e8 f7 2e 40 d7 76  |d.;z.7^w~....@.v|
00000070  a0 bc 91 f6 8f f2 c0 ab  cf f4 f4 69 4e 73 f6 ce  |...........iNs..|
00000080  cc c7 ed 2f 5a bb 33 43  94 1e f5 92 9e 0b 8d 9b  |.../Z.3C........|
00000090  df f3 9f c8 80 6f f5 12  a3 c7 1b 74 64 42 ba 11  |.....o.....tdB..|
000000a0  90 2b b5 24 27 a8 05 ab  94 3a 54 d3 a7 13 5c 22  |.+.$'....:T...\"|
000000b0  56 1b fe 67 38 c1 22 61  bd 82 51 32 2e 3a 13 82  |V..g8."a..Q2.:..|
000000c0  68 2d 0a 72 58 d4 cb 47  35 69 80 d3 80 31 3e a3  |h-.rX..G5i...1>.|
000000d0  bd 8d 27 ea ee be 3f 30  d4 7b 0f ba e5 35 fc b8  |..'...?0.{...5..|
000000e0  0c 24 64 31 23 19 7e af  31 03 ee aa 63 3e 2b b5  |.$d1#.~.1...c>+.|
000000f0  cc 9f 91 6a dc 40 45 16  a2 0c cc 25 c1 09 6a 4c  |...j.@E....%..jL|
00000100  33 69 3c 78 c1 4e 15 7a  3e 61 18 6f 87 11 1a f1  |3i<x.N.z>a.o....|
00000110  3a ab b5 ff 39 1f 2b ac  dd 8c 01 8b fa 90 57 d6  |:...9.+.......W.|
00000120  97 52 09 60 6a 4c 88 41  15 d9 76 3b 23 82 03 ee  |.R.`jL.A..v;#...|
00000130  c1 08 0a c0 3c 31 ea 8a  3e 53 25 03 c8 a2 bb ed  |....<1..>S%.....|
00000140  ef 39 44 01 56 e9 d0 9b  6f c5 7f 26 71 69 df 45  |.9D.V...o..&qi.E|
00000150  17 0e 08 c6 1f 50 79 47  7e b9 b1 a6 63 15 8d 2a  |.....PyG~...c..*|
00000160  f2 75 65 73 bd ff e4 21  02 7c ab 47 a7 9f a5 8e  |.ues...!.|.G....|
00000170  f6 16 28 29 18 52 d1 7c  53 17 1c 8c 03 c2 c5 25  |..().R.|S......%|
00000180  5a 5e e2 cd d7 65 bd 6b  87 56 73 b7 fe fb 4e 61  |Z^...e.k.Vs...Na|
00000190  14 76 e2 01 60 11 e9 c1  76 c3 df cc e0 82 5c 75  |.v..`...v.....\u|
000001a0  dd 4c 35 28 dc f3 52 11  b6 ab 4e 8e af 54 d1 55  |.L5(..R...N..T.U|
000001b0  2b 88 ac 65 30 64 b9 ae  9f 17 70 7f 32 2c 00 fe  |+..e0d....p.2,..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 41 39 40 06 00 fe  |..........A9@...|
000001d0  ff ff 05 fe ff ff 43 39  40 06 3f 2d 31 01 00 00  |......C9@.?-1...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/this/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by coffeecat on 2012-07-22
> **Arifcatalyst said:**
> Then I tried the NTFS-3g application and pysdm but of no help.

ntfs-3g is the driver for the ntfs filesystem and is already installed. pysdm is an old buggy, unmaintained piece of software and I suggest you uninstall it as soon as you have repaired your system. You need to mount your sda6 root partition from the live CD and edit fstab from the live session. This is what you do:

Boot up the live CD and "try Ubuntu" to get the live desktop. Open a Nautilus file browser and click on your sda6 root partition in the left pane. Since it has no partition label, it will probably appear as either "10.2GB filesystem" or "9.5GB filesystem," or similar. Once it has automounted, press ctrl-L to see what the mount path is. It should be "/media/191d2eac-f94d-4b90-9602-f1c66de131b6". If it is, open a terminal, and:

```
gksu gedit /media/191d2eac-f94d-4b90-9602-f1c66de131b6/etc/fstab
```

Don't forget tab completion in the terminal when you get to 191d2eac-f94d-4b90-9602-f1c66de131b6! :) This is your /etc/fstab at the moment and I've highlighted the two problem lines:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                    proc     nodev,noexec,nosuid                 0  0  
#Entry for /dev/sda6 :
UUID=191d2eac-f94d-4b90-9602-f1c66de131b6  /                        ext4     errors=remount -ro                           0  1  
[color=red]#Entry for /dev/sdb5 :
UUID=50747F3E747F263E                      /media/Arif\040Catalyst  ntfs-3g  defaults,nosuid,nodev,locale=en_IN  0  0[/color]  
#Entry for /dev/sda1 :
UUID=2A80A34780A31879                      /media/sda1              ntfs-3g  defaults,locale=en_IN               0  0  
#Entry for /dev/sda5 :
UUID=7228FDC428FD877F                      /media/sda5              ntfs-3g  defaults,locale=en_IN               0  0  
#Entry for /dev/sda8 :
UUID=F6A04FBEA04F83D9                      /media/sda8              ntfs-3g  defaults,locale=en_IN               0  0  
[color=green]UUID=2337-C493                                                                                                   0  1  [/color]
#Entry for /dev/sda7 :
UUID=1c6662d6-245b-4ce3-af9b-34e9663bb02c  none                     swap     sw                                  0  0  


/dev/sda6                                  /media/sda6              ext4     defaults                            0  0  
```

The lines in red refer to a partition that does not exist and the line in green is malformed, and I don't think you want to mount that partition anyway. Remove those two lines and save. Reboot and see if that helps.

---

