---
title: "traditional dual boot or not?"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by amitsaini on 2012-03-25
How do i know if i have traditional dual boot or not? Have not used Wubi  just want to confirm. Is there a way of getting to know through the terminal? At boot up i get an option between windows and natty.Pl help

---

### Post by Megaptera on 2012-03-25
Hi,
If you could post the output of Boot Script - as explained here: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) that'll help people here see what you set up is.

---

### Post by kdane4 on 2012-03-25
> **amitsaini said:**
> How do i know if i have traditional dual boot or not? Have not used Wubi  just want to confirm. Is there a way of getting to know through the terminal? At boot up i get an option between windows and natty.Pl help

Hi,

Another easy way to check is going to control panel in windows, in add/remove programs, if you see Ubuntu in that list, that is WUBI

---

### Post by Ryan Csh on 2012-03-25
What is *traditional* dual boot?

---

### Post by kdane4 on 2012-03-25
> **Ryan Csh said:**
> What is *traditional* dual boot?

Hello

It is installing another OS on a separate partition. Here's a good example of difference of installation between the two. 

[DUAL BOOT]("http://psychocats.net/ubuntu/installing")

[WUBI]("http://psychocats.net/ubuntu/wubi")

---

### Post by amitsaini on 2012-03-25
Here are the contents of the result file:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos9)/boot/grub on this drive.

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

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 20482938. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda7 starts at sector 81931563. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda8 starts at sector 122897313. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    20,482,874    20,482,812   7 NTFS / exFAT / HPFS
/dev/sda2          20,482,936   156,280,319   135,797,384   f W95 Extended (LBA)
/dev/sda5          20,482,938    40,965,749    20,482,812   b W95 FAT32
/dev/sda6          40,965,813    58,837,528    17,871,716   b W95 FAT32
/dev/sda7          81,931,563   122,897,249    40,965,687   b W95 FAT32
/dev/sda8         122,897,313   156,280,319    33,383,007   b W95 FAT32
/dev/sda9          58,839,040    79,331,327    20,492,288  83 Linux
/dev/sda10         79,333,376    81,930,239     2,596,864  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        F644BA5044BA137B                       ntfs       
/dev/sda10       7fedeeb8-4398-4b1b-ad28-eee381a57e01   swap       
/dev/sda5        200D-8CCC                              vfat       
/dev/sda6        A8B8-89EA                              vfat       
/dev/sda7        5860-33B6                              vfat       
/dev/sda8        80FF-2DB9                              vfat       
/dev/sda9        425291ae-e247-4610-a762-dcaf5cbd7bff   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
[spybotsd] 
timeout.old=30 
--------------------------------------------------------------------------------

=========================== sda9/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos9)'
search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=425291ae-e247-4610-a762-dcaf5cbd7bff ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=425291ae-e247-4610-a762-dcaf5cbd7bff ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=425291ae-e247-4610-a762-dcaf5cbd7bff ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=425291ae-e247-4610-a762-dcaf5cbd7bff ro single 
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
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 425291ae-e247-4610-a762-dcaf5cbd7bff
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root F644BA5044BA137B
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

=============================== sda9/etc/fstab: ================================

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
UUID=425291ae-e247-4610-a762-dcaf5cbd7bff /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=7fedeeb8-4398-4b1b-ad28-eee381a57e01 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  30.439739227 = 32.684421120   boot/grub/core.img                             1
  28.235332489 = 30.317457408   boot/grub/grub.cfg                             1
  30.876953125 = 33.153875968   boot/initrd.img-2.6.38-11-generic              2
  29.236328125 = 31.392268288   boot/initrd.img-2.6.38-8-generic               2
  29.474918365 = 31.648452608   boot/vmlinuz-2.6.38-11-generic                 2
  30.436599731 = 32.681050112   boot/vmlinuz-2.6.38-8-generic                  1
  30.876953125 = 33.153875968   initrd.img                                     2
  29.236328125 = 31.392268288   initrd.img.old                                 2
  29.474918365 = 31.648452608   vmlinuz                                        2
  30.436599731 = 32.681050112   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```






Please help.

---

### Post by oldfred on 2012-03-25
Added code tags to make boot script a bit easier to read. You highlight code or long code lists and then click on the # in the edit panel at the top of your message.

You have Windows XP in partition sda1 and Ubuntu 11.04 in partition sda9. This is a standard dual boot install.

You also have several FAT partitions, some look like they were copies from another location as the PBR - partition boot sectors have the wrong info. Partition table size and locations should match Windows PBR info. If not using partition for booting it may not create a problem.

Do you have any issues?

---

### Post by amitsaini on 2012-03-25
no so far no problems... am i required to rectify anything.

---

### Post by oldfred on 2012-03-25
No, should be fine.

I just do not recommend FAT anymore for storage. I lost data as I tried to save a file over 4GB, and it did not give any error just truncated file. FAT can only store files up to 4GB and has no journal, so repairs can take longer or be more difficult. 

NTFS is better if you want Windows compatibility. But you cannot just change formats. You have to back up all data and then restore, so next time you change partitions you may want to change but do not have to now.

---

