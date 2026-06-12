---
title: "just installed ubuntu..partition questions"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by d_stroyer on 2011-10-11
OK so i am totally new at doing this stuff..i have an acer netbook which came with winxp that i had upgraded to win7. i just installed ubuntu on it and when the screen to choose an OS comes up, it looks a bit funny so i just wanted to see what was going on..if anyone knows? i get like 10 options which are..(more or less, the screen doesnt stay up long enough to read it all)

ubuntu with linux 2.6.38-11-generic
"                                 "                    (recovery)
previous linux versions
memtest (memtest86+)
memtest  (memtest86+ with some additional stuff i couldnt catch)
win NT/XP loader (im guessing i can go ahead and delete this)
win7 loader
and then at the bottom is has 3 entries for ubuntu11.04 (when i select these a user login for cardamom pops up)

hopefully someone can give me some info. my netbook is working fine but i am sure at least the XP loader partition can be deleted. i don't have much experience with partitions.thanks!!

---

### Post by wolfen69 on 2011-10-11
Do
```
sudo update-grub
```
that should get rid of anything not needed.

---

### Post by d_stroyer on 2011-10-12
ok..i ran that command and it sad it found images but there is still 10 options when i start up to the boot screen. i no longer use winXP so i don't need that. should i go in with a partition manager program and delete that partition that way? also, the last 3 options which are all the same (ubuntu 11.04 that starts with the cardamom user log in) is followed by on/dev/sda5. what exactly does that mean? i know they are coming from the same partition, but why 3 different options to log on to it?

---

### Post by 11jmb on 2011-10-12
If you never use XP on that computer, yes. you will free up some hard drive space by giving that partition's space to your linux os

I like to boot from a gparted live disc to accomplish this

---

### Post by d_stroyer on 2011-10-12
hmm ok. i remember when i installed linux i gave it 40gb of space and i left windows with 60gb or so. so there is approx. 60 gb taken up by other things (i believe my HD is 160gb). i am new to this stuff, so i'm learning as i go. what i would like to have eventually is win7 on 1 partition, ubuntu on the other and a separate partition for progs/files.

---

### Post by blackbird34 on 2011-10-12
Thats normal, i've got the same thing. Usually there's an entry for each install of linux/windows you have, and for each install of ubuntu there's an entry fo each kernel so you can start on an older kernel or whatever and a memtest. So you should have one partition for each ubuntu (regardless how many kernels you've accumulated, i suppose) and one for each windows. If you remove xp you'll have more space of course

Edit: and you can use the freed partition for files.

---

### Post by 11jmb on 2011-10-12
please describe the "other stuff" and whether or not it is important to you. I'm guessing that there are things there like swap and boot partitions that you would like to keep

---

### Post by oldfred on 2011-10-12
The os-prober may just be finding both XP & 7 boot files in the same partition if you upgraded into the original XP partition.

Post this to see all the details:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:

---

### Post by d_stroyer on 2011-10-12
<useless info>

---

### Post by d_stroyer on 2011-10-12
.

---

### Post by d_stroyer on 2011-10-12
<not needed info>

---

### Post by d_stroyer on 2011-10-12
here u go oldfred...
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    12,273,659    12,273,597  12 Compaq diagnostics
/dev/sda2    *     12,273,660   136,451,809   124,178,150   7 NTFS / exFAT / HPFS
/dev/sda3         136,452,094   312,580,095   176,128,002   5 Extended
/dev/sda5         214,745,088   310,507,519    95,762,432  83 Linux
/dev/sda6         310,509,568   312,580,095     2,070,528  82 Linux swap / Solaris
/dev/sda7         136,452,096   212,672,511    76,220,416  83 Linux
/dev/sda8         212,674,560   214,740,991     2,066,432  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0159-6699                              vfat       PQSERVICE
/dev/sda2        A0789F9D789F7130                       ntfs       ACER
/dev/sda5        e8789582-3faa-424c-b2cf-2755d5e75e6a   ext4       
/dev/sda6        b8d085f1-41e6-461e-9e6b-466c9ae23eeb   swap       
/dev/sda7        53c720e5-2417-4504-90f5-840a33e61f4c   ext4       
/dev/sda8        b8393f27-cec6-40f7-9a59-c69547b18ff9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e8789582-3faa-424c-b2cf-2755d5e75e6a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b8d085f1-41e6-461e-9e6b-466c9ae23eeb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.530742645 = 112.239030272  boot/vmlinuz-2.6.38-8-generic                  1
 104.530742645 = 112.239030272  vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos7)'
search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=53c720e5-2417-4504-90f5-840a33e61f4c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=53c720e5-2417-4504-90f5-840a33e61f4c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=53c720e5-2417-4504-90f5-840a33e61f4c ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=53c720e5-2417-4504-90f5-840a33e61f4c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 53c720e5-2417-4504-90f5-840a33e61f4c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 0159-6699
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root A0789F9D789F7130
    chainloader +1
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e8789582-3faa-424c-b2cf-2755d5e75e6a
    linux /vmlinuz root=/dev/sda5
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e8789582-3faa-424c-b2cf-2755d5e75e6a
    linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda5
}
menuentry "Ubuntu 11.04 (11.04) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e8789582-3faa-424c-b2cf-2755d5e75e6a
    linux /vmlinuz root=/dev/sda5
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=53c720e5-2417-4504-90f5-840a33e61f4c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b8393f27-cec6-40f7-9a59-c69547b18ff9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  91.282238007 = 98.013556736   boot/grub/core.img                             1
  77.433383942 = 83.143462912   boot/grub/grub.cfg                             1
  66.733650208 = 71.654711296   boot/initrd.img-2.6.38-11-generic              1
  66.104709625 = 70.979391488   boot/initrd.img-2.6.38-8-generic               1
  66.358707428 = 71.252119552   boot/vmlinuz-2.6.38-11-generic                 1
  91.281093597 = 98.012327936   boot/vmlinuz-2.6.38-8-generic                  1
  66.733650208 = 71.654711296   initrd.img                                     1
  66.104709625 = 70.979391488   initrd.img.old                                 1
  66.358707428 = 71.252119552   vmlinuz                                        1
  91.281093597 = 98.012327936   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  c1 1a 65 4c 6b 5a d8 4c  2e 54 b9 b6 1b 72 e6 55  |..eLkZ.L.T...r.U|
00000010  a5 88 09 ed 1e d2 ac e3  1e da 2d 6b 5b 6b 69 a4  |..........-k[ki.|
00000020  6b 5b 65 35 8e b8 f9 47  89 9b 75 11 4c 62 9d 31  |k[e5...G..u.Lb.1|
00000030  13 11 68 ba a8 ef 10 f2  41 53 94 fd d3 5a d5 2e  |..h.....AS...Z..|
00000040  ce 63 e4 0d 62 9c da b5  ab 64 1a 39 76 86 69 04  |.c..b....d.9v.i.|
00000050  c0 19 35 71 67 0e 0e 47  ea 5a d6 c4 2c 73 52 39  |..5qg..G.Z..,sR9|
00000060  23 42 e6 42 10 83 9a d8  d3 bd 3b ab 2a 22 d3 b5  |#B.B......;.*"..|
00000070  2b c3 87 04 27 90 c8 35  af 82 8e f6 1a b4 aa b4  |+...'..5........|
00000080  ed 52 94 16 18 00 00 ff  fd 82 00 44 33 22 12 22  |.R.........D3"."|
00000090  22 21 11 22 11 12 24 94  49 24 90 00 00 00 00 00  |"!."..$.I$......|
000000a0  00 a6 7f a3 fa fa aa aa  ea a2 8a 30 b3 0b 3c a3  |...........0..<.|
000000b0  0e 4c d4 51 49 35 92 49  34 d6 5d 45 d6 55 85 16  |.L.QI5.I4.]E.U..|
000000c0  5d 76 59 65 96 9b 65 b6  5c 71 a6 d9 6d c5 33 88  |]vYe..e.\q..m.3.|
000000d0  84 b8 39 88 dc 6d af ad  5c 1a bd f2 19 47 ee 5a  |..9..m..\....G.Z|
000000e0  e4 67 6b 5a c4 ae 6c 18  d6 b5 75 a2 ef 4b 64 a7  |.gkZ..l...u..Kd.|
000000f0  4a 54 2d 26 9f b3 1d 0e  86 9a 0e b0 d9 36 ba 63  |JT-&.........6.c|
00000100  9c ce a7 19 5a 76 aa b2  75 64 e4 7c 24 bd 96 89  |....Zv..ud.|$...|
00000110  a9 60 21 7b 59 fc 14 d4  0f 1b 04 c3 1d 8e c6 02  |.`!{Y...........|
00000120  24 5a f0 9d f1 a3 df 58  ea 7e c8 dc 6d af a2 3f  |$Z.....X.~..m..?|
00000130  50 f5 02 4a d8 6f 9a d6  2b 82 9a ca 45 25 9a d2  |P..J.o..+...E%..|
00000140  36 4d 5c 18 a8 54 a7 64  a2 51 10 e9 56 ae f9 f3  |6M\..T.d.Q..V...|
00000150  ac 4d 70 db 66 f0 c9 08  da cf 4a af 56 b0 e7 99  |.Mp.f.....J.V...|
00000160  d3 33 48 42 76 d9 4a d7  13 07 7b 4b 5e 57 11 ae  |.3HBv.J...{K^W..|
00000170  59 38 82 62 ca c8 8a 83  5a c6 36 30 84 60 f6 64  |Y8.b....Z.60.`.d|
00000180  65 36 e4 72 10 c5 ba 20  a4 72 9d 07 1c 47 71 d8  |e6.r... .r...Gq.|
00000190  6e 5a c5 60 1b 9b 62 35  f1 84 23 15 85 47 36 aa  |nZ.`..b5..#..G6.|
000001a0  7a 99 e1 ac 38 fd eb 5d  07 e9 88 e6 d3 b2 9a b7  |z...8..]........|
000001b0  53 d6 9c 46 06 75 84 ab  18 6c 74 db 4c 6c 00 fe  |S..F.u...lt.Ll..|
000001c0  ff ff 83 fe ff ff 02 a8  aa 04 00 38 b5 05 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 e0  5f 0a 00 a0 1f 00 00 00  |........_.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by oldfred on 2011-10-12
The XP partition looks like a vendor recovery partition or vendor utilities partition? It says its Compaq Diagnostics. It has no boot.ini so it is not a full XP install. You can hide this if you want to keep it.

It looks like you installed Ubuntu twice as you have two ext4 and two swap  partitions.  Unless you want to keep it for some reason you can delete sda5 & sda6 as your install uses sda7 & swap sda8. 

You can use gparted from a liveCD to delete partitions. You could create a new /home or just a data partition. If using Windows a lot I would create a shared NTFS data partition.

You can hide things in the boot menu.

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by load12300 on 2011-10-12
The majority of online rings sell web sites are usually protected, dependable areas to order pay for top quality items. Stone, platinum, gold and/or metalic jewlery can obtainedat fantastic personal savings. Put an impression associated with [timberland outlet](http://www.timberlandsoutlets.com/) category and elegance, purchase rings auctions with confidence.
For a definitely not to get profit operation, you'll possess tons on the brain. You'll find limitless donor directories, creates, strategies to get structured and a lot do the job to get carried out. Doing this obviously requirements [timberland boots outlet](http://www.timberlandsoutlets.com/timberland-kids-boots-c-68.html) this support on the noise THE ITEM build and, in this, very good THE ITEM Help is totally crucial. The majority of little definitely not to get profit firms believe that this is one thing they might simply do the job about. Employing a in your free time THE ITEM expert, exactly who may not be [timberland boots sale](http://www.timberlandsoutlets.com/timberland-6-inch-boots-men-c-71.html)  most of which certified, is definitely just what exactly the majority of areas location tohowever, eventually, that isn't wise.
Whenever starting a definitely not to get profit operation it would be wise get started on way up powerful. By doing this you will [Michael Kors Satchel outlet ](http://www.michaelkors-online.com/michael-kors-handbags-michael-kors-satchel-c-18_20.html) not have got troubles forward motion. Rather than check out low cost sales to get equipment, meet with companies and examine if that they can present you with top quality solutions to get a very good price. By doing this you already know you have very good pc's and equipment at the start, bear in mind the sum of the fee associated with ownership [Michael kors handbags outlet](http://www.michaelkors-online.com/michael-kors-handbags-c-18.html) could be the principal thought, this expenditure around having apparatus setup for your distinct requirements is usually more important than the cost of the specific equipment – dependable equipment will be less eventually.
In relation to THE ITEM Help, [Gucci outlet online](http://www.topbagszone.com/gucci-outlet-c-36.html) it would be wise to lease an established exactly who is aware just what exactly they're performing. Don’t be fooled by way of a modern day impression, look for a [Burberry handbags outlet](hhttp://www.topbagszone.com/juicy-couture-outlet-c-43.html) person certified and with expertise employed in this definitely not to get profit field.. Have got these arrive and show off on a person's operation and suggest the easiest way associated with retaining kit.
You may furthermore contemplate selecting mastered providers or perhaps MSPs. They're laptop specialists exactly who do running [D&G Bags outlets](http://www.topbagszone.com/dg-outlet-dg-bags-c-90_91.html) a person's THE ITEM as his or her accountability. What this means is you no longer need to coach your personal team. That they are readily available, 24 / 7 as appropriate, that will resolve any kind of troubles that you could have got.
Around selecting a THE ITEM service provider you'll need a person exactly who knows what's needed on the definitely not to get profit, for instance funding, level of privacy and complying. A issuer that has a selection associated [http://www.michaelkors-online.com/](http://www.michaelkors-online.com/)with definitely not to get profit clients could have huge expertise using the related software for instance DHS methods, gift and fill increasing program, accounting method and getting at low cost chances highly relevant to a person's field. 
[michael kors outlet online](http://www.onlinemichaelkorsoutlet.com/)
[michael michael kors outlet](http://www.onlinemichaelkorsoutlet.com/)
[Michael kors outlet sale](http://www.onlinemichaelkorsoutlet.com/)
[Michael kors outlet store](http://www.onlinemichaelkorsoutlet.com/)
[Michael kors store outlet](http://www.onlinemichaelkorsoutlet.com/)
[michael michael kors handbags](http://www.onlinemichaelkorsoutlet.com/handbags-c-43.html)

---

### Post by d_stroyer on 2011-10-13
hmm..yeah the first time i tried to install it, it didnt finish and said unsuccessful. so maybe it did and just didn't work? after i restarted it just booted to win7. i used a partition program with win 7 and to me it looked like the winXP partition(/sda1) has all the driver files and whatnot for my netbook, so it might just be better to leave that alone. as far as using windows more, i am trying to get more into linux, but i would like to keep windows cause im used to it, and some things work on windows but not linux from what i know so far. thanks for the help. thanks again!!

---

### Post by oldfred on 2011-10-13
It has taken me a long time to wean myself from XP. I said I would be off it quickly 5 years ago. This year I am just about not booting XP at all. A few minor compromises as some things are better in Ubuntu, but after using a program in XP (from DOS days) I had a lot of history and familiarly with that program. The similar programs in Linux were not quite as good, but now are 'good enough'.:)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

I had learned not to use characters that Windows does not support, and normally used defaults to mount NTFS in fstab, but in another thread Morbius1 pointed out a better way than just using defaults.

- He'll get an error message if he tries to send something to the trash because trash is owned by root.
- Since this is a dual boot and the partition will also be used by Windows he'll need to take precautions against saving file names with characters that Windows cannot interpret.The following would eliminate both problems:
UUID=734240563B00719 /media/DOC ntfs defaults,uid=1000,nls=utf8,windows_names 0 0

---

### Post by d_stroyer on 2011-10-13
ok so..i went in with gparted and deleted sda5 & sda6..BUT when i rebooted the system it gives me a black screen that says:
error: no such partition
grub rescue>

help?! thanks.

---

### Post by oldfred on 2011-10-13
Are you sure you deleted the partitions you were not using? Partitions nor UUIDs should not have changed.

Repost boot info script.

Or download and run either of these:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

### Post by d_stroyer on 2011-10-13
yeah i'm pretty sure i did. i was just following what you were saying in the earlier post (#13 of this thread) and you said i didnt need sda5 or 6. i'm learning as i go ha. i went to the supergrub.org site. should i use the rescatux app or the supergrub2 disk? or no difference?

---

### Post by oldfred on 2011-10-13
I have not used supergrub for a while. It looks like Supergrub tries to boot anything and rescatux tries to do repairs.

---

### Post by d_stroyer on 2011-10-13
i ran the boot repair disk from a live usb and it seems to have gotten everything working again. the partitions i deleted were the unused ones. it got rid of those 3 ubuntu options that had a cardamom log in that i was talking about in the first post of this thread and looks like it freed up 40+gb on my hard drive. the win xp option still shows up but i will probably look at the post you put up about hiding options on the grub screen since i don't ever use it. thanks again for the help!! 
p.s. i added u as a contact/friend if that's ok. i promise not to bother you anymore than i need to!! haha

---

### Post by oldfred on 2011-10-13
Glad you got it working.

Post solved, so others may find thread and know something worked.

---

