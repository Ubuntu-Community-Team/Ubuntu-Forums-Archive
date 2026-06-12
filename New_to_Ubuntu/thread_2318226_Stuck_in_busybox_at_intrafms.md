---
title: "Stuck in busybox at intrafms"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by Shehzaad_Khan on 2016-03-24
Few days before, I tried to upgrade ubunu12.04 to ubuntu 14.04. But because of low space it stopped in the middle. Then after 2 days, my speakers stopped working in ubunu12.04. So, I thought some files might have changed during upgrade and not cleared again. So, I made enough space and then upgraded ubuntu from 12.04 to 14.04. But during installation, it asked for restart after completeing all processes, but couldn't restart. Instead it put me to a busybox. And it got stuck there. The error says:

BusyBox 1.21.1 (Ubuntu 1:1.21.0 - 1ubuntu1) built in shell (ash)
Enter 'help' for a lit of built-in commands.
(initramfs)

I looked up this error on net. And I tried to apply my debugging skils, which are trust me very weird. So, after going through chain of links I came across a thread, from where I downloaded a bootinfoscript and ran it on my pc. Its output can be seen below in bold below. But before that I would like to tell that I have a windows 7 on my pc and its not working because of some hardware memory malfunctioning. I will get it repaired next month when i got enough cash. Now, the output of the script:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 2003668 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   327,682,047   327,475,200   7 NTFS / exFAT / HPFS
/dev/sda3         327,682,048   655,362,047   327,680,000   7 NTFS / exFAT / HPFS
/dev/sda4         655,362,048   976,771,071   321,409,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,633,407    15,633,345  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       e6d63b84-34cc-4377-8789-8b4cc1ae755c   ext3       
/dev/sda1        3CD8A0E3D8A09D20                       ntfs       System Reserved
/dev/sda2        EAD4914FD4911F3F                       ntfs       
/dev/sda3        BEE690ADE6906803                       ntfs       
/dev/sda4        64D49A94D49A6856                       ntfs       
/dev/sdb1        B77B-FD2E                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if loadfont unicode ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-8vBx5d0p/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-8vBx5d0p/Tmp_Log: No such file or directory
  No volume groups found


----------------------------------------------------------------------------------------------Output until here only------------------------------------------------------------------------------------------------------------------
```
Now, I don't know what to do further because I have tried other methods from threads like (the one link that  found most promising:

[http://ubuntuforums.org/showthread.php?t=1291280&page=2](http://ubuntuforums.org/showthread.php?t=1291280&page=2)

I have compared with other outputs, but comprehending it and what to do further is something that I cannot understand.

Regarding PC, I am using DELL INSPIRON N5050 series with 3GB RAM and 500 GB HDD.  (i3 processor with x86 architecture). 

Please guys help me. What should I do next now in order to boot ubuntu 14.04 successfully. I am posting this script using Live Ubuntu USB.
Thanks a lot for the help. Admirations and Graces to you for that.

---

### Post by mastablasta on 2016-03-24
you are using wubi which is no longer supported.

install 64 bit Ubuntu side by side with Windows. but remove wubi first (uninstal from Windows).

---

### Post by hakuna_matata on 2016-03-24
> **Shehzaad_Khan said:**
> I have a windows 7 on my pc and its not working because because of some hardware memory  malfunctioning.I will get it repaired next month when i got enough  cash.
RAM failures can cause data corruption on Ubuntu, too. So it is better to remove faulty RAM module(s) before you continue. Maybe, there is at least one working RAM module with enough capacity to work with Ubuntu.

It seems that data corruption already affects your virtual Wubi partition:  
> **Shehzaad_Khan said:**
> 
```
sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Are there important data on Ubuntu? Do you have a backup of file **/**[B]ubuntu/disks/root.disk ?
[/B]
If data are not important or you have a backup, try to correct the file system:
```
sudo mount /dev/sda3 /mnt
sudo e2fsck -pv /mnt/ubuntu/disks/root.disk
```
If the file system is in a good shape you can access your Ubuntu files with:
```
sudo mkdir /wubi
sudo mount -o loop /mnt/ubuntu/disks/root.disk /wubi

```
The most important data should be in [B]/wubi/home/<your Ubuntu user name>
[/B]```
cd /wubi/home/*
ls -l

```

---

