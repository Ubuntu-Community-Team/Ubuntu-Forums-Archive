---
title: "Boot problem after deleting last 2 sdbs"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by usorted on 2011-11-06
I used gparted from usb stick to delete sdb7 (and the switch partition after it) and now the machine will not boot.

This is the partition table now. (if thats what it's called)

 ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a92f804

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    20980889    10490413+  12  Compaq diagnostics
/dev/sdb2   *    20981760   108451838    43735039+   7  HPFS/NTFS/exFAT
/dev/sdb3       166397950   312580095    73091073    5  Extended
/dev/sdb5       166397952   211566591    22584320   83  Linux
/dev/sdb6       211568640   213616639     1024000   82  Linux swap / Solaris

Disk /dev/sda: 7948 MB, 7948206080 bytes
245 heads, 62 sectors/track, 1021 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d9e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62    15508989     7754464    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 


is it possible to repair?

---

### Post by Elfy on 2011-11-06
Assuming that you got that information from the livecd - please go here and follow the instructions.

Post the resulting information here please.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It will give us a lot more information.

It would also help to know what messages you get when the boot fails.

---

### Post by usorted on 2011-11-06
Thanks, at first few tries screen said something like - no such partition
and Grub Rescue _

then next few tries (this morning) it wouldn't even boot from the usb it was just one line of text with someones name and then I went into the bios and put usb hard drive generic at the top and it booted but i don't know if that change was relevant as it booted from the USB last night - result is that now I'm in on the USB I'm reluctant to closed down in case I can't get it running again!   

Results of the test you directed me to are pasted below , thanks.
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>.......hT.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1453096 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sda1 starts at sector 
                       0. But according to the info from fdisk, sda1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /BOOTMGR /BOOT/BCD

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 7948 MB, 7948206080 bytes
245 heads, 62 sectors/track, 1021 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             62    15,508,989    15,508,928   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63    20,980,889    20,980,827  12 Compaq diagnostics
/dev/sdb2    *     20,981,760   108,451,838    87,470,079   7 NTFS / exFAT / HPFS
/dev/sdb3         166,397,950   312,580,095   146,182,146   5 Extended
/dev/sdb5         166,397,952   211,566,591    45,168,640  83 Linux
/dev/sdb6         211,568,640   213,616,639     2,048,000  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       e339e756-037e-413b-8145-2345ce6e9a8a   ext3       
/dev/sda1        20B4-9801                              vfat       
/dev/sdb1        E8E4440EE443DD86                       ntfs       PQSERVICE
/dev/sdb2        1AFA6167FA613FDD                       ntfs       ACER
/dev/sdb5        b910efbe-2437-4f53-8b25-8c2aee6e18e0   ext4       
/dev/sdb6        ce1f4a29-eec9-40b6-be16-69bf6bf447a7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

================================ sdb2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root b910efbe-2437-4f53-8b25-8c2aee6e18e0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root E8E4440EE443DD86
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1AFA6167FA613FDD
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 111ef9ca-c0de-4044-ab48-63c99372b080
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=111ef9ca-c0de-4044-ab48-63c99372b080 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos7)'
    search --no-floppy --fs-uuid --set=root 111ef9ca-c0de-4044-ab48-63c99372b080
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=111ef9ca-c0de-4044-ab48-63c99372b080 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=b910efbe-2437-4f53-8b25-8c2aee6e18e0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=ce1f4a29-eec9-40b6-be16-69bf6bf447a7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.35-28-generic              1
               =                boot/initrd.img-2.6.38-10-generic              3
               =                boot/initrd.img-2.6.38-11-generic              3
               =                boot/initrd.img-2.6.38-12-generic              2
               =                boot/initrd.img-2.6.38-8-generic               3
               =                boot/vmlinuz-2.6.35-28-generic                 1
               =                boot/vmlinuz-2.6.38-10-generic                 2
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-2.6.38-12-generic                 1
               =                boot/vmlinuz-2.6.38-8-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        1
               =                vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 38 b1 02 00 fe  |...........8....|
000001d0  ff ff 05 fe ff ff 02 38  b1 02 00 48 1f 00 00 00  |.......8...H....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

Downloads/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by Elfy on 2011-11-06
Can't see anything odd - but I'm not seeing too well today ...

Try reinstalling grub - [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by drs305 on 2011-11-06
It appears your Ubuntu installation is now on sdb5 while the sdb MBR is looking at sdb5. 

If you are currently on a LiveCD/USB, you should be able to run the following commands to change the sdb MBR to point to your sdb5 files:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
sudo umount /dev/sdb5
```
Do not include the partition number in the second command.

When you reboot, make sure the BIOS is set to boot from the 160GB drive first (or remove the other drive).

There is a slight possibility it won't boot because of the location of the boot files on the drive. If it fails to boot, at the grub prompt, run the following commands. The commands will indicate whether the BIOS/Grub can 'see' the boot files. If it finds nothing, try using hd0 in the commands  instead of hd1:

```
ls (hd1,**5**)/  # Does it find 'vmlinuz' and 'initrd.img'
ls (hd1,**5**)/boot # Does it find the kernel and initrd images
ls (hd1,**5**)/boot/grub # Are there lots of *.mod files
```

---

### Post by usorted on 2011-11-06
Many thanks to you both for helping me. IT WORKS !!!

That's the netbook sorted. just the desktop problem of not responding to the keyboard after installing 11.10 to sort out now. I think that may be more tricky due to not being able to type anything into the terminal!

---

### Post by drs305 on 2011-11-06
:-)

Glad it's working. If the issues in this thread are solved please mark it SOLVED via the thread tools link near the top right of the first post. 

It allows helpers to concentrate on unresolved problems.

As for your other issue, I've taken a look at the thread. Does the keyboard work at the Grub menu - can you press 'e' or 'c' and then type characters? If not, you may need to add the modules for an 'at' or 'usb' keyboard to the grub configuration file entries.

Please reply in your thread rather than here - whether the keyboard works in Grub but not once booted, or if it doesn't work anywhere. Also, does the keyboard still work if you are using a LiveCD?

---

