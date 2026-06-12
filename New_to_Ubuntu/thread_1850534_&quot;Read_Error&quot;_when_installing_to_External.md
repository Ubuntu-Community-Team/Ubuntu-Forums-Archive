---
title: "&quot;Read Error&quot; when installing to External Hard Drive..."
date: 2011-09-26
forum: New to Ubuntu
---

### Post by JoshSTJ on 2011-09-26
Hey guys,

Today I bought a Toshiba 500 gig external hard drive because the hdd in my laptop died.  I was previously running the live version of Ubuntu from a 2 gig flash drive, and was finally able to get an external hard drive to install it permanently on.

I followed online instructions to install Ubuntu to an external hard drive, it goes through the entire process, and tells me to restart.  After restarting and setting the bios to load from the external hard drive, I get "READ ERROR" and it goes no further.

I'm completely at a loss of what to do from here.  I've ran the Boot Info script and the contents of that can be found below.  Any help will be greatly appreciated...

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 680213 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2089 MB, 2089324032 bytes
255 heads, 63 sectors/track, 254 cylinders, total 4080711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *            104     4,080,710     4,080,607   6 FAT16


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sdc2          39,065,598   976,771,071   937,705,474   5 Extended
/dev/sdc5          39,065,600    58,595,327    19,529,728  82 Linux swap / Solaris
/dev/sdc6          58,597,376    78,127,103    19,529,728  83 Linux
/dev/sdc7          78,129,152   976,771,071   898,641,920  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BCBA-746B                              vfat       PENDRIVE
/dev/sdc1        7eca0f30-d942-4d0a-99b3-421dba729060   ext2       
/dev/sdc5        3fee46a5-1e62-4406-9fad-03a715787728   swap       
/dev/sdc6        1b85a208-96ea-4dd4-a073-ff72e0f850f5   ext4       
/dev/sdc7        8fff2199-0e50-4a65-a3ef-712fcd0fa22b   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/7eca0f30-d942-4d0a-99b3-421dba729060 ext2       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc6        /media/1b85a208-96ea-4dd4-a073-ff72e0f850f5 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc7        /media/8fff2199-0e50-4a65-a3ef-712fcd0fa22b ext4       (rw,nosuid,nodev,uhelper=udisks)


========================= sda1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

============================= sdc1/grub/grub.cfg: ==============================

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
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root 1b85a208-96ea-4dd4-a073-ff72e0f850f5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 7eca0f30-d942-4d0a-99b3-421dba729060
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eca0f30-d942-4d0a-99b3-421dba729060
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1b85a208-96ea-4dd4-a073-ff72e0f850f5 ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eca0f30-d942-4d0a-99b3-421dba729060
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=1b85a208-96ea-4dd4-a073-ff72e0f850f5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eca0f30-d942-4d0a-99b3-421dba729060
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 7eca0f30-d942-4d0a-99b3-421dba729060
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
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

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.165149689 = 17.357197312   grub/core.img                                  1
  16.196422577 = 17.390776320   grub/grub.cfg                                  1
   0.091060638 = 0.097775616    initrd.img-2.6.38-8-generic                    5
   0.031745911 = 0.034086912    vmlinuz-2.6.38-8-generic                       3

=============================== sdc6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc6 during installation
UUID=1b85a208-96ea-4dd4-a073-ff72e0f850f5 /               ext4    errors=remount-ro 0       1
/dev/sdc1       /boot           ext2    defaults        0       2
# /home was on /dev/sdc7 during installation
UUID=8fff2199-0e50-4a65-a3ef-712fcd0fa22b /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=3fee46a5-1e62-4406-9fad-03a715787728 none            swap    sw              0       0
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

---

### Post by JoshSTJ on 2011-09-29
Sorry for the bump.

I brought it to Geek Squad, and was told it won't work because it's a portable hard drive and doesn't have it's own power supply.

Before putting down over $100 for one with it's own power supply... can someone please verify that this is true?

---

### Post by dwasifar on 2011-09-29
I suppose it's possible it has something to do with the drive's power, but I think it's very unlikely.  If the drive is powered up and spun up by the time the BIOS starts looking for the boot sector, you should have no problem.  I'd guess it has more to do with the external drive's hardware interface.  I have run across USB external drives before that just would not let you do some things you should be able to do, like format them to a Linux filesystem.  This could be one of those things.

Frankly, I think you'd be better off using a 32GB flash drive than a 500GB external HD.  And you'd be even better off not trying to run from an external drive at all.  Why do you need to do it that way, if you don't mind my asking?  Why not set up dual boot or Wubi on your internal HD instead?

---

### Post by Kixtosh on 2011-09-30
I'm not sure why the drive wouldn't work either, but I'm not convinced it's a power issue, as long as the BIOS allows you to boot from USB.

What type of laptop are we talking about, and have you researched pricing for replacing the internal hard drive? There are a lot of laptop hard drives around for less than $100 (but they might be smaller than 500GB).

I don't like the Wubi suggestion, however. It seems to be riddled with difficulties that are easily avoided, and I saw no mention of the requirement to dual boot anyway.

---

### Post by dwasifar on 2011-09-30
> **Kixtosh said:**
> I don't like the Wubi suggestion, however. It seems to be riddled with difficulties that are easily avoided, and I saw no mention of the requirement to dual boot anyway.

That was an assumption on my part.  Typically people boot from a USB device to load an OS other than the one installed in the system.  From what you wrote, you're assuming he's booting from USB to avoid replacing a broken internal drive.  I've never seen anyone do that as a permanent solution, but I suppose it's marginally possible that someone would.  Maybe the OP can shed some light on it for us.

---

### Post by 3rdalbum on 2011-09-30
You say you've set up the BIOS to boot up the external hard drive. By default, Ubuntu 11.04 should install the bootloader to the external hard disk, but I'm wondering if it has been installed instead to the internal hard disk for some reason.

If you change your BIOS back to boot from the internal hard drive, do you get a menu that allows you to switch between Windows and Ubuntu? If so, then the bootloader has been installed to the internal disk.

---

### Post by westie457 on 2011-09-30
Is the dead drive still connected?
If so then remove it and try rebooting.

---

### Post by Kixtosh on 2011-09-30
> **dwasifar said:**
> ...  From what you wrote, you're assuming he's booting from USB to avoid replacing a broken internal drive. ...
> **JoshSTJ said:**
>  ...Today I bought a Toshiba 500 gig external hard drive because the hdd in my laptop died.  I was previously running the live version of Ubuntu from a 2 gig flash drive, and was finally able to get an external hard drive to install it permanently on. ...
It looks that way, but I don't understand why it wouldn't be simpler to just replace the broken drive completely. He might even be able to swap the new 500GB Toshiba drive for the internal one, if it's compatible with his laptop (physical dimensions, speed of rotation and heat generation, connector etc.). Then he could access whatever is still on the broken internal drive from the Toshiba drive enclosure.

---

### Post by j32wreck on 2011-10-09
I am having the same problem.  I have searched for a week for a solution and tried them all.  
 
I am trying to install and run Ubuntu from an external HD just because I want to.  I realize the simplicity of just installing it on the internal drive, but that is not the objective.
 
WD 1TB passport.
 
I have tried partitioning using gpart and through windows programs( mini tools partition wizard).  I have tried installing from a Ubuntu thumb drive iso (16 gb flash drive which boots and operates fine, but I want more).
 
I have tried just using the drive to install the iso to no avail.  I have tried to install on partitions, the whole drive, every combination there of I can think of.
 
I have tried using /boot, /, /home, and swap of varying combinations and sizes.
 
My bios is up to date and set to boot from USB Flash and USB HD prior to internal HD.
 
I have tried changing legacy support to enable or disable.
 
All results the same. 
 
I too am guessing the drive has plenty of power as it works just fine as an secondary drive both in windows and ubuntu.
 
Stumped novice.

---

### Post by gypsumwolf on 2012-04-05
I know this is old, but...

I have had numerous times where I have gotten Disk Read Error or random characters show up. This, for me, has NEVER been because of a bad drive.

Its because your MBR is corrupted. To solve this with a windows 7 disk, boot and do a repair and choose the option for command prompt and type: bootrec.exe /fixmbr

It will fix it.

Or using Linux, (DANGEROUS BACK UP YOUR DATA FIRST) load a live usb or cd and install "wipe" and do: wipe /dev/sda

and then after it runs for a few seconts to a minute just hit "ctrl" + "c" (Or it will take a extremely long time and wipe your whole drive.

and then reinstall grub or grub2 or Operating System(s)...

---

