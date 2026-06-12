---
title: "GRUB loading Error 15"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by luny022 on 2012-07-01
Hi! Kind of new to Ubuntu.  Used a few years ago, but somehow corrupted my ubuntu installation a couple years back and had just been using Windows.  Know just enough to get in trouble :)
Just reinstalled Ubuntu using a boot-up CD.  I have my hard drive partitioned with Windows OS and Ubuntu, so was just trying to update Ubuntu.  I now get the GRUB loading Error 15 when I try to boot up computer.  
I used boot info script' and am attaching results below.
Thanks in advance for your help!

```

                Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 124605338 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       13253562 sectors.. But according to the info from the 
                       partition table, it has 13237496 sectors.
    Operating System:  Windows 98
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 NTFS / exFAT / HPFS
/dev/sda2          81,915,496   149,115,329    67,199,834   5 Extended
/dev/sda5          81,915,498   145,918,394    64,002,897  83 Linux
/dev/sda6         145,918,458   149,115,329     3,196,872  82 Linux swap / Solaris
/dev/sda3         149,115,330   156,232,124     7,116,795  db CP/M / CTOS / ...


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 6800 MB, 6800080896 bytes
255 heads, 63 sectors/track, 826 cylinders, total 13281408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    13,237,559    13,237,497   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        62E0EDD9E0EDB407                       ntfs       
/dev/sda3        4524-4EA1                              vfat       DellRestore
/dev/sda5        b327230a-77ed-4e7a-85ab-6f7ac9ebe12b   ext4       
/dev/sda6        57505dc0-eae8-4ec7-b429-aea11933ff3a   swap       
/dev/sdb1        0F57-17DB                              vfat       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/62E0EDD9E0EDB407  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/b327230a-77ed-4e7a-85ab-6f7ac9ebe12b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/0F57-17DB         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=b327230a-77ed-4e7a-85ab-6f7ac9ebe12b ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=b327230a-77ed-4e7a-85ab-6f7ac9ebe12b ro recovery nomodeset 
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
    search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root b327230a-77ed-4e7a-85ab-6f7ac9ebe12b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 62E0EDD9E0EDB407
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
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b327230a-77ed-4e7a-85ab-6f7ac9ebe12b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=57505dc0-eae8-4ec7-b429-aea11933ff3a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  00 d7 fe 46 b9 33 5b 7b  7b 45 e8 9b 7a ee 95 97  |...F.3[{{E..z...|
00000010  4d f4 b9 d2 d4 62 d5 d2  be 9b af 4f c8 c0 99 64  |M....b.....O...d|
00000020  49 1a 33 16 72 df 78 9f  53 9f fe bd 3d e5 43 01  |I.3.r.x.S...=.C.|
00000030  8d f0 59 06 08 04 67 bf  41 eb fe 7d 6b c6 aa fd  |..Y...g.A..}k...|
00000040  d0 a5 27 29 19 8f 2a 30  06 dd 3c b1 11 19 27 e6  |..')..*0..<...'.|
00000050  66 ec 7f 5e 7b f7 fa 52  30 3e 6a 49 3f c8 1c 82  |f..^{..R0>jI?...|
00000060  a3 3f 29 3d 79 ed cf a7  e7 d2 b9 a5 26 8e b7 1b  |.?)=y.......&...|
00000070  c4 dd 68 d8 c4 24 91 c2  82 bf 28 3f 4e 02 f6 ff  |..h..$....(?N...|
00000080  00 0a 81 16 d6 45 03 ef  cb 09 c9 24 e3 af 6c 7e  |.....E.....$..l~|
00000090  1c 9f a5 69 ed 12 a6 79  bc 8e 06 4e a5 6e 1d 77  |...i...y...N.n.w|
000000a0  81 c6 78 0b c1 04 7a 9f  ad 73 b2 c9 1a 0f 2e e0  |..x...z..s......|
000000b0  82 cc 08 52 46 70 a3 8a  d2 1a c2 3e 68 b4 d4 a2  |...RFp.....>h...|
000000c0  fa bb 3b e9 af 5b 74 2b  41 6f 32 91 22 36 fb 72  |..;..[t+Ao2."6.r|
000000d0  d8 1c f3 8f a7 e3 8c fa  55 99 f4 e5 9a 36 91 76  |........U....6.v|
000000e0  c6 ea a5 98 e7 39 c7 1c  0f 5f 7a 49 a8 cb 96 d7  |.....9..._zI....|
000000f0  da fa ee 9d ba 7e 06 71  a5 28 ea d6 fe 9d df f9  |.....~.q.(......|
00000100  19 96 f1 49 1c bb 18 6f  52 3d 4e 33 ce 3f cf af  |...I...oR=N3.?..|
00000110  e3 53 dc e9 72 91 f6 91  0e 00 c9 07 b1 c7 41 9f  |.S..r.........A.|
00000120  5c fe 55 a6 8d f2 dd 3b  b5 fd 58 b8 c2 f7 bd d5  |\.U....;..X.....|
00000130  be 5f 99 36 93 3d db 48  61 9c 79 70 a1 c0 39 c9  |._.6.=.Ha.yp..9.|
00000140  23 b9 3f 4f 4f 7a de cd  a1 2c 3c ec b8 23 62 ed  |#.?OOz...,<..#b.|
00000150  e3 20 81 9c f4 ac e5 17  0d ae 97 5d 7f c8 d6 8a  |. .........]....|
00000160  8c 25 6b f6 56 b7 9f ea  4a 7c a9 25 51 21 2b 95  |.%k.V...J|.%Q!+.|
00000170  c1 63 ed c7 03 d3 a1 3d  2a b5 cc 28 55 80 c3 73  |.c.....=*..(U..s|
00000180  81 c6 01 1c f3 9a c2 17  75 0d 6a 35 73 39 ad 3c  |........u.j5s9.<|
00000190  c8 87 99 81 b0 e4 13 d4  63 a0 1e 9d 7b 62 a6 91  |........c...{b..|
000001a0  a4 b7 54 75 7c ab 2f 00  1c 95 03 1d 4f af b5 6f  |..Tu|./.....O..o|
000001b0  57 73 96 30 20 90 34 90  ab 33 85 cf 4f ef 00 fe  |Ws.0 .4..3..O...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 51 9b d0 03 00 fe  |..........Q.....|
000001d0  ff ff 05 fe ff ff 53 9b  d0 03 07 c8 30 00 00 00  |......S.....0...|
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
```

---

### Post by mapes12 on 2012-07-01
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by coffeecat on 2012-07-01
@luny022, this:

> **luny022 said:**
> 
```

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

<snip>

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 124605338 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos5)/boot/grub on this drive.
```

You must have told the installer to install grub to partition sda5, leaving a remnant of legacy grub in the mbr. This was a mistake. You need to install grub2 to the mbr, but this is easily done using the live 12.04 CD.

Boot up the live 12.04 and choose "try Ubuntu" to get to the live desktop. Open a terminal. Now:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

By the way, I've added code tags to your boot script output to make it easier to read.

---

### Post by luny022 on 2012-07-01
Thank You Coffeecat!  That worked beautifully!

---

