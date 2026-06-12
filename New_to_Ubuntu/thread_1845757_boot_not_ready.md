---
title: "/boot not ready"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by spillage2 on 2011-09-17
Hi all.

Have recently installed a fresh copy of 10.04 but have since moved my drive around. 

Now i have to press S to skip on boot.

This is my fstab

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 /               ext4    errors=remount-ro 0       1
/dev/sda5       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=38b44f80-d7e8-4c12-ba7e-e9d551f09819 /home           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0

```and this is my uuid

```

total 0
lrwxrwxrwx 1 root root 10 Sep 17 22:04 050dd4f5-bb68-4528-8358-b7872bd0deb3 -> ../../sda1
lrwxrwxrwx 1 root root 10 Sep 17 22:04 1CEF-9A66 -> ../../sdi1
lrwxrwxrwx 1 root root 10 Sep 17 22:04 38b44f80-d7e8-4c12-ba7e-e9d551f09819 -> ../../sdc7
lrwxrwxrwx 1 root root 10 Sep 17 22:04 4f2b4525-ab70-4688-91a5-7f8e359db849 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Sep 17 22:04 53B8-C29A -> ../../sdj1
lrwxrwxrwx 1 root root 10 Sep 17 22:04 6aaa4b56-0a92-48f7-9c7f-f2351e0a97af -> ../../sdc6
lrwxrwxrwx 1 root root 10 Sep 17 22:04 c13c665a-f042-4371-8432-d9415c691a53 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Sep 17 22:04 c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07 -> ../../sdc5


```Really lost in how to resolve this.

both boot and home need to be skipped as showing as not ready.

any help would be appreciated

Thanks Spill.

---

### Post by drs305 on 2011-09-17
> **[COLOR="Red"]#[/COLOR]**UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 /               ext4    errors=remount-ro 0    

It looks like you don't have / designated. It's commented. I've never seen an fstab like that. Remove the comment, save the file, and then see what happens.

---

### Post by Bodsda on 2011-09-17
> **drs305 said:**
> It looks like you don't have / designated. It's commented. Remove the comment, save the file, and then see what happens.

Should the system even be able to boot without that entry?

Bodsda

---

### Post by drs305 on 2011-09-17
> **Bodsda said:**
> Should the system even be able to boot without that entry?

Bodsda

I was thinking not, but I don't know if there is a way for /boot to pass something on or not. I edited by post a minute or two ago to reflect I've not seen it like that in fstab.

---

### Post by spillage2 on 2011-09-17
all i have to do is press 's' and it boots fine. I will try and remove the comment tomorrow and see what happens.

if all else fails i will have to reinstall the o/s.

or maybe work out where how the drives where plugged in before and see if that cures it?

---

### Post by drs305 on 2011-09-17
Before you change the fstab, take a look at the results of the "mount" command. See if it reports / on sdc1. It's possible your real fstab is not the one you posted

It might be helpful for you to run the boot info script. It will show us the location and designation of all your boot files in a file called RESULTS.txt

If you run the script and post the contents of RESULTS.txt we might be able to see what's going on. Click the "BIS" link in my signature line to go to the download site.

---

### Post by spillage2 on 2011-09-21
Here are the result from RESULT.txt.

I am also sure that the posted fstab is the correct one.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /grub.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   410,542,079   410,540,032  83 Linux
/dev/sda3         410,544,126 1,250,263,039   839,718,914   5 Extended
/dev/sda5         410,544,128   428,122,111    17,577,984  83 Linux
/dev/sda6         428,124,160   430,075,903     1,951,744  82 Linux swap / Solaris
/dev/sda7         430,077,952 1,250,263,039   820,185,088  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    78,156,224    78,156,162  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63 1,250,258,624 1,250,258,562  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4f2b4525-ab70-4688-91a5-7f8e359db849   ext4       
/dev/sda5        c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07   ext4       
/dev/sda6        6aaa4b56-0a92-48f7-9c7f-f2351e0a97af   swap       
/dev/sda7        38b44f80-d7e8-4c12-ba7e-e9d551f09819   ext4       
/dev/sdb1        050dd4f5-bb68-4528-8358-b7872bd0deb3   ext4       hd3
/dev/sdc1        c13c665a-f042-4371-8432-d9415c691a53   ext4       hd2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw)
/dev/sda5        /boot                    ext4       (rw)
/dev/sda7        /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4f2b4525-ab70-4688-91a5-7f8e359db849
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux    /vmlinuz-2.6.32-33-generic-pae root=UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    echo    'Loading Linux 2.6.32-33-generic-pae ...'
    linux    /vmlinuz-2.6.32-33-generic-pae root=UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
#UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 /               ext4    errors=remount-ro 0       1
/dev/sda5       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=38b44f80-d7e8-4c12-ba7e-e9d551f09819 /home           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.130714417 = 2.287837184    boot/grub/core.img                             1
   2.139656067 = 2.297438208    boot/grub/grub.cfg                             1
   0.137874603 = 0.148041728    boot/initrd.img-2.6.32-33-generic-pae          1
   0.144363403 = 0.155009024    boot/vmlinuz-2.6.32-33-generic-pae             1
   0.137874603 = 0.148041728    initrd.img                                     1
   0.144363403 = 0.155009024    vmlinuz                                        1

============================= sda5/grub/grub.cfg: ==============================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4f2b4525-ab70-4688-91a5-7f8e359db849
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux    /vmlinuz-2.6.32-33-generic-pae root=UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 ro   quiet splash
    initrd    /initrd.img-2.6.32-33-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    echo    'Loading Linux 2.6.32-33-generic-pae ...'
    linux    /vmlinuz-2.6.32-33-generic-pae root=UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set c84b2eb9-abd6-4d2f-b4e8-a41fafc4bb07
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 197.892433167 = 212.485382144  grub/core.img                                  1
 197.901374817 = 212.494983168  grub/grub.cfg                                  1
 195.899593353 = 210.345586688  initrd.img-2.6.32-33-generic-pae               1
 195.906082153 = 210.352553984  vmlinuz-2.6.32-33-generic-pae                  1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  fb 5c e3 ee 7d fe 27 a1  fe 51 2c 36 79 f4 ef 9c  |.\..}.'..Q,6y...|
00000010  bd 66 a2 af 8f 5a 4f 5b  54 ec 63 fb ca b6 83 f6  |.f...ZO[T.c.....|
00000020  7b a5 94 e5 2e ab f9 34  b8 bb dc ae fe 3b b1 e8  |{......4.....;..|
00000030  60 01 18 a1 10 01 92 20  24 02 29 54 b6 5e af 65  |`...... $.)T.^.e|
00000040  f2 6c 6b c4 82 d4 0f 35  76 a8 ce ae 41 c2 4a 08  |.lk....5v...A.J.|
00000050  87 58 7d 5e 90 88 82 11  e2 72 96 ca 0c 49 f4 f7  |.X}^.....r...I..|
00000060  7f ff f7 7f ff ff fd 06  85 f6 d7 00 00 02 9d 8d  |................|
00000070  a9 43 e8 d3 15 b9 2f 96  e2 f7 6b e1 56 b3 f8 bb  |.C..../...k.V...|
00000080  d1 24 11 d1 28 68 2b 85  0c 19 12 10 1b 07 c4 02  |.$..(h+.........|
00000090  51 64 50 54 39 27 14 96  8f ea 9c a4 44 3b b9 a9  |QdPT9'......D;..|
000000a0  c7 83 d5 47 6c 10 8e 88  e6 81 20 f4 79 0a b3 38  |...Gl..... .y..8|
000000b0  cc 14 1c a3 15 cd 24 c4  4c 20 0c 4c 49 d8 41 3c  |......$.L .LI.A<|
000000c0  3e ea 77 65 73 3d 79 8f  9f eb 30 30 64 63 f6 0b  |>.wes=y...00dc..|
000000d0  00 00 46 b2 ee 83 c9 d8  bb 16 c3 ad 85 99 ce c2  |..F.............|
000000e0  50 5a 1b 4f c9 c9 e9 41  f2 52 0f 05 26 b4 ee 0c  |PZ.O...A.R..&...|
000000f0  62 d8 81 59 55 09 3f 95  8f 11 d5 23 01 31 58 eb  |b..YU.?....#.1X.|
00000100  ab 9a 16 fa 95 0b 09 49  13 7d fc 2b 73 ff 5c 8c  |.......I.}.+s.\.|
00000110  de 00 20 ac 6b 81 cd a2  94 26 99 07 f0 1c 90 9a  |.. .k....&......|
00000120  83 37 60 2e d9 2d d6 74  d4 31 ca 69 41 4b 1b 52  |.7`..-.t.1.iAK.R|
00000130  6f 82 90 69 4c 14 00 ed  dc e9 e2 cf 30 cd d0 34  |o..iL.......0..4|
00000140  18 6a 8a 6e cb 2c 98 99  31 06 e7 ce a3 3f 63 bd  |.j.n.,..1....?c.|
00000150  29 29 df cb e1 e7 b2 a3  3b ab f6 62 56 0f 32 93  |))......;..bV.2.|
00000160  7b 51 e5 b0 3c d2 e8 8a  58 24 fd b1 0c 99 14 b4  |{Q..<...X$......|
00000170  13 04 55 3f 40 0e b0 ba  59 75 20 61 b0 74 67 69  |..U?@...Yu a.tgi|
00000180  00 18 73 e1 82 eb e5 4b  99 60 12 d7 3c a8 97 10  |..s....K.`..<...|
00000190  f0 b7 4b 1f 8d 41 df 6d  66 9a 26 c3 76 29 30 ce  |..K..A.mf.&.v)0.|
000001a0  6b 2b 47 f6 d9 af 0d a8  63 ed 86 82 ef 07 d1 b7  |k+G.....c.......|
000001b0  27 0a e3 b8 2f 1c 9c db  27 a6 42 09 02 44 00 fe  |'.../...'.B..D..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 0c 01 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 38  0c 01 00 d0 1d 00 00 00  |.......8........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 



```

---

### Post by drs305 on 2011-09-21
When your boot stops and you get the S option, there should be a message telling you why it stopped. If there is and you can provide it, it would be easy for us to help fixing it.

Next, your fstab doesn't specify / anywhere. It got commented out at some point. I didn't even know Ubuntu would boot like that, but I've recently seen it in another case.

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
**[COLOR="Red"]#[/COLOR]**UUID=4f2b4525-ab70-4688-91a5-7f8e359db849 /               ext4    errors=remount-ro 0       1
/dev/sda5       /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=38b44f80-d7e8-4c12-ba7e-e9d551f09819 /home           ext4    defaults        0       2
/dev/sda6       none            swap    sw              0       0
Remove the **[COLOR="Red"]#[/COLOR]**, save the file, reboot and see if it boots without pausing.

I'd recommend using UUIDs for all the entries but we can discuss that after we solve this problem.

---

### Post by spillage2 on 2011-09-21
HI drs305,

Thanks for all your help so far.

I have removed the # from fstab.

first of all it came up with "the disc drive for /boot is not ready yet or not present" I pressed "s" as usual and very quickly another line came up I think about sda6 not ready then booted (be it very slow)

I booted a couple more times and it went straight through without prompting me to press "s" but is really hanging.

takes an age to boot.

Of course I could just reinstall the os but kinda of like to know whats going on and try and sort out the problem rather than throwing in the towel and taking the easy option.

---

### Post by drs305 on 2011-09-21
I'm going to review your RESULTS.txt again, but I do have another question. You have a separate /boot on sda5, but it also looks like you have all the boot files in sda1 as well. Did you have a specific reason for creating the separate /boot file?

One reason I ask is that the / boot files are early in the disk, the sda5 are far out on the disk (which sometimes causes problems). Often a user creates a separate /boot file if the BIOS can only see the first 137Gb of the disk, but your's is outside that part of the drive. [COLOR="DarkRed"]I'm tempted to say that the delay *is* because the BIOS isn't seeing the /boot directory and that is why you get the delay and it is using the info in your / folder's boot folder, but I don't know if that is possible.
[/COLOR]
I've created a separate /boot partition for testing and left the boot files intact in / as well and didn't have any issues; the /boot should be mounted over the boot files in / as far as I know, thus hiding them.

I haven't thought through the potential conflicts, if any, but it's something I'll consider.

**Added: **

You appear to be offline, so I'll add a couple of requests. In preparation of perhaps trying to boot from the sda1 boot files we need to confirm they are there.
In / are there: vmlinuz and initrd.img files.
Unmount /boot (sudo umount /boot). This will expose the boot files on sda1.
In /boot are there vmlinuz-2-6..... kernel and initrd.img-2.6... files and a grub folder?
In /boot/grub are there a lot of *.mod files and grub.cfg?
Remount /boot with (sudo mount /dev/sda5).

---

### Post by spillage2 on 2011-09-23
Ok when I umount /boot all I can see is a grub file with just ############### in it.

If I try sudo mount /dev/sda5 i get mount: special device /dev/sda5 does not exist.

I have looked at the hd and can see that sdc5 has the files grub and initrdimg 2.06.32.33 and vmlnuz 2.6.32.33.

really not sure if this helps.

I seems the my third hd is plugged into the sata slot that the system is looking for the /boot file.

Not sure if its worth switching the sata plugs around.

---

### Post by drs305 on 2011-09-24
Take a look at your BIOS settings to see which drive is booting first. Look carefully since both your sda and sdc drives are the same size. If you don't know how to enter the BIOS setup - the key to press during the early part of boot may be displayed on the screen. It's often the DEL key, or one of the F* keys).

Try setting it to what in RESULTS txt is your sda drive.

Also during the initial boot, at the grub menu (if you don't see the menu, hold down the SHIFT key), press c to get to the Grub prompt.

Type the following and see if you see the boot files. The first looks for /boot/grub on sda1. The second /grub on sda5.
```
ls (hd0,1)/boot/grub
ls (hd0,5)/grub
```

Added:
I'm a bit puzzled by your 'sdc5' comment in the previous post. RESULTS.txt doesn't show a sdc5, so it's possible that sda has been redesignated as sdc. In that case, the above commands need to be changed to (hd2,...).

With the "ls" check at the grub prompt, I'm trying to find out if GRUB is finding the necessary boot files on sda1 (or maybe sdc1 if renamed). If it can, what I'd propose is to comment out the /boot entry in fstab, update-grub and let the system try to boot sda1 without a separate /boot partition. If the files are on sda1, it should do so. I wouldn't attempt it unless you have a bootable LiveCD so you can reverse the change if it doesn't boot.

Another question: You've stated you don't have to press 'S' any longer but it takes a long time to boot. Does the menu take a long time to display or is it later. What's the last thing you see before the delay?

---

### Post by spillage2 on 2011-09-25
Ok

Changed the bios and it will only boot from the one drive.

When I went into grub I got:

ext2 uuid 4f264525-ab70-4688-91a5-7f8e359db849

and 

ext2 uuid c84b2eb9-abd6-4d2f-b4e8-941fafc4bb07

Hope this helps..

---

