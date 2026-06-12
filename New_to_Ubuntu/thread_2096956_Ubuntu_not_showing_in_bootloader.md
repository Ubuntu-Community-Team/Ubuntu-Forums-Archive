---
title: "Ubuntu not showing in bootloader"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Asheboy on 2012-12-21
Hi,

I had installed Ubuntu usering the Windows installer. I then tried to triple boot with Windows 8 but had issues where I had nothing displaying on my bootloader list. I did managed to use the Windows tool diskpart to get Windows 7 back on the bootloader. When I download the Windows Ubuntu installer it says that I already have Ubuntu installed. I have run the bootinfoscript and here is the results:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 407551 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       1189294079 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 1435465728. But according to the info from 
                       fdisk, sda3 starts at sector 409600. According to the 
                       info in the boot sector, sda3 has 29470719 sectors, 
                       but according to the info from fdisk, it has 
                       1189294079 sectors.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd /wubildr

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 1464936448. But according to the info from 
                       fdisk, sda4 starts at sector 1189703680. According to 
                       the info in the boot sector, sda4 has 210672 sectors.. 
                       But according to the info from the partition table, it 
                       has 275443439 sectors.
    Operating System:  
    Boot files:        /wubildr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2               2,048       409,599       407,552  42 SFS
/dev/sda3    *        409,600 1,189,703,679 1,189,294,080  42 SFS
/dev/sda4       1,189,703,680 1,465,147,119   275,443,440  42 SFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        AE20CDCD20CD9D29                       ntfs       SYSTEM
/dev/sda2        AC82C79082C75D88                       ntfs       
/dev/sda3        AE448079448045D5                       ntfs       RECOVERY
/dev/sda4        1EC2-2660                              vfat       HP_TOOLS
/dev/sr0                                                iso9660    Ubuntu 12.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== sda2/Wubi/boot/grub/grub.cfg: =========================

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
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root AC82C79082C75D88
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ntfs
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root AC82C79082C75D88
  loopback loop0 /ubuntu/disks/root.disk
  set root=(loop0)
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
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
menuentry 'Ubuntu, with Linux 3.2.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root AC82C79082C75D88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=AC82C79082C75D88 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root AC82C79082C75D88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-27-generic ...'
	linux	/boot/vmlinuz-3.2.0-27-generic root=UUID=AC82C79082C75D88 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-27-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root AC82C79082C75D88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=AC82C79082C75D88 loop=/ubuntu/disks/root.disk ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root AC82C79082C75D88
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=AC82C79082C75D88 loop=/ubuntu/disks/root.disk ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
/host/ubuntu/disks/swap.disk	none	swap	sw	0	0
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic              62
               =                boot/initrd.img-3.2.0-27-generic              103
               =                boot/vmlinuz-3.2.0-23-generic                 20
               =                boot/vmlinuz-3.2.0-27-generic                 36
               =                vmlinuz                                       36
               =                vmlinuz.old                                   20

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  04 00 68 8e 00 00 00 00  10 00 00 00 60 00 00 00  |..h.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  26 1a 52 cc 8c 44 cc 01  26 1a 52 cc 8c 44 cc 01  |&.R..D..&.R..D..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  26 1a 52 cc 8c 44 cc 01  |........&.R..D..|
000000c0  26 1a 52 cc 8c 44 cc 01  26 1a 52 cc 8c 44 cc 01  |&.R..D..&.R..D..|
000000d0  26 1a 52 cc 8c 44 cc 01  00 40 00 00 00 00 00 00  |&.R..D...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 42 00 01 90 97  b0 00 00 00 50 00 00 00  |!@UB........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 42 21 01 fd fd  |........!.TB!...|
00000190  00 00 01 00 00 20 68 8e  ff ff ff ff 00 00 00 00  |..... h.........|
000001a0  00 00 04 00 00 00 00 00  21 40 55 42 00 01 90 97  |........!@UB....|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 42 21 01 fd fd  00 00 01 00 00 20 04 00  |!.TB!........ ..|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  85 82 2d 46 06 00 00 00  |FILE0.....-F....|
00000010  01 00 01 00 38 00 01 00  b0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  50 1e 34 8a 00 00 00 00  10 00 00 00 60 00 00 00  |P.4.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  13 f3 01 c6 20 f7 cb 01  13 f3 01 c6 20 f7 cb 01  |.... ....... ...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  13 f3 01 c6 20 f7 cb 01  |............ ...|
000000c0  13 f3 01 c6 20 f7 cb 01  13 f3 01 c6 20 f7 cb 01  |.... ....... ...|
000000d0  13 f3 01 c6 20 f7 cb 01  00 40 00 00 00 00 00 00  |.... ....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 58 00 00 00  01 00 40 00 00 00 01 00  |....X.....@.....|
00000110  00 00 00 00 00 00 00 00  7f 12 01 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 28 11 00 00 00 00  |@.........(.....|
00000130  00 00 28 11 00 00 00 00  00 00 28 11 00 00 00 00  |..(.......(.....|
00000140  32 40 78 00 00 0c 42 00  7b e2 b2 3e 01 42 40 1f  |2@x...B.{..>.B@.|
00000150  7e b0 1a 04 00 00 00 00  b0 00 00 00 50 00 00 00  |~...........P...|
00000160  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000170  09 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000180  00 a0 00 00 00 00 00 00  08 90 00 00 00 00 00 00  |................|
00000190  08 90 00 00 00 00 00 00  31 01 ff ff 0b 31 09 77  |........1....1.w|
000001a0  d6 0a 00 06 80 fa ff ff  ff ff ff ff 00 00 00 00  |................|
000001b0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 d0 50 1e  |1.............P.|
00000200

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
  No volume groups found

```

I have seen other threads which say to run commands similar to:

```
sudo mount /dev/sda* /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

When running the latter of the commands I receive:

```
/usr/sbin/grub-bios-setup: warning: this LDM has no Embedding Partition; embedding won't be possible.
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for RAID and LVM install.

```

Any help would be greatly appreciated.

Ash

---

### Post by sandyd on 2012-12-21
You have Ubuntu installed via Wubi. You need to remove Wubi via Windows's Add/Remove programs in the control Panel if you want to re-install.

Technically, you can use EasyBCD to add the entry back on, but I don't know how to.

---

### Post by oldfred on 2012-12-21
I really do not know wubi, but you have converted from Windows basic partitions to dynamic. Not sure if then wubi will work with dynamic partitions or not.

Windows with MBR(msdos) partitioning does not create the extended partition but converts to its own proprietary dynamic partitions.

Microsoft says conversion to dynamic is a one way process. One click to convert to dynamic and you have to totally backup, erase drive, create new partitions and restore data to convert back. But some third party tools may convert back, but backup is still required.

With wubi you use the Windows boot loader, so you never install grub to the MBR, that is only for a full partition install.
When you installed a second copy of Windows it overwrote the BCD and you would then have to manually add an entry for wubi.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)



 bcdEdit - bcbc - do not know if this works with dynamic or not
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
       
More info on dyamic:
       Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

    
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Asheboy on 2012-12-21
Thank you very much, you have been most helpful!

Ash

---

