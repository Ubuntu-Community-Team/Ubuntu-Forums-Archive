---
title: "Installed Unbuntu 11.10, now don't get option to load XP"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Face-Ache on 2012-01-02
Hi folks

I'm very new to this, and have installed Ubuntu 11.10 next to Windows XP. I let the the installer create the partition, 35gb of a 120gb drive, and now when the machine boots, i don't seem to have the option of booting to windows anywhere. Loving the OS, but also need XP for other reasons.

Can anyone please help?

Many thanks in advance  :)

My Boot Info Summary Results file is;

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Windows is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files:        /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   166,009,475   165,929,151   7 NTFS / exFAT / HPFS
/dev/sda3         166,010,878   234,373,119    68,362,242   5 Extended
/dev/sda5         166,010,880   230,182,911    64,172,032  83 Linux
/dev/sda6         230,184,960   234,373,119     4,188,160  82 Linux swap / Solaris


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1               2,048 2,930,277,167 2,930,275,120   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D3-080F                              vfat       DellUtility
/dev/sda2        1008631A0862FE5A                       ntfs       
/dev/sda5        437a26ab-2125-436e-b34d-1b55e6537e51   ext4       
/dev/sda6        a78b471e-70c9-4f41-b9c4-dd478118ee91   swap       
/dev/sdf1        42DC4CB4DC4CA44F                       ntfs       Elements

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/1008631A0862FE5A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdf1        /media/Elements          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /media/SHAKE_WEIGHT_TOTAL_BODY_DVD udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
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
search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
  set locale_dir=($root)/boot/grub/locale
  set lang=en_NZ
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
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=437a26ab-2125-436e-b34d-1b55e6537e51 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=437a26ab-2125-436e-b34d-1b55e6537e51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=437a26ab-2125-436e-b34d-1b55e6537e51 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=437a26ab-2125-436e-b34d-1b55e6537e51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
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
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 437a26ab-2125-436e-b34d-1b55e6537e51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 1008631A0862FE5A
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
UUID=437a26ab-2125-436e-b34d-1b55e6537e51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a78b471e-70c9-4f41-b9c4-dd478118ee91 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  2
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 4f 00  3f 00 ff 00 3f 00 00 00  |......O.?...?...|
00000020  86 39 01 00 80 00 29 0f  08 d3 07 44 65 6c 6c 55  |.9....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 00 55 aa  |    SYS.......U.|
00000200

Unknown BootLoader on sda3

00000000  26 db 79 5e 39 ed 39 aa  7b f0 58 e8 8d 97 f5 f6  |&.y^9.9.{.X.....|
00000010  f7 b8 1f 2f 68 77 f0 39  1a 6f 8f d1 8c cd a2 00  |.../hw.9.o......|
00000020  ac d2 68 3f 92 61 59 92  47 0a c0 85 1e 24 9b 82  |..h?.aY.G....$..|
00000030  b6 41 60 a8 94 c5 eb 79  55 5d 15 c2 9e 59 c0 c2  |.A`....yU]...Y..|
00000040  16 74 67 6f 50 75 37 3b  81 02 bf f8 d7 27 30 4b  |.tgoPu7;.....'0K|
00000050  2b 8f 45 70 5b c4 18 ce  b6 1a 3a 0f bd b8 98 0b  |+.Ep[.....:.....|
00000060  95 f1 9e c0 f5 9e 99 66  b6 4a b4 75 47 b8 de 17  |.......f.J.uG...|
00000070  7b 2e c0 3e 6a 48 86 72  c5 2b a0 16 16 27 9a fb  |{..>jH.r.+...'..|
00000080  b0 db 1f b3 81 18 50 0d  6e 73 bd 6c dd 42 35 cf  |......P.ns.l.B5.|
00000090  a0 ef 5b 65 05 62 3a 5b  d3 e8 de 13 e0 7f ed bc  |..[e.b:[........|
000000a0  4e 6b ff d0 2b f1 ae ad  24 d0 ad fc 45 0d 26 c7  |Nk..+...$...E.&.|
000000b0  62 a7 99 89 a5 a8 ee cb  43 10 b3 9b fb ac 5d c8  |b.......C.....].|
000000c0  ff 7b a2 7c 8f 99 1d ff  0b bd 05 8f 4b e0 1e e8  |.{.|........K...|
000000d0  c6 3d a0 58 7a c2 5d 2b  bf 51 b1 1a 92 7b 9d e4  |.=.Xz.]+.Q...{..|
000000e0  ea bc b2 83 bc ef 39 59  28 fb 57 2c 45 52 35 56  |......9Y(.W,ER5V|
000000f0  39 a3 20 3f a1 c1 25 a6  9c a5 a3 7a 6f c6 a8 fe  |9. ?..%....zo...|
00000100  de 01 6a 80 50 64 e7 41  ea ae 01 e2 05 26 72 cb  |..j.Pd.A.....&r.|
00000110  6c f0 2f 43 80 ab 24 5d  4e 38 f7 0c 33 1c ac 7c  |l./C..$]N8..3..||
00000120  bd 95 8c 3e 1e e8 0c bd  b9 ff 18 d3 42 73 b2 15  |...>........Bs..|
00000130  ab 92 35 d4 da ce a1 35  66 1e 0c e5 7e 12 ac 68  |..5....5f...~..h|
00000140  85 fb fa 8c ec 75 76 10  86 cb 93 4a 4d 37 e2 d0  |.....uv....JM7..|
00000150  e9 b7 96 b7 ef 64 f7 88  3b 2d f3 3b b5 e9 c1 9d  |.....d..;-.;....|
00000160  fb dd f4 77 80 5a f1 fb  ea 5e 1e 66 7a 8a 49 b0  |...w.Z...^.fz.I.|
00000170  6b b2 82 13 41 af 31 4c  ea 34 7d f3 41 20 69 76  |k...A.1L.4}.A iv|
00000180  69 fb 31 c4 e3 8b 8f fa  dc d5 b9 c3 80 b9 91 7f  |i.1.............|
00000190  02 09 c7 ca 57 32 a2 3b  c0 2c 3a fd 02 81 49 42  |....W2.;.,:...IB|
000001a0  cc bd 9c 36 67 70 50 bb  28 68 67 04 63 90 7f a7  |...6gpP.(hg.c...|
000001b0  12 b8 5a ae 20 1e 84 94  81 58 4a 5d b4 11 00 fe  |..Z. ....XJ]....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 30 d3 03 00 fe  |...........0....|
000001d0  ff ff 05 fe ff ff 02 30  d3 03 00 f0 3f 00 00 00  |.......0....?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
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

### Post by carl4926 on 2012-01-02
did you try running

```
sudo update-grub
```

make sure os-prober is installed

---

### Post by QIII on 2012-01-02
os-prober is installed by default, I believe.  I haven't installed it manually for several releases that I recall.

---

### Post by carl4926 on 2012-01-02
> **QIII said:**
> os-prober is installed by default, I believe.  I haven't installed it manually for several releases that I recall.
I know
But you never know.

---

### Post by Face-Ache on 2012-01-02
Thanks Carl & Q. Yep i did that, restarted the PC, but still no choice of what OS to boot to - this is what it said;
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-14-generic
Found initrd image: /boot/initrd.img-3.0.0-14-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda2
done

---

### Post by carl4926 on 2012-01-02
So you mean you don't see the grub menu?

---

### Post by carl4926 on 2012-01-02
If so

Just after the BIOS at boot start pressing SHIFT
The menu should appear

---

### Post by Face-Ache on 2012-01-02
Yes that's correct.

---

### Post by Face-Ache on 2012-01-02
Okay, update.

Restarted and tapped 'shift' as it re-booted. Caught sight of a DOS screen saying "GRUB loading", and then my monitor saying 'Cannot display this video mode', with Ubuntu loading moments later.

Now the  'Cannot display this video mode' error has been coming up since i installed, and also when shutting down. I assumed it was because i hadn't set up start and shutdown splash screens, but after a restart, it seems i've figured it out - for some reason, my monitor can't display the GRUB UI!

I figured it out by hitting the down arrow on the keyboard, and then 'Enter' when it was saying 'Cannot display this video mode' - hey presto, Windows is loading. First load was a CHKDSK scan telling me that "The volume is dirty", but second load it was Windows as normal.

So my issue has changed from a sort-of-serious "Heck! Where's my Windows?!?!" one to a not-so-serious "Phew, just a cosmetic issue" one!

Thanks for the advice so far guys, very much appreciated.

Now, any ideas on how to get the GRUB to display?  :)

---

### Post by Face-Ache on 2012-01-02
Another update.

Figured it out; used Grub Customizer to change the resolution, to 1024 x 768, and the GRUB UI showed during the boot, so it's all sorted!

Thanks for your help Carl  :)

---

### Post by carl4926 on 2012-01-02
> **Face-Ache said:**
> Another update.

Figured it out; used Grub Customizer to change the resolution, to 1024 x 768, and the GRUB UI showed during the boot, so it's all sorted!

Thanks for your help Carl  :)

Happy to hear you sorted it
Well done

---

