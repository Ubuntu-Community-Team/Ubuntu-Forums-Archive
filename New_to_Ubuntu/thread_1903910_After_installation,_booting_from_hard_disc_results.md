---
title: "After installation, booting from hard disc results in a hang at BusyBox shell"
date: 2012-01-03
forum: New to Ubuntu
---

### Post by Cashughes on 2012-01-03
Hello Ubuntu forms. This is my first post. I've got a problem with something, but I'm not entirely sure what. I've search the forms the best I could, but I could not find anything to help my problem specifically.

     I'm having problems starting up my installation of Ubuntu 11.10. When launching the demo from a LiveCD I had to enable the option **acpi=off** for it to boot. When I do not enable said option all I get is the BusyBox v1.18.4 built-in shell with the error:

```
(initramfs) Unable to find a medium containing a live file system.
```     However, when I do enable that option, after waiting 15~30 seconds at the Ubuntu loading screen, I see a screen of 11 black and white alternating horizontal bars with random color pixels scattered across the screen. After waiting for another 15~25 seconds that screen disappears and the desktop loads. 

     I installed via the 'Install Ubuntu 11.10' file on the desktop after launching the 'Test Ubuntu' option. Installation went fine, and it produced no errors.

    When I restart my computer and boot from hard drive I end up at the GRUB screen with options to boot normal or safe mode and some memory tests. I choose the normal kernal (at the top) and wait for it to boot. It ends up sending me to the same BusyBox shell as before but without any messages underneath. It just stalls at that screen with **(initramfs)** and no cursor. Neither my mouse nor my keyboard work at this stage of the boot process (No lights/ Input).

     Any help would be greatly appreciated, for I have overwritten my previous operating system and am currently running from the LiveCD.

**Edit:** Upon trying to boot in Safety Mode there was a lot of text  that was spit out while trying to boot. (After Grub) It included  something about a missing file, and that that was the reason it was  dumping me to the shell. Unfortunately, it scrolled by so fast I  couldn't write down what was missing. It included a lot of numbers.

---

### Post by Cashughes on 2012-01-03
If there is any information that I should be including in this thread please let me know! I've been trying to figure this thing out all day now, and it is starting to turn me off on linux. I'm installing the AMD64 distribution, so would that have anything to do with my problem?

Also, I re-ran the safety mode thing and got the numbers/letters. The message said something like: "Cannot find dev/disk/by-uuid/bdcdd35b-0bc5-48e8-x... I couldn't get the last few.

---

### Post by Cashughes on 2012-01-03
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 349127392 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   781,252,607   781,250,560  83 Linux
/dev/sda2         781,254,654   976,771,071   195,516,418   5 Extended
/dev/sda5         781,254,656   791,021,567     9,766,912  82 Linux swap / Solaris
/dev/sda6         791,023,616   888,680,447    97,656,832  83 Linux
/dev/sda7         888,682,496   976,771,071    88,088,576  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        bdcdd35b-0bc5-49e8-b537-ab14ba06d761   ext4       
/dev/sda5        701817bb-8098-4875-9d42-efbf31ffdd74   swap       
/dev/sda6        2908dc19-a46d-4292-9729-3557d3810d47   ext4       
/dev/sda7        7d07fc01-cf2a-484c-8ffb-dd93dbbe2a52   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=bdcdd35b-0bc5-49e8-b537-ab14ba06d761 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=bdcdd35b-0bc5-49e8-b537-ab14ba06d761 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bdcdd35b-0bc5-49e8-b537-ab14ba06d761
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bdcdd35b-0bc5-49e8-b537-ab14ba06d761 /               ext4    errors=remount-ro 0       1
# /backup was on /dev/sda7 during installation
UUID=7d07fc01-cf2a-484c-8ffb-dd93dbbe2a52 /backup         ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=2908dc19-a46d-4292-9729-3557d3810d47 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=701817bb-8098-4875-9d42-efbf31ffdd74 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 166.476940155 = 178.753253376  boot/grub/core.img                             1
  72.135696411 = 77.455114240   boot/grub/grub.cfg                             1
   2.141601562 = 2.299527168    boot/initrd.img-3.0.0-12-generic               2
  72.133979797 = 77.453271040   boot/vmlinuz-3.0.0-12-generic                  1
   1.977973938 = 2.123833344    boot/vmlinuz-3.0.0-14-generic                  1
   2.141601562 = 2.299527168    initrd.img                                     2
  72.133979797 = 77.453271040   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  77 77 77 77 77 77 77 77  77 77 77 77 77 77 77 77  |wwwwwwwwwwwwwwww|
*
000001b0  77 77 77 77 77 77 77 77  77 77 77 77 77 77 00 fe  |wwwwwwwwwwwwww..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 95 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 08  95 00 00 28 d2 05 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Cashughes on 2012-01-04
Resolved the problem after a lot of screwing around with the BIOS settings, a few re-installations, and some patience.

---

