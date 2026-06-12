---
title: "External drive does not boot - grub issue"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by rajagottipati on 2011-11-09
hi all, i am having issue with booting from external usb hard drive with 11.02 installation in it, placed boot script output as follows , i am getting blinking cursor.

```
     
             Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb5 
                       and looks at sector 492637896 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   259,971,119   229,044,272   7 NTFS / exFAT / HPFS
/dev/sda4         259,973,120   976,771,071   716,797,952   f W95 Extended (LBA)
/dev/sda5         259,975,168   771,971,071   511,995,904   7 NTFS / exFAT / HPFS
/dev/sda6         771,973,120   976,771,071   204,797,952   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   215,527,423   215,525,376   7 NTFS / exFAT / HPFS
/dev/sdb2         215,529,470   625,141,759   409,612,290   5 Extended
/dev/sdb5         215,529,472   608,448,511   392,919,040  83 Linux
/dev/sdb6         608,450,560   625,141,759    16,691,200  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        AC7C4EC27C4E86D4                       ntfs       OS
/dev/sda5        B8E485C5E48585FA                       ntfs       Raja
/dev/sda6        56021F75021F58F7                       ntfs       Misc
/dev/sdb1        F4567DBF567D8362                       ntfs       NTFS_PART
/dev/sdb5        f86134f8-1dc5-463c-9229-096e65f53f2f   ext4       
/dev/sdb6        c41b6f3f-871e-47b0-8a31-1d198ec49f29   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/NTFS_PART         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb5        /media/f86134f8-1dc5-463c-9229-096e65f53f2f ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=f86134f8-1dc5-463c-9229-096e65f53f2f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	echo	'Loading Linux 3.0.0-12-generic-pae ...'
	linux	/boot/vmlinuz-3.0.0-12-generic-pae root=UUID=f86134f8-1dc5-463c-9229-096e65f53f2f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=f86134f8-1dc5-463c-9229-096e65f53f2f ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=f86134f8-1dc5-463c-9229-096e65f53f2f ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
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
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos5)'
	search --no-floppy --fs-uuid --set=root f86134f8-1dc5-463c-9229-096e65f53f2f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root CC70378A703779F2
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root AC7C4EC27C4E86D4
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
UUID=f86134f8-1dc5-463c-9229-096e65f53f2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c41b6f3f-871e-47b0-8a31-1d198ec49f29 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-12-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              2
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  c1 f3 60 09 09 28 f2 56  4b 95 b2 a2 4e d4 dd c3  |..`..(.VK...N...|
00000010  e8 9c 84 f0 53 f6 17 83  c3 40 1f 41 e2 3f f5 56  |....S....@.A.?.V|
00000020  0f 9b 00 6d 1e 0f c0 c8  42 9f 5c 1b 69 48 94 16  |...m....B.\.iH..|
00000030  8e 93 28 59 af 14 9e aa  33 82 5c 49 62 8f cb 2b  |..(Y....3.\Ib..+|
00000040  1b 78 b3 47 e0 4c 04 4a  4a 86 21 4f 53 47 fb 74  |.x.G.L.JJ.!OSG.t|
00000050  21 09 20 c8 55 16 93 7a  d8 0c 0a 60 83 2c bd 90  |!. .U..z...`.,..|
00000060  10 80 79 76 09 6c 84 34  73 cb 03 23 b1 ea ba 0c  |..yv.l.4s..#....|
00000070  06 75 14 bb 5a d5 1e ea  46 09 1b 26 a8 f9 09 08  |.u..Z...F..&....|
00000080  ef ba 07 0c e5 b8 c7 f2  73 ea 32 ea 15 9b a4 8d  |........s.2.....|
00000090  31 54 d8 be aa ca 05 1b  fa 18 eb c0 31 d5 e5 2a  |1T..........1..*|
000000a0  86 00 a7 77 d0 1c 2f 07  85 80 3d 1d 08 61 09 2a  |...w../...=..a.*|
000000b0  e6 40 e2 bf 08 f0 7d 04  45 1f 06 a0 d3 66 83 c4  |.@....}.E....f..|
000000c0  7f ea 34 03 83 e8 3b 2e  12 21 76 d6 d5 17 ff fd  |..4...;..!v.....|
000000d0  67 55 6d 51 bb 4e 35 ce  43 45 a8 99 42 7f b8 b0  |gUmQ.N5.CE..B...|
000000e0  e1 01 90 29 f7 dd 1e 0f  d5 b6 10 82 0c 4b 02 14  |...).........K..|
000000f0  fa 4e 80 7c 19 37 44 62  e5 55 ae 2a 12 c2 07 d2  |.N.|.7Db.U.*....|
00000100  de 03 06 6d 09 bd 89 31  06 44 b0 ea 1a 85 31 33  |...m...1.D....13|
00000110  7a d0 62 33 bf ff df 6c  10 ac 4e a4 ba 95 2b b5  |z.b3...l..N...+.|
00000120  19 ef a8 aa 14 82 17 ec  66 a9 55 85 aa d9 e1 89  |........f.U.....|
00000130  14 08 8d a6 57 fa 9f 2c  ce f1 a6 49 fd 47 82 3b  |....W..,...I.G.;|
00000140  31 3d 5d 65 f5 a5 9e 14  02 9f 5d 73 f5 a1 f1 7a  |1=]e......]s...z|
00000150  2c 06 1c b7 ad 8b 72 ae  07 e2 d1 5a ab ea 39 1a  |,.....r....Z..9.|
00000160  c1 1d 9e 08 d8 a6 f0 6c  39 27 ee 86 ac d0 c0 13  |.......l9'......|
00000170  00 a7 61 f4 16 6b c0 38  ae eb 4a 22 2c ed 18 51  |..a..k.8..J",..Q|
00000180  ed 1f 7c 1e 0b fe 90 84  5f e1 2b 62 9b 7d 47 c2  |..|....._.+b.}G.|
00000190  3a db 40 e2 b4 d7 55 27  f3 fa d4 4f 75 ae 23 30  |:.@...U'...Ou.#0|
000001a0  3f 12 81 40 3f 08 00 1a  0d a0 1e 3f 2f 54 0a 0f  |?..@?......?/T..|
000001b0  aa 12 b0 20 e7 8b af 87  df fd 1e b6 a5 4e 00 fe  |... .........N..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 78 6b 17 00 fe  |...........xk...|
000001d0  ff ff 05 fe ff ff 02 78  6b 17 00 b8 fe 00 00 00  |.......xk.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
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

### Post by rajagottipati on 2011-11-10
am i posting in right thread for above problem, i am bit new to forums.

---

### Post by oldfred on 2011-11-11
@rajagottipati
I do not go back and look at old threads. It would be better to have just started a new thread. As a solved thread few others will look at it also. Moved to your own thread.

> => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    [COLOR=Red]for  on[/COLOR] this drive.
You have something missing as it should show the partition after the for.
I would just try reinstalling grub to sdb.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by rajagottipati on 2011-11-13
Hi Fred,
 
Thank you for your reply.
 
I tried installing 10.02 and now i am getting proper grub info but still not able to boot, it seems  its not going till grub loading, i am getting blank screen with cursor, please find boot script output as follows...
```
                  Boot Info Script 0.60    from 17 May 2011

============================= Boot Info Summary: ===============================
 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
sda1: __________________________________________________________________________
    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM
sda2: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
sda3: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD
sda4: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        
sda6: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        
sdc1: __________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
sdc2: __________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdc5: __________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sdc6: __________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2    *        206,848    30,926,847    30,720,000   7 NTFS / exFAT / HPFS
/dev/sda3          30,926,848   259,971,119   229,044,272   7 NTFS / exFAT / HPFS
/dev/sda4         259,973,120   976,771,071   716,797,952   f W95 Extended (LBA)
/dev/sda5         259,975,168   771,971,071   511,995,904   7 NTFS / exFAT / HPFS
/dev/sda6         771,973,120   976,771,071   204,797,952   7 NTFS / exFAT / HPFS

Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdc1    *          2,048   409,602,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sdc2         409,604,094   625,141,759   215,537,666   5 Extended
/dev/sdc5         409,604,096   604,913,663   195,309,568  83 Linux
/dev/sdc6         604,915,712   625,141,759    20,226,048  82 Linux swap / Solaris

"blkid" output: ________________________________________________________________
Device           UUID                                   TYPE       LABEL
/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DELLUTILITY
/dev/sda2        CC70378A703779F2                       ntfs       Recovery
/dev/sda3        6E28737328733963                       ntfs       OS
/dev/sda5        B8E485C5E48585FA                       ntfs       Raja
/dev/sda6        56021F75021F58F7                       ntfs       Misc
/dev/sdc1        807A01677A015B74                       ntfs       NTFS_PART
/dev/sdc5        9f135f1e-6ba7-406e-8df5-5aba5564173e   ext4       
/dev/sdc6        a75ab2a9-0642-4dc5-92da-4edeadb8580a   swap       
================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/NTFS_PART         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc5        /media/9f135f1e-6ba7-406e-8df5-5aba5564173e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

=========================== sdc5/boot/grub/grub.cfg: ===========================
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=9f135f1e-6ba7-406e-8df5-5aba5564173e ro   quiet splash
 initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
 echo 'Loading Linux 2.6.32-28-generic ...'
 linux /boot/vmlinuz-2.6.32-28-generic root=UUID=9f135f1e-6ba7-406e-8df5-5aba5564173e ro single 
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod ext2
 set root='(hd1,5)'
 search --no-floppy --fs-uuid --set 9f135f1e-6ba7-406e-8df5-5aba5564173e
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
 insmod ntfs
 set root='(hd0,2)'
 search --no-floppy --fs-uuid --set cc70378a703779f2
 chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
 insmod ntfs
 set root='(hd0,3)'
 search --no-floppy --fs-uuid --set 6e28737328733963
 chainloader +1
}
### END /etc/grub.d/30_os-prober ###
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------
=============================== sdc5/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb5       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=a75ab2a9-0642-4dc5-92da-4edeadb8580a none            swap    sw              0       0
--------------------------------------------------------------------------------
=================== sdc5: Location of files loaded by Grub: ====================
           GiB - GB             File                                 Fragment(s)
 269.447502136 = 289.317052416  boot/grub/core.img                             1
 201.466091156 = 216.322568192  boot/grub/grub.cfg                             1
 269.455272675 = 289.325395968  boot/initrd.img-2.6.32-28-generic              1
 269.446102142 = 289.315549184  boot/vmlinuz-2.6.32-28-generic                 1
 269.455272675 = 289.325395968  initrd.img                                     1
 269.446102142 = 289.315549184  vmlinuz                                        1


```

---

### Post by oldfred on 2011-11-13
Do you get a grub menu?

Sometimes you have booted with grub, but then Ubuntu has video issues or other parameters to adjust for your specific system are needed.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rajagottipati on 2011-11-17
Fred,
 
I tried all the combinations mentioned in thread and i am still getting blank screen with blinking cursor,by pressing shift key continously during boot i am seeing Grub loading and blinking cursor after that.
 
Grub Loading.
-

---

### Post by rajagottipati on 2011-11-17
Hi Fred,
 
I checked with Dell support , they told that dell laptops wont support external usb hard drive booting (my model is Inspiron N5010) is that true?

---

### Post by oldfred on 2011-11-17
Most newer systems do, as you used to have to boot a DOS disk to update BIOS. Very old systems (over 5 or 6 years) did not, and maybe some very new UEFI have started the lockdown that Microsoft wants to prevent users from booting anything else.

---

