---
title: "Issue with Windows 7 DualBoot"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by kennethlin on 2012-05-04
Hi!

So I'm new to Ubuntu and after a week or so of contemplation and deep introspection, I decided to install Ubuntu 12.04 alongside my Windows 7 installation. I created a USB boot drive and installed it no problem. However, after messing around a bit (just with the environment, not with any of the partitions and whatnot), I realized that I couldn't boot into Windows. Specifically, after attempting the Windows boot option, the screen simply stalls at a black screen with only a blinking underscore-cursor. I've read issues of the sort in other threads but none specific to what I'm experiencing.

Of note is that the option to boot Windows says that it's in /dev/sda2. Is this the cause of my issues, because Windows was installed before Ubuntu? I tried reinstalling Ubuntu entirely over the original install, but that didn't work either. Suggestions online suggested I try fdisk -l and whatnot but the command outputs nothing whatsoever.

Searching elsewhere, I found this bootinfoscript thing that I decided to run to diagnose what was wrong. Could someone help me figure out what's wrong here?


                  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 707646248 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    33,845,247    33,843,200  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,845,248    34,050,047       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          34,050,048   664,311,161   630,261,114   7 NTFS / exFAT / HPFS
/dev/sda4         664,311,806   976,771,071   312,459,266   5 Extended
/dev/sda5         964,364,288   976,771,071    12,406,784  82 Linux swap / Solaris
/dev/sda6         664,311,808   964,364,287   300,052,480  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8A168F7F168F6B51                       ntfs       Recovery
/dev/sda2        E472476C72474292                       ntfs       System Reserved
/dev/sda3        E41A48CC1A489E04                       ntfs       Everything
/dev/sda5        e7f5a3ae-10e0-49b1-82f5-7abd67e2c162   swap       
/dev/sda6        6eefaaca-20db-491c-b3ea-c33728786d70   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
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
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=6eefaaca-20db-491c-b3ea-c33728786d70 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    echo    'Loading Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=6eefaaca-20db-491c-b3ea-c33728786d70 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=6eefaaca-20db-491c-b3ea-c33728786d70 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=6eefaaca-20db-491c-b3ea-c33728786d70 ro recovery nomodeset 
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
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 6eefaaca-20db-491c-b3ea-c33728786d70
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 8A168F7F168F6B51
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root E472476C72474292
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6eefaaca-20db-491c-b3ea-c33728786d70 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e7f5a3ae-10e0-49b1-82f5-7abd67e2c162 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  0e 60 5d 4b fd 06 f4 62  a3 ff f0 b2 9a 74 a2 ba  |.`]K...b.....t..|
00000010  01 3a 3b 29 5d 59 13 81  ff ef f9 66 a6 5d 98 07  |.:;)]Y.....f.]..|
00000020  dc a0 bf 50 17 24 12 0d  ab a8 c3 67 16 13 1e 7b  |...P.$.....g...{|
00000030  c9 49 e1 7d 57 90 67 5c  7f df 8f 8b d8 b7 f7 7a  |.I.}W.g\.......z|
00000040  6b d9 93 c0 bd 01 fe 84  e6 03 b2 47 2a 91 68 c8  |k..........G*.h.|
00000050  b9 b8 9d d5 ec ca 63 a9  1d 32 cd 66 41 d8 c1 3c  |......c..2.fA..<|
00000060  b0 bd 47 82 f7 2d 14 92  22 00 89 dc 8b 86 15 2e  |..G..-..".......|
00000070  24 af 25 8b 65 cb 79 0f  22 11 02 01 a8 fb 73 c5  |$.%.e.y.".....s.|
00000080  72 fc e1 c9 e4 b3 58 e7  b7 ce cf f5 cf e9 ba 3e  |r.....X........>|
00000090  d6 3f 77 e2 f1 a2 3e 6c  9c 98 ab 7f 3c 93 d5 d6  |.?w...>l....<...|
000000a0  4f cc 7d 34 85 eb 78 1f  4d 5d 8d a5 5f 37 2c f0  |O.}4..x.M].._7,.|
000000b0  fd b1 38 e8 40 ac fb 8c  13 0a 5d 8d f1 31 3e 2e  |..8.@.....]..1>.|
000000c0  9c 43 ee 75 cb 02 ee 83  a3 ec 05 97 bb 37 d2 1a  |.C.u.........7..|
000000d0  19 bc b5 f5 8d 56 f0 fd  ab 65 3e 1e 8c e5 47 dc  |.....V...e>...G.|
000000e0  3f dc 19 bc 3d f2 e4 10  cf 4f 86 e6 87 80 ff b1  |?...=....O......|
000000f0  b1 de 6e d0 ff 89 b3 7c  2f f0 0f dc c7 e3 c8 7f  |..n....|/.......|
00000100  28 1e 0f 3d d1 cd 75 15  cb bb c3 5c 27 fa ff 32  |(..=..u....\'..2|
00000110  7f 11 f8 2f 0f 97 f9 f7  9b be 59 37 0c 82 e0 2b  |.../......Y7...+|
00000120  75 bf fc ec ee ee 2e 9d  ff 41 5f 89 fd bf e3 ad  |u........A_.....|
00000130  c7 8f 23 ff 1d b2 26 e3  7d df f1 7e 00 9f e2 ff  |..#...&.}..~....|
00000140  48 85 ff 53 cd 9f dc 07  14 04 41 53 33 f0 ef 6d  |H..S......AS3..m|
00000150  f2 37 a1 ff 07 9b a0 62  fd 87 f2 a9 e2 3e 00 46  |.7.....b.....>.F|
00000160  e2 58 dc 07 84 f7 47 c6  7d 00 16 18 03 9c 03 9e  |.X....G.}.......|
00000170  4e 27 d2 b8 0e c0 49 95  fa af d9 85 3c fa 00 89  |N'....I.....<...|
00000180  9e 07 86 e7 81 48 ca 47  a0 03 70 3e a0 2e 65 cd  |.....H.G..p>..e.|
00000190  9a 66 de ec 87 48 d4 d6  8e e7 96 da 92 81 e8 d9  |.f...H..........|
000001a0  b3 b8 9f ea f8 e5 cb 97  31 16 7f 6c 90 6b 90 0f  |........1..l.k..|
000001b0  4c d3 6e 2f 64 fb 53 79  c1 a1 3a 00 ca 3d 00 fe  |L.n/d.Sy..:..=..|
000001c0  ff ff 82 fe ff ff 02 70  e2 11 00 50 bd 00 00 fe  |.......p...P....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 70 e2 11 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

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

### Post by 2ta8gdfte on 2012-05-04
Not a big problem you have grub in the sda2 partition, you can use testdisk to fix this generally follow this link.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Do you have a windows recovery or install disc to reload the Windows boot to the mbr if needed as well?

---

### Post by kennethlin on 2012-05-04
> **2ta8gdfte said:**
> Not a big problem you have grub in the sda2 partition, you can use testdisk to fix this generally follow this link.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Do you have a windows recovery or install disc to reload the Windows boot to the mbr if needed as well?

Before installing I made a Windows recovery USB as well. I will try that in a second while I restart my computer, because I just tried using boot-repair. Here are the results:

[http://paste.ubuntu.com/968312/](http://paste.ubuntu.com/968312/)

---

### Post by oldfred on 2012-05-04
Added code tags. You can highlight like copying and click on the # in the edit panel above you message to add code tags.

The boot repair is the same info as the bootscript plus a little more as it runs the boot info script as part of its Boot-Info.

The testdisk repair asw posted by 2ta8gdfte works well if you have only overwritten the PBR partition boot sector once. Windows keeps a backup of the PBR and the procedure recovers that backup. Only if you overwrote more than once, will you need the Windows repair tools.

---

### Post by kennethlin on 2012-05-04
So boot-repair didn't work, but it created a new Windows Recovery boot option on /dev/sda3. I tried loading this one but it told me something along the lines of Windows hardware boot failed. Insert your recovery disk to recover. I'll try the link you suggested right now.

---

### Post by kennethlin on 2012-05-04
> **oldfred said:**
> Added code tags. You can highlight like copying and click on the # in the edit panel above you message to add code tags.

The boot repair is the same info as the bootscript plus a little more as it runs the boot info script as part of its Boot-Info.

The testdisk repair asw posted by 2ta8gdfte works well if you have only overwritten the PBR partition boot sector once. Windows keeps a backup of the PBR and the procedure recovers that backup. Only if you overwrote more than once, will you need the Windows repair tools.

I'm sorry, but what is the PBR partition boot sector? I'm guessing this was the partition for the Ubuntu installation?

---

### Post by kennethlin on 2012-05-04
Sorry for the multiple posts, but here's an update from the testdisk utility:

```
TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
     Partition                  Start        End    Size in sectors
 2 * HPFS - NTFS           2106 196 11  2119 131 60     204800 [System Reserved]

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.




>[  Quit  ]  [  List  ]  [Rebuild BS]  [Repair MFT]  [  Dump  ]
                            Return to Advanced menulink@nietzsche:~$ 

```

The sourcefourge page suggests that this means I have some other sort of problem?

---

### Post by 2ta8gdfte on 2012-05-04
You are in good hands with oldfred, I learned everything I know in this area from them and some others on this site, carry on. :)

---

### Post by kennethlin on 2012-05-05
Thanks a ton! The testdisk method worked after Windows did a bit of checking for disk consistency.

---

### Post by 2ta8gdfte on 2012-05-05
> **kennethlin said:**
> Thanks a ton! The testdisk method worked after Windows did a bit of checking for disk consistency.

Cool, you can also boot from the sda3 now, if you put the bootflag on the sda3 if you have problems from the sda2 again. Not sure if it would pickup the recovery part in sda1 though, probably. You may see it now in the grub menu the recovery boot be careful.

---

### Post by oldfred on 2012-05-05
PBR is partition boot sector or the first sector of a partition reserved for boot code, like the MBR is the first sector of the hard drive. 
NTFS has to have its code in NTFS partition's boot sector.

Testdisk as you posted shows boot sector and backup as identical. Did Boot-Repair fix it. I have not used Boot-Repair to do that. May have to check with Yanni to see if he added that function.

---

