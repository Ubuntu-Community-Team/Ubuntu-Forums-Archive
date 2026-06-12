---
title: "Running Ubuntu from HDD - Won't boot"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by matbob3 on 2011-11-27
Hi,

I've installed Ubuntu 10.04 on my external hard drive, but it will not boot Ubuntu when I start the computer with the hard drive plugged in, it just starts up Windows instead, which is what I have installed on the computer. I have already changed the BIOS settings to make the HDD second highest priority (second to a live CD, so I can run the CD if I need to) but this hasn't worked. I can provide the specs of either the computer or the HDD if needed.

If anyone can help I would appreciate it,
Thanks.

---

### Post by coffeecat on 2011-11-27
Welcome to the forum!

This sounds like a grub misconfiguration in your external drive. If so, it would be easily fixed, but first we need an overview of your system.

Boot up the live Ubuntu CD with the external drive plugged in and switched on. Choose 'try Ubuntu' to get to the live desktop, ensure you are connected to the internet, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by matbob3 on 2011-11-27
Ok, thanks, here it is:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   464,278,499   464,278,437   7 NTFS / exFAT / HPFS
/dev/sda2         464,278,500   488,392,064    24,113,565   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    48,828,415    48,826,368  83 Linux
/dev/sdb2          48,830,462   839,841,791   791,011,330   5 Extended
/dev/sdb5          48,830,464    58,593,279     9,762,816  82 Linux swap / Solaris
/dev/sdb6          58,595,328   644,530,175   585,934,848  83 Linux
/dev/sdb7         644,532,224   839,841,791   195,309,568   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        09803C9932F31857                       ntfs       
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY
/dev/sdb1        63d9031e-a707-44ac-817d-f9544f464b5a   ext4       
/dev/sdb5        43378e6d-913b-4b6c-96bc-e83b0516d2b7   swap       
/dev/sdb6        e6c80638-3e18-4d2b-899c-30df36dc2634   ext4       
/dev/sdb7        24E6-AF1B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 09803c9932f31857
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=e6c80638-3e18-4d2b-899c-30df36dc2634 /home           ext4    defaults        0       2
# /shared was on /dev/sdb7 during installation
UUID=24E6-AF1B  /shared         vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=43378e6d-913b-4b6c-96bc-e83b0516d2b7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.145816803 = 2.304053248    boot/grub/core.img                             1
  12.310081482 = 13.217849344   boot/grub/grub.cfg                             1
   2.153236389 = 2.312019968    boot/initrd.img-2.6.32-21-generic              1
   2.132167816 = 2.289397760    boot/vmlinuz-2.6.32-21-generic                 1
   2.153236389 = 2.312019968    initrd.img                                     1
   2.132167816 = 2.289397760    vmlinuz                                        1


```

---

### Post by coffeecat on 2011-11-27
Hi - fairly straightforward problem, easily resolved. There is no bootloader in the mbr of your external hard drive, which appears as sdb in the boot script output.

Before you follow the below instructions, I notice that you have syslinux installed in the mbr of sda, your internal drive with Windows. Which is a bit odd. Normally, you would have the Windows bootloader. Do you remember installing anything to the mbr of sda?

Anyway, so long as you can boot Windows without the external drive plugged in, there's nothing to do about it. If you can boot Windows OK, then boot up the live Ubuntu CD with the external drive plugged in and switched on, and choose the live desktop. Open a terminal, and:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```

Make sure you type sdb at the end of the second command. You don't want grub going to the mbr of sda. Now shut down from the live CD session.

If you now boot without the external drive plugged in, it will boot Windows. So long as the BIOS is set with priority for the external drive before that for the internal drive, if you bootup with the external drive plugged in and powered on, you will be presented with a grub menu and you will be able to boot into Ubuntu. There are also two Windows entries in your grub menu which should work. If they don't, post back.

Doing it this way means that you will still be able to boot into Windows without the external drive plugged in. If you install grub to the internal drive, sda, you would need the external drive plugged in every time you boot. One disadvantage though is that I see you have a shared FAT32 partition on sdb. Obviously, if you boot Windows without the external drive, you would need to plug the drive in in order to access the partition.

---

### Post by matbob3 on 2011-11-27
Hi,

Thank you very much :D That worked brilliantly and I'm happily using Ubuntu now!

About what you said: > syslinux installed in the mbr of sd  I don't really know much about the MBR, but I don't remember installing anything that sounds like that.


Also, > There are also two Windows entries in your grub menu which should work I did see both of these in the GRUB screen - does it matter which one I use to get into windows?

Again thanks for your help.

---

### Post by coffeecat on 2011-11-27
> **matbob3 said:**
> 
Also,  I did see both of these in the GRUB screen - does it matter which one I use to get into windows?


The first entry boots to sda1 which has all the Windows boot files, and the second to sda2 which has some of the boot files, so I'm not clear how your Windows installation is organised. The first entry should work OK, but try the second one to see what happens. The worst that could happen is failing with an error message.

---

### Post by matbob3 on 2011-11-28
Hi again, 

Today when I went to turn on my computer, I could not access either of my operating systems because of a grub error. I remember this happening once before when I previously attempted to install Ubuntu, so I used the live CD to search for a solution online.

I found a resource that showed me how to reinstall grub through the terminal, and now I can access Ubuntu but I cannot access windows. 

Any ideas?

Thanks.

---

### Post by coffeecat on 2011-11-28
> **matbob3 said:**
> 
I found a resource that showed me how to reinstall grub through the terminal, and now I can access Ubuntu but I cannot access windows. 


Oh dear. Online resources. Treat with caution. I can think of several things that could have gone wrong, but we need to see what has.

Boot into Ubuntu and run the boot info script as before. Post the results as before and we'll take it from there. Please confirm one thing, not that it may matter much. Are you running Windows 7 or Vista?

---

### Post by matbob3 on 2011-11-28
Here is the boot info:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   464,278,499   464,278,437   7 NTFS / exFAT / HPFS
/dev/sda2         464,278,500   488,392,064    24,113,565   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    48,828,415    48,826,368  83 Linux
/dev/sdb2          48,830,462   839,841,791   791,011,330   5 Extended
/dev/sdb5          48,830,464    58,593,279     9,762,816  82 Linux swap / Solaris
/dev/sdb6          58,595,328   644,530,175   585,934,848  83 Linux
/dev/sdb7         644,532,224   839,841,791   195,309,568   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        09803C9932F31857                       ntfs       
/dev/sda2        2C88743C8874071C                       ntfs       HP_RECOVERY
/dev/sdb1        63d9031e-a707-44ac-817d-f9544f464b5a   ext4       
/dev/sdb5        43378e6d-913b-4b6c-96bc-e83b0516d2b7   swap       
/dev/sdb6        e6c80638-3e18-4d2b-899c-30df36dc2634   ext4       
/dev/sdb7        24E6-AF1B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb6        /home                    ext4       (rw)
/dev/sdb7        /shared                  vfat       (rw,utf8,umask=007,gid=46)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
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
menuentry 'Ubuntu, with Linux 2.6.32-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    echo    'Loading Linux 2.6.32-35-generic ...'
    linux    /boot/vmlinuz-2.6.32-35-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-35-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=63d9031e-a707-44ac-817d-f9544f464b5a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 63d9031e-a707-44ac-817d-f9544f464b5a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 09803C9932F31857
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2C88743C8874071C
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=e6c80638-3e18-4d2b-899c-30df36dc2634 /home           ext4    defaults        0       2
# /shared was on /dev/sdb7 during installation
UUID=24E6-AF1B  /shared         vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sdb5 during installation
UUID=43378e6d-913b-4b6c-96bc-e83b0516d2b7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   2.134681702 = 2.292097024    boot/grub/core.img                             1
  12.302459717 = 13.209665536   boot/grub/grub.cfg                             2
   2.153236389 = 2.312019968    boot/initrd.img-2.6.32-21-generic              1
   2.203384399 = 2.365865984    boot/initrd.img-2.6.32-35-generic              1
   2.132167816 = 2.289397760    boot/vmlinuz-2.6.32-21-generic                 1
   2.254741669 = 2.421010432    boot/vmlinuz-2.6.32-35-generic                 1
   2.203384399 = 2.365865984    initrd.img                                     1
   2.153236389 = 2.312019968    initrd.img.old                                 1
   2.254741669 = 2.421010432    vmlinuz                                        1
   2.132167816 = 2.289397760    vmlinuz.old                                    1


```Also, I just found that I can log in to windows, but only if I select it instead of Ubuntu at the GRUB screen while my HDD is plugged in, however, if the HDD is not plugged in, it goes to some sort of GRUB terminal. I am using vista by the way. (Yeah, I'm not too happy about it either.)

---

### Post by coffeecat on 2011-11-28
I can only post quickly because I must log off for a couple of hours. I can see several problems already in the boot script output which are entirely a result of following whatever you found online.

* You have managed to install grub to the mbr of sda. You don't want it there - for reasons see my earlier post. You need Windows booting code or equivalent.

* Grub in sda is looking for /boot/grub in sda1 which is your Windows partition. /boot/grub should be in your Ubuntu Linux partition.

* In fact you do have /boot/grub in the Windows sda1 boot sector and it has no business being there. I'm surprised you can boot into Windows at all. Windows is usually rendered unbootable if grub is installed to its partition boot sector. 

You need to:

1 - install Windows mbr to the mbr of sda with a Windows installation disk with "bootrec /FixMbr". If you don't have one, you can install functionally equivalent code with an Ubuntu live CD. See here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

lilo works perfectly well as a Windows bootloader if installed as described in that post.

2 - You need to repair the Windows sda1 boot sector. Here is one way of doing it:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I've never done that myself, but I've seen several threads where that has worked.

If you do both of those, you should be able to boot Windows if the external drive is not plugged in. I haven't looked closely at the rest of the boot script output yet, but I shall do so when I next log back in again to see what other problems there might be.

---

### Post by matbob3 on 2011-11-28
I think that may have worked :) 

I don't really know how to thank you enough, you have been of amazing help to me; thanks for putting up with my mistakes - I'll be sure to be more careful when following advice online next time.

Hopefully it will stay working this time, but I'll be sure to post back if it doesn't.

Much appreciated,
matbob3.

---

### Post by coffeecat on 2011-11-28
> **matbob3 said:**
> I think that may have worked :) 

Excellent.

Can you confirm that everything is working now? I'm still concerned about the grub error you saw before you tried the online "resource" fix you found - we haven't explained that. What *should* happen now is that if you boot up without the external drive attached, it will boot straight into Windows. If you boot up with the external drive attached it should give you a grub menu from which you can choose Ubuntu or Windows. At least, that is what should happen. :) Post back if not.

---

### Post by matbob3 on 2011-11-29
Yes it boots into windows without the HDD :)

And I got the GRUB error no longer shows; I got it the last time I attempted to install ubuntu, but I found a solution pretty soon and fixed it. The error, if I remember correctly, said something like "disk does not exist", and I think it was something to do with the BIOS settings.

---

### Post by matbob3 on 2011-11-29
And with regards to the fix I found online that made things worse, I realise what I did wrong now - the code was written to install GRUB to sda, which is why the Ubuntu bootloader was in the windows partition, I should have changed it to sdb.

---

