---
title: "Ubuntu 12.04: Grub Rescue triggered from Windows Recovery Mode"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by Celereon on 2013-05-07
Hi, first post:

I'll be quick. I installed Ubuntu 12.04 alongside Windows 7 and have been using it fine for a few months. I misclicked and went into Windows Recovery Mode from the boot menu, didn't think anything of it, just exited it. Then I got the dreaded grub rescue problem.

I tried [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting) but when I type insmod normal I get "error: unknown filesystem". When I run my LiveCD and run "fdisk -l" it comes up with a few options (which I can post if you think it's useful) but "Linux" is not one of them.

I'm going to try boot repair now but thought I'd post this here, not just in case it doesn't work but also since in my reading I haven't found anything similar and this hasn't been fixed by any of the above methods (yet).

Any help would be so, so appreciated. I'm in some time pressure here too.

Cheers,
Celereon

---

### Post by oldfred on 2013-05-07
Post link to BootInfo report from Boot-Repair.

What you did seems to rewrite partition table. If that is all that was done, you may be able to use testdisk to restore Linux partitions.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

---

### Post by Celereon on 2013-05-08
Thanks for your reply.

Boot-repair fixed Windows but I think grub is well and truly lost: upon login it boots straight to Windows now. I am not too fussed (only thing of value I lost to Linux is the 50GB or so I partitioned for it) and I'll probably just buy a dedicated netbook for Ubuntu later if I need it. That way I don't risk messing up my Windows stuff.

The link from boot-repair is here:
[http://paste.ubuntu.com/5640863/](http://paste.ubuntu.com/5640863/)

Cheers
Celereon

---

### Post by Chase993 on 2013-05-08
boot-repair is for fixing the Windows boot loader. It will overwrite the Grub loader...

---

### Post by mastablasta on 2013-05-08
> **Celereon said:**
> Hi, first post:

I'll be quick. I installed Ubuntu 12.04 alongside Windows 7 and have been using it fine for a few months. 


> **Celereon said:**
> Thanks for your reply.

Boot-repair fixed Windows but I think grub is well and truly lost: upon login it boots straight to Windows now. I am not too fussed (only thing of value I lost to Linux is the 50GB or so I partitioned for it) and I'll probably just buy a dedicated netbook for Ubuntu later if I need it. That way I don't risk messing up my Windows stuff.

The link from boot-repair is here:
[http://paste.ubuntu.com/5640863/](http://paste.ubuntu.com/5640863/)

Cheers
Celereon

wha? where is linux partion? on what disk?

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31459327    15728640   27  Hidden NTFS WinRE
/dev/sda2   *    31459328    31664127      102400    7  HPFS/NTFS/exFAT
/dev/sda3        31664128  1170733479   569534676    7  HPFS/NTFS/exFAT
/dev/sda4      1170735102  1465147391   147206145    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1452869632  1465147391     6138880   82  Linux swap / Solaris



```

---

### Post by oldfred on 2013-05-08
The recovery mode boot must have eliminated the Linux entry in the partition table. You have a large gap from start of extended to start of swap which looks like it was your missing partition. Testdisk should be able to recover missing partition and then Boot-Repair will see a Linux install and repair grub. It repaired only Windows as that was all it found.

         [URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]https://help.ubuntu.com/community/DataRecovery#Lost%20Partition

[/URL]
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
      [/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

    [URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

[URL="https://help.ubuntu.com/community/DataRecovery#Lost%20Partition"]
[/URL]

---

### Post by Celereon on 2013-06-02
Hi,

Sorry it took so long to reply; I've been busy (and also putting it off since I hadn't needed Ubuntu again until now, and also I was too scared to fiddle any more with it)

Short version: I had Windows but not Ubuntu, now I have Ubuntu but not Windows (but Grub is back)

Long version: I ran testdisk, as recommended, and it found the Linux partition. This partition, along with all the other partitions (the default system one with the factory presets, for example), was listed as D ("delete") - so I switched it to L ("logical") hoping this would restore Linux. Note that I could see all the files within testdisk (I didn't have to repair anything, there were never any errors).

When I rebooted I was met with a blinking underscore. Oh dear.

Booted in Ubuntu Live CD and ran boot-repair again, and now I have Linux but not Windows.

I am thinking I might try to run testdisk again but switch the Linux, Linux swap and the HPFS - NTFS drives all over to L and see if that restores both OSs at once. I really don't think I'm cut out for all this haha. Any advice?

Paste: [http://paste.ubuntu.com/5725599/](http://paste.ubuntu.com/5725599/)

Cheers

EDIT: A Screenshot is below of what I am currently seeing in testdisk in Ubuntu. I've played with things but haven't hit enter; originally all five partitions said "D" for "delete" - what should I set them to?
[ATTACH=CONFIG]243427[/ATTACH]

---

### Post by Celereon on 2013-06-02
UPDATE: I've run testdisk and set the primary partition to GATEWAY and Linux to Logical (as in the screenshot above).

I've reinstalled grub, running update-grub still doesn't find Windows. Also I've now lost the mem86 memory test option in grub when I reboot.

Output from bootinfoscript:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *     31,664,128 1,170,733,472 1,139,069,345   7 NTFS / exFAT / HPFS
/dev/sda2       1,170,735,048 1,452,870,404   282,135,357   f W95 Extended (LBA)
/dev/sda5       1,170,735,104 1,452,869,631   282,134,528  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C02A880B2A880120                       ntfs       Gateway
/dev/sda5        fedbe250-d83d-469e-8991-eaeb41433a51   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
  set locale_dir=($root)/boot/grub/locale
  set lang=en_AU
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.5.0-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    linux    /boot/vmlinuz-3.5.0-27-generic root=UUID=fedbe250-d83d-469e-8991-eaeb41433a51 ro   quiet splash acpi_osi=Linux acpi_backlight=vendor $vt_handoff
    initrd    /boot/initrd.img-3.5.0-27-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    echo    'Loading Linux 3.5.0-27-generic ...'
    linux    /boot/vmlinuz-3.5.0-27-generic root=UUID=fedbe250-d83d-469e-8991-eaeb41433a51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-27-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=fedbe250-d83d-469e-8991-eaeb41433a51 ro   quiet splash acpi_osi=Linux acpi_backlight=vendor $vt_handoff
    initrd    /boot/initrd.img-3.5.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    echo    'Loading Linux 3.5.0-23-generic ...'
    linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=fedbe250-d83d-469e-8991-eaeb41433a51 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root fedbe250-d83d-469e-8991-eaeb41433a51
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
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
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=fedbe250-d83d-469e-8991-eaeb41433a51 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c24c1f5f-b4bd-4f3b-a874-96cf2a5196d6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 560.421459198 = 601.747959808  boot/grub/core.img                             1
 576.527385712 = 619.041566720  boot/grub/grub.cfg                             1
 569.623844147 = 611.628945408  boot/initrd.img-3.5.0-23-generic               1
 569.530166626 = 611.528359936  boot/initrd.img-3.5.0-27-generic               2
 558.723583221 = 599.924879360  boot/vmlinuz-3.5.0-23-generic                  1
 569.965763092 = 611.996078080  boot/vmlinuz-3.5.0-27-generic                  1
 569.530166626 = 611.528359936  initrd.img                                     2
 569.623844147 = 611.628945408  initrd.img.old                                 1
 569.965763092 = 611.996078080  vmlinuz                                        1
 558.723583221 = 599.924879360  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt


```

---

