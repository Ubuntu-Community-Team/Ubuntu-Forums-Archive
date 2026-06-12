---
title: "MBR not modified by dual-boot &quot;Side by Side&quot; install?!?!"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by Draexo on 2012-07-18
I had used Wubi to install Ubuntu and it was suggested that instead I provide a dedicated partition using the bootable CD.  I removed the Wubi install and it no longer appeared in the Windows Boot Menu.   I booted from the CD and let the installer partition my drive (I gave it 250 gb, leaving 350GB for Windows 7).  I answered a bunch of questions, after which the install was supposed to exist "Side By Side" with Windows.  I took this as a dual boot situation.  Now I have 250GB less on my drive, but Ubuntu install, which copied many files, does not have a record in the boot record!  When it was finished, Ubuntu ejected the install CD and said to reboot.

Did I do something incorrect?  Can I manually add a record to the MBR?  Why did Ubuntu not add the record to the MBR yet it partitioned the drive and spent a while copying files over.

---

### Post by Draexo on 2012-07-18
I've received several errors.  One was that I did not have enough room on the disk.  Well, there are 250GB, I should think that is enough.  When I boot into Windows I now have all these little partitions that were not there before.  it looks like Ubuntu is ignoring the 250BG partition I set aside for it and trying to make a new partition, which it can not as it does not have the room, and then bombs.

---

### Post by Draexo on 2012-07-19
I have successfully installed the current version of Ubuntu with Wubi.  It was suggested to me that I remove Wubi and install dual-boot.  

I downloaded the 64 bit version of Ubuntu, put it on a disk, rebooted,   and followed the prompts for the "side by side" install.  Everything appears to go well.  The drive partitions are resized and the install proceeds fine.  When Ubuntu finishes, it ejects the DVD and says hit enter to reboot.

At that point in time, it will only reboot into Windows 7.  It does not offer me the option of booting into Ubuntu.  I can see that the drive is resized and that there is data on the drive, yet it appears the master boot record was not modified.  I know how to modify the MBR, but I do not know where to point it to in order for it to launch Ubuntu.

---

### Post by Draexo on 2012-07-19
Ok
After numerous installation attempts, I was able to solve this by using Neosmart's EasyBCD to manually add a boot record.  Now I have dual boot for both a full install Windows and a full install Ubuntu.

[http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/) in case you need the link.

---

### Post by Draexo on 2012-07-19
I solved this, but I do not think it should have been necessary for me to go to this step.  It was simple to fix, but I am not sure why the installer did not do it automatically.  Please see my other post here for my solution to this trouble.

[http://ubuntuforums.org/showthread.php?p=12114846#post12114846](http://ubuntuforums.org/showthread.php?p=12114846#post12114846)

---

### Post by coffeecat on 2012-07-19
Threads merged. Please do not create duplicate threads about the same issue.

> **Draexo said:**
> I solved this, but I do not think it should have been necessary for me to go to this step.

Normally the installer installs grub to the mbr for you and everything works fine. The only way I know of making that not happen is to tell the installer to install grub to a partition. Did you choose the "something else" option and override the default option for installing grub?

I see you have installed EasyBCD. Although that works well enough, many would think that not the best solution and better to rely on a correctly installed grub. If you would like help with that boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Please note that there is currently an error in the instructions on that page. The script file is now called bootinfoscript, and if moved to your desktop the command should be 'sudo bash ~/Desktop/bootinfoscript'.

The RESULTS.txt file will give an overview of your system and will help for re-installing grub.

---

### Post by Draexo on 2012-07-19
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /NST/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /boot/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    32,017,544    32,017,482  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     32,017,545 1,953,520,064 1,921,502,520   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    20,482,874    20,482,812  27 Hidden NTFS (Recovery Environment)
/dev/sdb2    *     20,484,096   793,883,642   773,399,547   7 NTFS / exFAT / HPFS
/dev/sdb3         793,884,670 1,250,263,039   456,378,370   5 Extended
/dev/sdb5         793,884,672 1,233,487,871   439,603,200  83 Linux
/dev/sdb6       1,233,489,920 1,250,263,039    16,773,120  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7AC0765EC0762115                       ntfs       PQSERVICE
/dev/sda2        E2B48232B48208ED                       ntfs       
/dev/sdb1        7AC0765EC0762115                       ntfs       PQSERVICE
/dev/sdb2        E2B48232B48208ED                       ntfs       
/dev/sdb5        5779a9f4-bdfb-4516-912a-7ca354fbc953   ext4       
/dev/sdb6        c079502e-1f3e-4125-b753-48de3eab43b0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


============================== sda2/NST/menu.lst: ==============================

--------------------------------------------------------------------------------
# NeoSmart NeoGrub Bootloader Configuration File 
# 
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst 
# Please see the EasyBCD Documentation for information on how to create/modify entries: 
# http://neosmart.net/wiki/display/EBCD/ 
 
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             NST/menu.lst                                   0

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=5779a9f4-bdfb-4516-912a-7ca354fbc953 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-26-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    echo    'Loading Linux 3.2.0-26-generic ...'
    linux    /boot/vmlinuz-3.2.0-26-generic root=UUID=5779a9f4-bdfb-4516-912a-7ca354fbc953 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-26-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5779a9f4-bdfb-4516-912a-7ca354fbc953 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=5779a9f4-bdfb-4516-912a-7ca354fbc953 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 5779a9f4-bdfb-4516-912a-7ca354fbc953
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 7AC0765EC0762115
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root E2B48232B48208ED
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 7AC0765EC0762115
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root E2B48232B48208ED
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5779a9f4-bdfb-4516-912a-7ca354fbc953 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c079502e-1f3e-4125-b753-48de3eab43b0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/initrd.img-3.2.0-26-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-26-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  fb bc 32 c7 5b 42 b4 bc  3c df 0b 68 0c a0 ad 20  |..2.[B..<..h... |
00000010  4e 28 d9 ee f5 f2 95 3f  57 6f 99 12 cc fe 59 f6  |N(.....?Wo....Y.|
00000020  99 3d 52 07 5b 36 21 3c  7d 27 bd 17 19 ac b0 07  |.=R.[6!<}'......|
00000030  c8 fa 28 3f 81 48 72 94  9f 65 bd 9a f7 10 94 34  |..(?.Hr..e.....4|
00000040  b2 2e 7f d6 67 4e 38 5b  e5 be c9 2e 69 db 6b 0d  |....gN8[....i.k.|
00000050  9d d8 8e 4a b4 e9 81 a7  5b 34 c3 b6 5e 4b a9 c5  |...J....[4..^K..|
00000060  c3 d7 18 87 d3 cc 19 f7  58 fe 67 b6 ff 1f 9f b1  |........X.g.....|
00000070  b6 47 f1 df 05 34 01 6f  89 ae 29 ab 6b 55 d2 91  |.G...4.o..).kU..|
00000080  d1 8d b2 c6 2f 65 07 5e  af ef af f4 07 4b 1f b3  |..../e.^.....K..|
00000090  97 bd ef 07 a4 b1 ba fd  0b 4e 19 10 b7 c3 67 d1  |.........N....g.|
000000a0  3e 69 23 16 f7 fd 4e 7d  e0 29 0f 4a 19 60 c2 07  |>i#...N}.).J.`..|
000000b0  11 0b ef a2 8e fd 71 e9  ca 42 d0 f6 08 b2 0d 92  |......q..B......|
000000c0  ba 65 2e 1a 9f 5d 2a a3  1a be b5 a1 2a 98 b3 ec  |.e...]*.....*...|
000000d0  e0 cb 9b 2e 83 72 a4 70  ee e1 fb da 31 40 28 57  |.....r.p....1@(W|
000000e0  6f 76 d2 cb 22 19 6f c3  92 36 e0 d2 2f db cc f8  |ov..".o..6../...|
000000f0  87 41 3d 20 70 32 66 25  05 ab 3e b5 97 02 37 be  |.A= p2f%..>...7.|
00000100  55 9e 55 40 72 b7 ca e3  97 60 12 4f 91 c7 0d c2  |U.U@r....`.O....|
00000110  6d 48 84 df 08 c4 16 33  b5 10 49 2b e4 bc 27 87  |mH.....3..I+..'.|
00000120  9a 60 01 74 66 43 31 f2  6f 23 86 a5 04 6c d0 e4  |.`.tfC1.o#...l..|
00000130  ce 26 1c 3b ef 57 5c 00  39 01 1a 32 06 6e 70 2f  |.&.;.W\.9..2.np/|
00000140  68 f6 1b 56 cd 94 11 00  79 4c 81 0f a8 11 a1 bc  |h..V....yL......|
00000150  1c d2 c5 23 2e b3 c5 ec  dc 20 e3 8e 13 cf ba db  |...#..... ......|
00000160  e4 16 01 d2 2c 23 a4 fe  bd 3f 4e 33 91 b6 d5 26  |....,#...?N3...&|
00000170  af d4 a7 90 f7 04 62 ed  82 b7 7a 4b be f7 34 b7  |......b...zK..4.|
00000180  f6 34 c0 34 0a 27 95 25  fd b0 b9 cc 3e 42 4f 57  |.4.4.'.%....>BOW|
00000190  4e 4e 86 9e 20 8d af cf  b7 d7 f4 0c 3b 89 9d 57  |NN.. .......;..W|
000001a0  e3 04 dd 86 ef 59 23 6c  5c e9 2c 00 e7 d3 b6 ec  |.....Y#l\.,.....|
000001b0  ac a9 c5 52 a4 bc e6 88  6a 1c c0 aa b6 11 00 fe  |...R....j.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 33 1a 00 fe  |............3...|
000001d0  ff ff 05 fe ff ff 02 d0  33 1a 00 f8 ff 00 00 00  |........3.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
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

```

---

### Post by Draexo on 2012-07-23
Does this mean anything to anyone???

---

### Post by oldfred on 2012-07-23
You did some sort of image copy from sda to sdb or vice versa. 

```
"blkid" output: _______________

Device UUID TYPE LABEL

/dev/sda1 [COLOR=Red]7AC0765EC0762115[/COLOR] ntfs PQSERVICE
/dev/sda2 [COLOR=Blue]E2B48232B48208ED[/COLOR] ntfs
/dev/sdb1 [COLOR=Red]7AC0765EC0762115[/COLOR] ntfs PQSERVICE
/dev/sdb2 [COLOR=Blue]E2B48232B48208ED[/COLOR] ntfs
/dev/sdb5 5779a9f4-bdfb-4516-912a-7ca354fbc953 ext4
/dev/sdb6 c079502e-1f3e-4125-b753-48de3eab43b0 swap 
```

You cannot have duplicate UUIDs. Not sure what Windows does, but Ubuntu gets very confused and may use one partition one time and next time the other. Then they get out of sync and major problems occur.

---

### Post by Draexo on 2012-07-23
> **oldfred said:**
> You did some sort of image copy from sda to sdb or vice versa. 

```
"blkid" output: _______________

Device UUID TYPE LABEL

/dev/sda1 [COLOR=Red]7AC0765EC0762115[/COLOR] ntfs PQSERVICE
/dev/sda2 [COLOR=Blue]E2B48232B48208ED[/COLOR] ntfs
/dev/sdb1 [COLOR=Red]7AC0765EC0762115[/COLOR] ntfs PQSERVICE
/dev/sdb2 [COLOR=Blue]E2B48232B48208ED[/COLOR] ntfs
/dev/sdb5 5779a9f4-bdfb-4516-912a-7ca354fbc953 ext4
/dev/sdb6 c079502e-1f3e-4125-b753-48de3eab43b0 swap 
```You cannot have duplicate UUIDs. Not sure what Windows does, but Ubuntu gets very confused and may use one partition one time and next time the other. Then they get out of sync and major problems occur.

This is all Greek to me!  I see what you say about UUID, but I am pretty sure that it was that way before I installed Ubuntu.  It seems to work ok now.

---

