---
title: "Can't load windows 7 upon choosing from grub menu(ubuntu 11.10)"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by dotalovesme on 2011-11-14
Hello,

I installed ubuntu 11.10 on another hard drive (slave) and it works fine.
I managed to show the grub menu on boot but when i choose windows 7 loader, it doesn' load w7.
It simply shows a blinking underscore and nothing happens after that.

Please help me with this matter.


PS.

Windows 7 was my main OS when I installed ubuntu using USB LIVE boot.
Ubuntu is now installed on a separate hard drive.


Thanks in advance! :(

---

### Post by Mark Phelps on 2011-11-14
> **dotalovesme said:**
> Hindows 7 was my main OS when I installed ubuntu using USB LIVE boot. Ubuntu is now installed on a separate hard drive.(

Yeah ... but you most probably STILL had the Win7 drive connected when you installed Ubuntu, and if Ubuntu saw it as the FIRST drive in the system, it installed GRUB to that drive -- effectively, hosing up your Win7 boot.

The folks who support Boot Repair claim it can fix Windows boot issues.  It's free and is worth a try.  Download from the link below, burn a CD, and try it:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If that doesn't work, your other option is to use a Win7 Repair CD, but you have to purchase those CD images now.

---

### Post by dotalovesme on 2011-11-14
@mark helps: thanks i will try the link you gave. I will post updates here as soon as possible...thanks!

---

### Post by dotalovesme on 2011-11-15
the method failed.

I already submitted a ticket to boot.repair thru email

waiting for reply.

i ll post updates soon...

---

### Post by Quackers on 2011-11-15
Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
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

### Post by dotalovesme on 2011-11-15
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for .
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /menu.lst /grldr /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd 
                       /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /GRLDR /ntldr 
                       /NTLDR /NTDETECT.COM /ntdetect.com

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        /menu.lst

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1          25,270,272    78,241,791    52,971,520  83 Linux
/dev/sda2          19,533,822    25,270,271     5,736,450   5 Extended
/dev/sda5          19,533,824    23,439,359     3,905,536  82 Linux swap / Solaris
/dev/sda3                  63    19,518,974    19,518,912  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    62,075,159    62,075,097   7 NTFS / exFAT / HPFS
/dev/sdb2          62,075,160   312,560,639   250,485,480   f W95 Extended (LBA)
/dev/sdb5          62,075,223   312,557,913   250,482,691   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8016 MB, 8016363520 bytes
154 heads, 11 sectors/track, 9242 cylinders, total 15656960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  32    15,656,959    15,656,928   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        d79743e4-8f98-4360-ba66-4dd9b5d8bee7   ext4       
/dev/sda3        7a3fa479-9b3b-4771-8d89-ae089203ac64   ext4       New Volume
/dev/sda5        a07e055b-47a3-4254-9b18-33430610e6df   swap       
/dev/sdb1        2E9C19D69C199A03                       ntfs       
/dev/sdb5        30FCD6BEFCD67D92                       ntfs       alur
/dev/sdc1        7A15-D5AE                              vfat       JASARIE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/2E9C19D69C199A03  ntfs       (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)


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
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_PH
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d79743e4-8f98-4360-ba66-4dd9b5d8bee7 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d79743e4-8f98-4360-ba66-4dd9b5d8bee7 ro recovery nomodeset 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root d79743e4-8f98-4360-ba66-4dd9b5d8bee7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 2E9C19D69C199A03
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
# / was on /dev/sdb1 during installation
UUID=d79743e4-8f98-4360-ba66-4dd9b5d8bee7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c92d275c-e67b-471b-b9f2-9788b6d488bb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  26.423400879 = 28.371910656   boot/grub/core.img                             1
  16.174957275 = 17.367728128   boot/grub/grub.cfg                             1
  12.945217133 = 13.899821056   boot/initrd.img-3.0.0-12-generic               1
  32.242015839 = 34.619600896   boot/vmlinuz-3.0.0-12-generic                  1
  12.945217133 = 13.899821056   initrd.img                                     1
  32.242015839 = 34.619600896   vmlinuz                                        1

================================ sdb1/menu.lst: ================================

--------------------------------------------------------------------------------
# menu.lst produced by grb4dosconf
color white/blue black/cyan white/black cyan/black
timeout 10
default 0

#title Puppy Linux 112 frugal in sdb2 dir puppy112
 # find --set-root --ignore-floppies /puppy112/initrd.gz
 # kernel /puppy112/vmlinuz pmedia=atahd psubdir=puppy112 nosmp
 # initrd /puppy112/initrd.gz
  
title Windows Vista/2008/7
  find --set-root --ignore-floppies /bootmgr
  chainloader /bootmgr

#title Windows NT/2000/XP
 # find --set-root --ignore-floppies /ntldr
 # chainloader /ntldr

#title Windows 9x/Me
 # find --set-root /io.sys
 # chainloader /io.sys

title Grub4Dos commandline\n(for experts only)
  commandline

title Reboot computer
  reboot

title Halt computer
  halt
--------------------------------------------------------------------------------

========================== sdb1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1
            ?? = ??             vmlinuz                                        1

================================ sdb5/menu.lst: ================================

--------------------------------------------------------------------------------
# menu.lst produced by grb4dosconf
color white/blue black/cyan white/black cyan/black
timeout 10
default 0

title Puppy Linux 112 frugal in sdb2 dir puppy112
  find --set-root --ignore-floppies /puppy112/initrd.gz
  kernel /puppy112/vmlinuz pmedia=atahd psubdir=puppy112 nosmp
  initrd /puppy112/initrd.gz
  
title Windows Vista/2008/7
  find --set-root --ignore-floppies /bootmgr
  chainloader /bootmgr

#title Windows NT/2000/XP
 # find --set-root --ignore-floppies /ntldr
 # chainloader /ntldr

#title Windows 9x/Me
 # find --set-root /io.sys
 # chainloader /io.sys

title Grub4Dos commandline\n(for experts only)
  commandline

title Reboot computer
  reboot

title Halt computer
  halt
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  04 8a 84 93 82 4e 71 fc  ea 65 77 a1 3c ba 6d a0  |.....Nq..ew.<.m.|
00000010  89 77 82 17 03 38 a5 69  9c 64 02 47 af 14 de cc  |.w...8.i.d.G....|
00000020  85 29 74 42 14 72 32 01  ab 11 ab 2e 1f 9e 69 5e  |.)tB.r2.......i^|
00000030  e8 de 31 7b b2 da 29 27  8c d4 e2 dd 94 1c 82 33  |..1{..)'.......3|
00000040  eb 59 f5 3a 63 4e e4 8b  bf 19 5e 29 c9 70 79 c9  |.Y.:cN....^).py.|
00000050  cd 0b a9 b2 7c ad 2b e8  4d bc b0 c6 78 c5 7b 07  |....|.+.M...x.{.|
00000060  c0 dd 3d 2e 7c 61 a5 6f  1f ea bc d9 07 e0 9f fd  |..=.|a.o........|
00000070  7a ea c3 2f df 45 79 9c  d8 95 fb ba 92 fe eb 3f  |z../.Ey........?|
00000080  42 e3 8d 62 05 d8 72 73  d6 a8 c5 71 b6 56 25 7b  |B..b..rs...q.V%{|
00000090  66 be 8f a9 f2 28 e5 bc  45 71 66 27 59 ee df 62  |f....(..Eqf'Y..b|
000000a0  aa 71 9e 3f 9d 78 df 8b  fc 70 de 5b d9 58 c9 18  |.q.?.x...p.[.X..|
000000b0  12 a1 53 c0 e4 1a 6d 7b  a5 27 af cc f8 c3 c4 1a  |..S...m{.'......|
000000c0  61 d3 b5 09 60 2b b4 13  b8 7e 35 9a b8 c6 47 73  |a...`+...~5...Gs|
000000d0  5f 03 5e 3c b5 64 bc d9  f7 14 27 cd 4a 2f c8 91  |_.^<.d....'.J/..|
000000e0  1c 8c 1a f6 bf 01 ea b1  b5 b4 90 49 92 53 a0 f6  |...........I.S..|
000000f0  af 6f 28 9d ab a5 dd 1e  66 65 1e 6a 32 7d 9d cf  |.o(.....fe.j2}..|
00000100  5a 87 5f 1e 4f 95 8c 9e  d5 53 4d b9 db 7c c3 03  |Z._.O....SM..|..|
00000110  e7 af b9 76 dc f8 a5 a1  a9 aa df 79 92 a4 40 28  |...v.......y..@(|
00000120  18 e7 15 8d e5 e1 b8 1c  66 a5 d8 49 b3 73 4c 63  |........f..I.sLc|
00000130  1b 0f ad 76 e5 c4 90 90  c3 3c 73 50 91 6d 9f 21  |...v.....<sP.m.!|
00000140  f8 b3 4d 16 9a b5 cc 00  1c 6e dc 3e 86 a8 69 da  |..M......n.>..i.|
00000150  7f 9a e4 0e 42 a9 26 be  23 13 1b 55 9a f3 67 d8  |....B.&.#..U..g.|
00000160  d1 95 e9 c1 f9 23 1b c4  17 81 11 a2 5f ca bc 6b  |.....#......_..k|
00000170  51 46 62 5c 8e f5 e3 2d  5d cf 79 af 75 7a 1e c7  |QFb\...-].y.uz..|
00000180  fb 3d f8 74 5d ea 77 5a  bc ab fb bb 40 51 72 3f  |.=.t].wZ....@Qr?|
00000190  88 8f f3 fa d7 d9 9f 68  21 72 3a 62 bd 1a 5f 09  |.......h!r:b.._.|
000001a0  f3 78 99 5e a3 3e 4c f8  b9 e2 a3 7b 34 96 e8 df  |.x.^.>L....{4...|
000001b0  ba 8f e5 00 1e a6 be 69  4c 06 3d b9 35 85 00 fe  |.......iL.=.5...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 3b 00 00 00  |............;...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  f8 8f 7f 7f 3d 3b 81 3e  43 b1 c2 0b 11 e7 e1 90  |....=;.>C.......|
00000010  64 87 bc c0 f8 07 ad 99  a5 4b 88 33 5e 6b 72 8a  |d........K.3^kr.|
00000020  4e ec 47 4e 92 72 94 42  53 24 38 d2 4c 17 5b 66  |N.GN.r.BS$8.L.[f|
00000030  10 63 f5 4b 85 28 63 1d  58 55 ce b7 51 11 8a 84  |.c.K.(c.XU..Q...|
00000040  cc 58 74 f3 fc 60 1f 84  7f 7e 9c 68 3b c8 04 c7  |.Xt..`...~.h;...|
00000050  a3 f3 c4 1f 7b e9 ae 9d  35 06 f0 0c 7e 8d 13 32  |....{...5...~..2|
00000060  36 11 7c 64 18 59 b6 de  23 77 0a c6 ab 7d 65 12  |6.|d.Y..#w...}e.|
00000070  39 37 33 1d 89 0f d4 86  5b c9 b9 12 61 03 bc 67  |973.....[...a..g|
00000080  05 21 a0 16 b7 4a 82 95  71 94 41 15 12 19 17 3a  |.!...J..q.A....:|
00000090  4a ef ff f1 b7 c4 65 d5  11 02 c6 62 9f 72 71 1e  |J.....e....b.rq.|
000000a0  c0 ee d0 bd 8f 3f ef 08  ef df c0 72 80 e0 52 76  |.....?.....r..Rv|
000000b0  fc d5 12 22 e3 20 f7 36  ed b2 4d 1b 33 cd 85 34  |...". .6..M.3..4|
000000c0  98 d8 c8 78 0a 70 1e 1b  42 dd 2d 93 c1 8a b4 a7  |...x.p..B.-.....|
000000d0  a1 cd 73 db a3 ee 96 c3  9a c4 6a b4 91 25 1b 7c  |..s.......j..%.||
000000e0  46 5d 51 10 2c 66 29 f7  27 11 ec 0e ed 0b d8 f3  |F]Q.,f).'.......|
000000f0  fe f0 8e fd fc 07 28 0e  05 27 6f cd 51 22 2e 32  |......(..'o.Q".2|
00000100  0f 73 6e db 24 d1 b3 3c  d8 53 49 8d 8c 87 80 a7  |.sn.$..<.SI.....|
00000110  01 e1 b4 2d d2 d9 3c 18  ab 4a 7a 1c d7 3d ba 3e  |...-..<..Jz..=.>|
00000120  e9 6c 39 ac 46 ab 49 12  5f 2f b0 79 da f5 78 f7  |.l9.F.I._/.y..x.|
00000130  1e 1f 8d b2 3e 5e e0 f1  ee b2 84 bc 7b 32 38 27  |....>^......{28'|
00000140  3e 84 08 6f fa 1f e4 92  08 dc 9e 4f 73 8a 53 b6  |>..o.......Os.S.|
00000150  13 cf ec 88 d1 2b 8c c1  1f 9b 8a 38 97 94 88 dc  |.....+.....8....|
00000160  b9 9a 92 e1 44 55 0d 95  13 05 a2 59 91 8f 29 50  |....DU.....Y..)P|
00000170  41 83 24 e7 60 61 b7 c4  65 d5 11 02 c6 62 9f 72  |A.$.`a..e....b.r|
00000180  71 1e c0 ee d0 bd 8f 3f  ef 08 ef df c0 72 80 e0  |q......?.....r..|
00000190  52 76 fc d5 12 22 e3 20  f7 36 ed b2 4d 1b 33 cd  |Rv...". .6..M.3.|
000001a0  85 34 98 d8 c8 78 0a 70  1e 1b 42 dd 2d 93 c1 8a  |.4...x.p..B.-...|
000001b0  b4 a7 a1 cd 73 db a3 ee  96 c3 9a c4 6a b4 00 fe  |....s.......j...|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 03 10 ee 0e 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 cc 08  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e0 e7 ee 00 9a 3b 00 00  00 00 00 00 02 00 00 00  |.....;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 ae d5 15 7a 4e  4f 20 4e 41 4d 45 20 20  |..)...zNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument
FIBMAP: Invalid argument

```oh the contents are very long... :/

i just learned that this is the same file with the content here using boot.repair --->[ http://paste.ubuntu.com/739296/]("http://paste.ubuntu.com/739296/")

---

### Post by Mark Phelps on 2011-11-15
Don't want to upstage Quackers ... but it looks like sdb is a real mess.  You have both GRUB there and the Win7 boot loader -- which, in that past, has resulted in Win7 being confused and unable to boot.

Since /grldr is there, you have now (or have had) a Wubi install -- since that is where it writes its boot loader (GRUB4DOS).  But it also looks like you have BOTH versions of GRUB -- since there are menu.lst files lying around as well.

Plus, you have more versions of "boot" there than I have ever seen!

My suggestions below presume you have a Win7 Repair CD with which to restore the Win7 boot loader ...

At the very least, I would mount the Windows OS partition and remove ALL the boot folders and boot files there.  Also, would remove all the grldr folders.  And, I would remove the menu.lst file from /sdb5.

Once those are gone, I would shutdown the PC, disconnect the Ubuntu drive, reboot with the Win7 Repair CD in the drive -- and run startup repair three times.  That will reinstall the boot loader components and should get Win7 booting again.  

Then I would reconnect the Ubuntu drive, boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This will regenerate the GRUB menu and after that, when you reboot, you should be able to boot into either OS.

But ... Quackers may have better suggestions.  Suggest you wait for them to reply.

---

### Post by Quackers on 2011-11-15
Wow! That's a lot of boot files in sdb1
```
sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        [COLOR="Red"]/menu.lst /grldr[/COLOR] /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd 
                       /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD 
                       /Windows/System32/winload.exe [COLOR="Red"]/grldr /GRLDR[/COLOR] /ntldr 
                       /NTLDR /NTDETECT.COM /ntdetect.com
```

All the files in red should not be there, I think.
I'm also not convinced that all the /boot/bcd and /boot/BCD files should be there either.

Do you have a Windows 7 repair disc?


EDIT  Also please see Mark Phelps's post one up :-)

---

### Post by dotalovesme on 2011-11-15
oh my GOD. you mean I should buy those Windows 7 Repair Disk???
I don't want to spend money for windows anymore.
Is there away to download those image files for free?

Thanks

---

### Post by dotalovesme on 2011-11-15
I think you both need an explanation why there are a lot of boot files in sdb.

2 years ago I have my W7 installed.
Suddenly I tried wubi ubuntu install and removed it( i don't know if it was really removed)
Then, I was amazed by this Linux Puppy Version so I tried it that's why another boot file is created in sdb.
Now, I installed Ubuntu 11.10 without knowing that there are already messes inside sdb...

>.< feels like im much dumber now.

---

### Post by Quackers on 2011-11-15
It's not a recovery dvd that you need to buy.
It's a repair cd. One can be downloaded (I think they are about 270MB iirc) and can be burned as an image to a cd.
Sadly the links that I used to give for them have now started charging. If you google for a repair disc I'm sure they are still available.
You must get one that matches your architecture - ie if you have a 32 bit system you need a 32 bit repair cd and if you have a 64 bit system you need a 64 bit image.

EDIT  In answer to your last post I can assure you that I have no idea why so many boot files are in sdb1. It is possible that all your previous installations have left some behind, maybe.
There sure are loads of them :-)

---

### Post by dotalovesme on 2011-11-15
oh I remembered using A USB Repair Disk for Windows 7 when I installed Linux Puppy years ago but sadly, I can't find a free download for that LIVE USB Repair. sighs* I guess I need to say goodbye to my W7 for now...

---

### Post by itismike on 2011-11-15
> **dotalovesme said:**
> oh my GOD. you mean I should buy those Windows 7 Repair Disk???Just borrow one from a friend. Make sure it's the same version as yours: "Home Premium" or whatever. Disconnect the drive with Ubuntu and get your Windows system operational again. Nobody should be forced into becoming a Linux user! It should be a mutual attraction :)

---

### Post by Quackers on 2011-11-15
If you have another pc (or a friend does) with either Win 7 or even Vista with the same architecture (32 bit/64 bit) you can make a repair disc from that system wich can be used to repair your boot sector.
It should be repairable.

---

### Post by oldfred on 2011-11-15
It might not need the Windows repairCD, but if you have Windows installed you should have one.

Windows is not case sensitive so everyone of the duplicate entires is a problem that prevents Window from working. But I am not sure which /boot/BCD for example may be the correct working one. You may have to copy all of them and try each to see which works. But you should only have one each of these, regardless of case.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You have for just the BCD but some of the other boot files are also duplicated. Only one may be correct, if none are correct then you will need repairCD:

[COLOR=Red]/boot/bcd /BOOT/bcd /Boot/bcd /boot/BCD /BOOT/BCD /Boot/BCD [/COLOR]

---

### Post by dotalovesme on 2011-11-15
googled some ways while ago and found some.

1. I need to create a USB Live Disk.
2. If creating that is successful, I will boot from USB
3. Repair my w7 installation


I have questions:
--> Should I remove the hard drive which I installed Ubuntu before doing the repair for windows?
--> After repairing what should I do for me to use ubuntu anytime?

Thanks a lot!

---

### Post by dotalovesme on 2011-11-15
> **Mark Phelps said:**
> 
My suggestions below presume you have a Win7 Repair CD with which to restore the Win7 boot loader ...

At the very least, I would mount the Windows OS partition and remove ALL the boot folders and boot files there.  Also, would remove all the grldr folders.  And, I would remove the menu.lst file from /sdb5.

Once those are gone, I would shutdown the PC, disconnect the Ubuntu drive, reboot with the Win7 Repair CD in the drive -- and run startup repair three times.  That will reinstall the boot loader components and should get Win7 booting again.  

Then I would reconnect the Ubuntu drive, boot into Ubuntu, open a terminal, and enter "sudo update-grub".  This will regenerate the GRUB menu and after that, when you reboot, you should be able to boot into either OS.

But ... Quackers may have better suggestions.  Suggest you wait for them to reply.


I will try this suggestion...

I will update you all soon.

---

### Post by Quackers on 2011-11-15
There are 2 choices, but others may disagree :-)
You can leave everything connected but make sure that /dev/sdb is the first bootable HDD in your bios, then repair the Windows boot sector.
OR you can disconnect the Ubuntu drive then repair the Windows boot sector.

If Windows becomes bootable again you can then re-connect the Ubuntu drive (if necessary) and make that the first bootable HDD and when Ubuntu boots you can run ```
sudo update-grub
``` which should find Windows on /dev/sdb.

---

### Post by dotalovesme on 2011-11-15
Thanks @Quackers!


You all rock in here...Thanks I should hug my pillow now...zzz

---

### Post by Quackers on 2011-11-15
Sleep well and prepare for tomorrow :-)

---

