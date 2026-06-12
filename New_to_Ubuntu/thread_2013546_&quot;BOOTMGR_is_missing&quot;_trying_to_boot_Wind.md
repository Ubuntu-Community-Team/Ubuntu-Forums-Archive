---
title: "&quot;BOOTMGR is missing&quot; trying to boot Windows 7 with Grub2"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by drblitzen on 2012-07-01
I installed Windows 7 on /dev/sda4, then with a Gentoo-minimal CD manually set and formatted sda1 through sda3 as /boot, / and swap  (which probably wiped whatever Windows had in the 100MB sda1) before changing my mind and installing Ubuntu onto them without it reformatting again. While it didn't give me a "You have Windows here, dual boot?" option, it got Grub2 booting Ubuntu fine. It did not, however, include an entry for Windows 7.

Not sure how os-prober works, and wondering why it didn't find the Windows partition (or at least put anything about it in /etc/grub.d/30_os-prober). The /dev/sda4 partition apparently wasn't added to /etc/fstab during installation,  but can be mounted fine.

I thus attempted to manually piece together an entry  into /etc/grub.d/40_custom from examples I've seen on this forum:
```

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" --class windows --class os {
           insmod part_msdos
           insmod ntfs
           set root='(hd0,msdos4)'
           search --no-floppy --fs-uuid --set=root D414B7D314B7B6B8
           chainloader +1
}

```(The UUID was obtained by running "blkid")

When selecting the "Windows 7" entry at the GRUB menu at boot time, however, it gives me "BOOTMGR is missing. Ctrl-alt-del to reboot" or some such.

Here is the output of the boot info script:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Boot file info:      Grub2 (v1.97-1.98) in the file /boot.0800 looks at 
                       sector 1 of the same hard drive for core.img, but 
                       core.img can not be found at this location.
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img /map

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab /etc/lilo.conf

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem „“

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       192,779       192,717  83 Linux
/dev/sda2             192,780   117,386,954   117,194,175  83 Linux
/dev/sda3         117,386,955   139,266,047    21,879,093  82 Linux swap / Solaris
/dev/sda4         139,266,048   976,771,071   837,505,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 239d9b04-57cc-4b36-8ea7-99198bd76495   swap       
/dev/sda1        0b450a23-4b1c-4dfd-9c17-958ac2cf2f14   ext2       
/dev/sda2        7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f   ext3       
/dev/sda4        D414B7D314B7B6B8                       ntfs       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot                    ext2       (rw)
/dev/sda2        /                        ext3       (rw,errors=remount-ro,commit=0)


============================= sda1/grub/grub.cfg: ==============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
set locale_dir=($root)/grub/locale
set lang=de_DE
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
menuentry 'Ubuntu, mit Linux 3.0.0-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    linux    /vmlinuz-3.0.0-22-generic root=UUID=7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f ro   quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-22-generic
}
menuentry 'Ubuntu, mit Linux 3.0.0-22-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    echo    'Linux 3.0.0-22-generic wird geladen …'
    linux    /vmlinuz-3.0.0-22-generic root=UUID=7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /initrd.img-3.0.0-22-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    linux    /vmlinuz-2.6.38-8-generic root=UUID=7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f ro   quiet splash vt.handoff=7
    initrd    /initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, mit Linux 2.6.38-8-generic (Wiederherstellungsmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    echo    'Linux 2.6.38-8-generic wird geladen …'
    linux    /vmlinuz-2.6.38-8-generic root=UUID=7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f ro single 
    echo    'Initiale Ramdisk wird geladen …'
    initrd    /initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 0b450a23-4b1c-4dfd-9c17-958ac2cf2f14
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root D414B7D314B7B6B8
    chainloader +1
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  2
               =                grub/grub.cfg                                  1
               =                initrd.img-2.6.38-8-generic                   93
               =                initrd.img-3.0.0-22-generic                   82
               =                vmlinuz-2.6.38-8-generic                      19
               =                vmlinuz-3.0.0-22-generic                      19

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=7d7ea2ba-13b7-4094-9aba-f9cdb77e3b5f /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0b450a23-4b1c-4dfd-9c17-958ac2cf2f14 /boot           ext2    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=016ebfd6-f242-4848-8216-63b001383518 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

============================= sda2/etc/lilo.conf: ==============================

--------------------------------------------------------------------------------
boot=/dev/sda
prompt
timeout=50
lba32
compact
vga=normal
read-only
menu-title="Bob's Studio"
default=ubuntu
image=/boot/vmlinuz-3.0.0-22-generic
    root=/dev/sda2
    label=ubuntu
    initrd=/boot/initrd.img-3.0.0-22-generic
other=/dev/sda4
    label=Win7
    boot-as=0x80 #must be C:
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                initrd.img                                    82
               =                initrd.img.old                                93
               =                vmlinuz                                       19
               =                vmlinuz.old                                   19

=============================== StdErr Messages: ===============================

xz: (stdin): Komprimierte Daten sind korrupt
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

```(The lilo.conf part was from having installed LILO instead, since that's what I'm familiar with. It did not work either.)

Thanks.

---

### Post by mapes12 on 2012-07-01
Have you tried Boot Repair:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2012-07-01
GRUB did find the widows partition.  The boot doesn't work because there are no boot files there.  If your PC came preinstalled with Win7, those boot files were in a different partition -- one that you erased or removed.

---

### Post by NikTh on 2012-07-01
Hi , 
you can recover missing boot files with testdisk . Check out this tutorial --> [http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628) its old post so if you have any questions ask here. 
I did it sometime with windows xp and worked . I don't know if its the same for windows 7. 
Good luck.

---

### Post by oldfred on 2012-07-01
As mentioned above, two of your windows boot files are missing and they normally are in the 100MB hidden Windows boot/repair partition. That has nothing to do with an Ubuntu /boot partition (which desktops do not normally need).

It looks like you overwrote your sda1 Windows boot partition with the Ubuntu /boot files.

Windows does not have to have the separate boot partition and you can repair your Windows since it is a primary partition. But the boot flag has to be moved from sda1 to sda4. Windows uses boot flag, grub does not use boot flag. And Windows normally only repairs the "active" partition which is the one with the boot flag. Use gparted or Windows repairCD to move boot flag/active partition first. Then you can run Windows repairs.

Boot files You are missing the two in [COLOR=Red]red[/COLOR].:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the [COLOR=Red]first two files[/COLOR] are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

[COLOR=Black]oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

Details:
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)


[/COLOR]

---

### Post by drblitzen on 2012-07-01
Thanks mapes12, Mark Phelps, NikTh and oldfred.

Marking the ntfs partition as bootable with gparted made grub2's os-prober now find it without having to create a custom entry, and then the Windows 7 CD restored the files with a boot repair.

Cool forum.

---

