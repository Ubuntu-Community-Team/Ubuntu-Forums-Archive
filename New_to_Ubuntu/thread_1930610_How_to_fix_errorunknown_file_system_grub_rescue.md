---
title: "How to fix: error:unknown file system grub rescue?"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by vandrf on 2012-02-24
Hi i new in this, a have install for first time lubuntu 11.04 it was OK but, in win xp i format H: disc, it was empty. Then when i turn computer on these message appears: Verifying DMI Pool Data Boot from cd: error:unknown file system grub rescue. How to fix this problem, please help???

---

### Post by SuaSwe on 2012-02-24
Hi there, 

Not totally sure what you mean - you installed 11.04, it was initially OK and allowed booting into Windows and Ubuntu, then you formatted H: and now you can't boot into either, is that right? Not knowing any other facts, I would be inclined to think that the boot loader has got messed up and that following the instructions in [this forum post]("http://ubuntuforums.org/showthread.php?t=1758396") may be a good idea - if there's anything you don't fully understand, I would suggest asking here whether to try it before doing anything. :)

---

### Post by vandrf on 2012-02-24
I reinstall grub but mesage  appears:The file /mnt/boot/grub/stage1 not read correctly. what to do next?

---

### Post by raja.genupula on 2012-02-24
* we have  a default solution that boot repair (in signature at grub recovery )
* if thats not helkp you , then please post the output of bootinfoscript (in my signature )

all the best and thank you . :)

---

### Post by vandrf on 2012-02-24
sudo                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 30764 of /dev/sdb for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    41,945,714    41,945,652   7 NTFS / exFAT / HPFS
/dev/sda2          41,945,776   320,159,384   278,213,609   5 Extended
/dev/sda5          41,945,778   181,036,484   139,090,707   7 NTFS / exFAT / HPFS
/dev/sda6         181,036,548   296,962,433   115,925,886   7 NTFS / exFAT / HPFS
/dev/sda7         296,964,096   308,461,567    11,497,472  83 Linux
/dev/sda8         308,463,616   309,202,943       739,328  82 Linux swap / Solaris
/dev/sda9         309,203,118   320,159,384    10,956,267   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5E8C7F138C7EE4C5                       ntfs       
/dev/sda5        EA08F58508F55155                       ntfs       Local Disk
/dev/sda6        10D7316E11638B79                       ntfs       
/dev/sda7        ae25c05f-b2df-44c5-a760-1b09ab8a7c8e   ext4       
/dev/sda8        fa00a1b3-f0a9-4845-aa54-658706ee2c30   swap       
/dev/sda9        2A1DD9E6758FD348                       ntfs       H:
/dev/sdb         07F6-0D65                              vfat       PENDRIVE
/dev/zram0       52b6419a-cb62-4c49-a95c-cb763fdcc7bc   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/Local Disk        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/10D7316E11638B79  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/ae25c05f-b2df-44c5-a760-1b09ab8a7c8e ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda9        /media/H:                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/stage2                               1

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=ae25c05f-b2df-44c5-a760-1b09ab8a7c8e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=ae25c05f-b2df-44c5-a760-1b09ab8a7c8e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=ae25c05f-b2df-44c5-a760-1b09ab8a7c8e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=ae25c05f-b2df-44c5-a760-1b09ab8a7c8e ro recovery nomodeset 
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
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root ae25c05f-b2df-44c5-a760-1b09ab8a7c8e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 5E8C7F138C7EE4C5
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=ae25c05f-b2df-44c5-a760-1b09ab8a7c8e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=fa00a1b3-f0a9-4845-aa54-658706ee2c30 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  2
               =                initrd.img.old                                 2
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========================== sdb/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================== sdb: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

=============== sdb: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

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
/home/ubuntu/Downloads/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by vandrf on 2012-02-24
SOLVED. reinstalling GRUB from the LiveCD as a first step in troubleshooting this:ode:


sudo mount /dev/sda4 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

Back in Ubuntu, run
Code:
sudo update-grub


#sda4 must be Linux
#must be between -install* and*--boot, two spaces.

Thanks guys....

---

