---
title: "boot menu unreadable in 12.04"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2012-10-29
Hi, 

I have a multiple boot system with different partitions where I install different flavours of Linux and Ubuntus for testing with Ubuntu controlling grub. Except for a main Ubuntu installation which I use as a 'real system' I  install and reinstall other OSes frequently, sometimes erasing them and replacing them with a new release. Everytime I make these changes I boot into Ubuntu and run sudo update-grub and it has been working fine. But since 12.04 it seems that old grub entries are not being removed even after running sudo update-grub successfully in the terminal (which reports the oses and their partitions correctly) so the screen is full of oses and kernel that no longer exists and I have gibberish lines like 

```
Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)
``` (is it for sdc7 or sdc9?)

The boot screen is so cluttered that it is completely unreadable. Now I am in the ridiculous position that I can't even find my oses to boot into! Please please help!!!!

---

### Post by newb85 on 2012-10-29
Are you saying that the feedback from update-grub does or does not include the removed OSes?

---

### Post by monkeybrain2012 on 2012-10-29
OS has been removed but still shows up on boot screen (same for removed kernels)

Run sudo update grub in the terminal and it is correct, but the boot screen is not being updated.

---

### Post by ajgreeny on 2012-10-29
> **monkeybrain2012 said:**
> OS has been removed but still shows up on boot screen (same for removed kernels)

Run sudo update grub in the terminal and it is correct, but the boot screen is not being updated.
Are you absolutely certain that the Ubuntu you think is supplying grub is really the one doing so?  It sounds as if there is another OS which is the one with grub.

Which OS is at the top of the menu when you see it?  Whichever of the OSs that is the first entry will be the one that supplies grub for booting the system.

Click on the boot-info-script link in my signature and follow the instructions. Paste contents of results.txt in a New Reply, then highlight entire file and click on # in toolbar (code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ CODE] paste here [ /CODE] tags.
From V60 the script output has improved formatting and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by monkeybrain2012 on 2012-10-29
Hi,  Thanks for the reply.

               ```
   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Fedora release 17 (Beefy 
                       Miracle) Kernel on an ()
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb7 
                       and looks at sector 528954744 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb9 
                       and looks at sector 362578496 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 72 for .
    Operating System:  Ubuntu 12.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    73,402,367    73,400,320  83 Linux
/dev/sda2          73,404,414   488,396,799   414,992,386   5 Extended
/dev/sda5          73,404,416   328,022,015   254,617,600  83 Linux
/dev/sda6         480,008,192   488,396,799     8,388,608  82 Linux swap / Solaris
/dev/sda7         328,024,064   448,546,815   120,522,752  83 Linux
/dev/sda8         448,548,864   480,004,095    31,455,232  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    41,945,407    41,943,360  83 Linux
/dev/sdb2          41,947,134   564,340,735   522,393,602   5 Extended
/dev/sdb5          41,947,136   343,191,551   301,244,416  83 Linux
/dev/sdb6         374,124,544   478,351,359   104,226,816   7 NTFS / exFAT / HPFS
/dev/sdb7         478,353,408   532,880,751    54,527,344  83 Linux
/dev/sdb8         532,883,456   564,340,735    31,457,280  83 Linux
/dev/sdb9         353,153,024   374,121,773    20,968,750  83 Linux
/dev/sdb10        343,193,600   353,150,975     9,957,376  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        55fdd28d-6d87-462d-8f61-d31d45f57a1a   ext4       
/dev/sda5        e99633d9-7d2f-46a6-8d03-5cec2a745d1a   ext4       
/dev/sda6        a56125dc-39c1-4126-b23f-4cca1545df41   swap       
/dev/sda7        7c6c6da9-e6c7-49bd-b57c-dba4f49426af   ext4       
/dev/sda8        099e462d-0876-4430-b10b-1631ffad96ba   ext4       _Fedora-17-i686-
/dev/sdb1        211934fe-e4d8-49aa-b623-9552dec61563   ext4       
/dev/sdb10       9f2ad884-e537-4732-bc2b-29c71a04f13f   swap       
/dev/sdb5        bc6ec861-3289-4351-8663-aa71d5a568ca   ext4       
/dev/sdb6        5E4241E25190B301                       ntfs       temdat
/dev/sdb7        8c2490f6-1e27-4508-b54c-8c2c58cfb710   ext4       
/dev/sdb8        5feefd23-a160-484a-87e7-fc1eeeb90fcf   ext4       
/dev/sdb9        66396b0d-5815-45ff-ad09-11c9d7002e95   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb5        /home                    ext4       (rw)
/dev/sdb6        /media/temdat            fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb7        /media/8c2490f6-1e27-4508-b54c-8c2c58cfb710 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb8        /media/5feefd23-a160-484a-87e7-fc1eeeb90fcf ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb9        /media/66396b0d-5815-45ff-ad09-11c9d7002e95 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 2.6.38-16-generic ...'
    linux    /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 2.6.38-15-generic ...'
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 2.6.38-14-generic ...'
    linux    /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 2.6.38-13-generic ...'
    linux    /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-13-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro   quiet splash profile vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single 
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
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora release 17 (Beefy Miracle) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 099e462d-0876-4430-b10b-1631ffad96ba
    linux /boot/vmlinuz-3.3.4-5.fc17.i686 root=/dev/sda8
    initrd /boot/initramfs-3.3.4-5.fc17.i686.img
}
menuentry "Fedora release 17 (Beefy Miracle) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 099e462d-0876-4430-b10b-1631ffad96ba
    linux /boot/vmlinuz-3.5.4-2.fc17.i686 root=/dev/sda8
    initrd /boot/initramfs-3.5.4-2.fc17.i686.img
}
menuentry "Fedora release 17 (Beefy Miracle) (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos8)'
    search --no-floppy --fs-uuid --set=root 099e462d-0876-4430-b10b-1631ffad96ba
    linux /boot/vmlinuz-3.6.2-4.fc17.i686 root=/dev/sda8
    initrd /boot/initramfs-3.6.2-4.fc17.i686.img
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=e99633d9-7d2f-46a6-8d03-5cec2a745d1a /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a56125dc-39c1-4126-b23f-4cca1545df41 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  14.194877625 = 15.241633792   boot/grub/core.img                             1
   3.952262878 = 4.243709952    boot/grub/grub.cfg                             1
  22.039974213 = 23.665242112   boot/initrd.img-2.6.38-13-generic              3
   9.533523560 = 10.236542976   boot/initrd.img-2.6.38-14-generic              3
   6.910469055 = 7.420059648    boot/initrd.img-2.6.38-15-generic              3
  24.074886322 = 25.850212352   boot/initrd.img-2.6.38-16-generic              3
   4.891601562 = 5.252317184    boot/initrd.img-2.6.38-8-generic               2
  20.838573456 = 22.375247872   boot/initrd.img-3.0.0-13-generic               1
  21.571598053 = 23.162327040   boot/vmlinuz-2.6.38-13-generic                 1
  17.997379303 = 19.324538880   boot/vmlinuz-2.6.38-14-generic                 2
  27.173160553 = 29.176958976   boot/vmlinuz-2.6.38-15-generic                 1
  23.743473053 = 25.494360064   boot/vmlinuz-2.6.38-16-generic                 1
  14.193157196 = 15.239786496   boot/vmlinuz-2.6.38-8-generic                  1
   5.423263550 = 5.823184896    boot/vmlinuz-3.0.0-13-generic                  1
  24.074886322 = 25.850212352   initrd.img                                     3
   6.910469055 = 7.420059648    initrd.img.old                                 3
  23.743473053 = 25.494360064   vmlinuz                                        1
  27.173160553 = 29.176958976   vmlinuz.old                                    1

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jun  2 11:36:47 2012
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=099e462d-0876-4430-b10b-1631ffad96ba /                       ext4    defaults        1 1
UUID=7c6c6da9-e6c7-49bd-b57c-dba4f49426af /home                   ext4    defaults        1 2
UUID=a56125dc-39c1-4126-b23f-4cca1545df41 swap                    swap    defaults        0 0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 216.392456055 = 232.349630464  boot/initramfs-3.3.4-5.fc17.i686.img           2
 225.712368011 = 242.356809728  boot/initramfs-3.5.4-2.fc17.i686.img           2
 221.846412659 = 238.205771776  boot/initramfs-3.6.2-4.fc17.i686.img           2
 214.451560974 = 230.265610240  boot/vmlinuz-3.3.4-5.fc17.i686                 1
 220.711486816 = 236.987154432  boot/vmlinuz-3.5.4-2.fc17.i686                 1
 220.881786346 = 237.170012160  boot/vmlinuz-3.6.2-4.fc17.i686                 1

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
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
menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.5.0-17-generic ...'
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-25-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-16-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-16-generic
}
menuentry "Ubuntu, with Linux 2.6.38-16-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-16-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=211934fe-e4d8-49aa-b623-9552dec61563 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc5 during installation
UUID=bc6ec861-3289-4351-8663-aa71d5a568ca /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=a56125dc-39c1-4126-b23f-4cca1545df41 none            swap    sw              0       0
# swap was on /dev/sdc10 during installation
UUID=428ccb00-b16b-4e09-9610-67ee7e0dce3a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  18.484775543 = 19.847876608   boot/grub/core.img                             1
  12.776573181 = 13.718740992   boot/grub/grub.cfg                             1
  13.092243195 = 14.057689088   boot/initrd.img-3.2.0-23-generic-pae           1
   5.568809509 = 5.979463680    boot/initrd.img-3.2.0-24-generic-pae           1
   5.740684509 = 6.164013056    boot/initrd.img-3.2.0-25-generic-pae           1
   9.404773712 = 10.098298880   boot/initrd.img-3.2.0-27-generic-pae           1
  12.489696503 = 13.410709504   boot/initrd.img-3.5.0-17-generic               3
  14.134029388 = 15.176298496   boot/vmlinuz-3.2.0-23-generic-pae              1
   4.884555817 = 5.244751872    boot/vmlinuz-3.2.0-24-generic-pae              1
   1.802528381 = 1.935450112    boot/vmlinuz-3.2.0-25-generic-pae              2
   7.857208252 = 8.436613120    boot/vmlinuz-3.2.0-27-generic-pae              1
   7.498039246 = 8.050958336    boot/vmlinuz-3.5.0-17-generic                  2
  12.489696503 = 13.410709504   initrd.img                                     3
  12.489696503 = 13.410709504   initrd.img.old                                 3
   7.498039246 = 8.050958336    vmlinuz                                        2
   7.498039246 = 8.050958336    vmlinuz.old                                    2

=========================== sdb7/boot/grub/grub.cfg: ===========================

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

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
else
  search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
    else
      search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    fi
    linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-18-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        echo    'Loading Linux 3.5.0-18-generic ...'
        linux    /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
    else
      search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos7 --hint-efi=hd1,msdos7 --hint-baremetal=ahci1,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
    else
      search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 11.04 (11.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
    else
      search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    fi
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
submenu 'Advanced options for Ubuntu 11.04 (11.04)' $menuentry_id_option 'osprober-gnulinux-advanced-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
    menuentry 'Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-13-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-3.0.0-13-generic
    }
    menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-13-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-3.0.0-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-16-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-16-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-16-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-16-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-16-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-16-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-15-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-15-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-15-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-15-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-15-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-14-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-14-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-14-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-14-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-14-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-13-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-13-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-13-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-8-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-8-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-8-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-8-generic
    }
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
    else
      search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    fi
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-211934fe-e4d8-49aa-b623-9552dec61563' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-5-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-5-generic--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-5-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-5-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-5-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-5-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-5-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-5-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-4-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-4-generic--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-4-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-4-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-4-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-4-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-4-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-4-generic
    }
    menuentry 'Ubuntu, with Linux 3.4.0-1-generic-pae (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4.0-1-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.4.0-1-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.4.0-1-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.4.0-1-generic-pae (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4.0-1-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.4.0-1-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.4.0-1-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-25-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-25-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
}

menuentry 'Fedora release 16 (Verne)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-d3086a54-8a55-4115-9950-6a14188add59' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos11'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos11 --hint-efi=hd1,msdos11 --hint-baremetal=ahci1,msdos11  d3086a54-8a55-4115-9950-6a14188add59
    else
      search --no-floppy --fs-uuid --set=root d3086a54-8a55-4115-9950-6a14188add59
    fi
    linux /boot/vmlinuz-3.1.0-7.fc16.i686 root=/dev/sdb11
    initrd /boot/initramfs-3.1.0-7.fc16.i686.img
}
submenu 'Advanced options for Fedora release 16 (Verne)' $menuentry_id_option 'osprober-gnulinux-advanced-d3086a54-8a55-4115-9950-6a14188add59' {
    menuentry 'Fedora release 16 (Verne) (on /dev/sdb11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.1.0-7.fc16.i686--d3086a54-8a55-4115-9950-6a14188add59' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos11'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos11 --hint-efi=hd1,msdos11 --hint-baremetal=ahci1,msdos11  d3086a54-8a55-4115-9950-6a14188add59
        else
          search --no-floppy --fs-uuid --set=root d3086a54-8a55-4115-9950-6a14188add59
        fi
        linux /boot/vmlinuz-3.1.0-7.fc16.i686 root=/dev/sdb11
        initrd /boot/initramfs-3.1.0-7.fc16.i686.img
    }
    menuentry 'Fedora release 16 (Verne) (on /dev/sdb11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.3.7-1.fc16.i686--d3086a54-8a55-4115-9950-6a14188add59' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos11'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos11 --hint-efi=hd1,msdos11 --hint-baremetal=ahci1,msdos11  d3086a54-8a55-4115-9950-6a14188add59
        else
          search --no-floppy --fs-uuid --set=root d3086a54-8a55-4115-9950-6a14188add59
        fi
        linux /boot/vmlinuz-3.3.7-1.fc16.i686 root=/dev/sdb11
        initrd /boot/initramfs-3.3.7-1.fc16.i686.img
    }
    menuentry 'Fedora release 16 (Verne) (on /dev/sdb11)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4.11-1.fc16.i686--d3086a54-8a55-4115-9950-6a14188add59' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos11'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos11 --hint-efi=hd1,msdos11 --hint-baremetal=ahci1,msdos11  d3086a54-8a55-4115-9950-6a14188add59
        else
          search --no-floppy --fs-uuid --set=root d3086a54-8a55-4115-9950-6a14188add59
        fi
        linux /boot/vmlinuz-3.4.11-1.fc16.i686 root=/dev/sdb11
        initrd /boot/initramfs-3.4.11-1.fc16.i686.img
    }
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
    else
      search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
    fi
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-10-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-10-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-10-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-10-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-10-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-10-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-10-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-10-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-9-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-9-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-9-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-9-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-9-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-9-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-9-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-9-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-7-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-7-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-7-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-7-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-7-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-7-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.5.0-7-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-7-generic
    }
    menuentry 'Ubuntu, with Linux 3.4.0-1-generic-pae (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4.0-1-generic-pae--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.4.0-1-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.4.0-1-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.4.0-1-generic-pae (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.4.0-1-generic-pae-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.4.0-1-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.4.0-1-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-29-generic-pae-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-29-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae--a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc' {
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos9 --hint-efi=hd1,msdos9 --hint-baremetal=ahci1,msdos9  a44f9715-e2a3-4422-88c1-29f171dfbddc
        else
          search --no-floppy --fs-uuid --set=root a44f9715-e2a3-4422-88c1-29f171dfbddc
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
}

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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc7 during installation
UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a56125dc-39c1-4126-b23f-4cca1545df41 none            swap    sw              0       0
# swap was on /dev/sdc10 during installation
UUID=428ccb00-b16b-4e09-9610-67ee7e0dce3a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 236.932579041 = 254.404419584  boot/grub/grub.cfg                             1
 229.681022644 = 246.618120192  boot/initrd.img-3.5.0-17-generic               2
 232.641963959 = 249.797406720  boot/initrd.img-3.5.0-18-generic               1
 250.275459290 = 268.731228160  boot/vmlinuz-3.5.0-17-generic                  1
 228.706970215 = 245.572239360  boot/vmlinuz-3.5.0-18-generic                  1
 232.641963959 = 249.797406720  initrd.img                                     1
 228.706970215 = 245.572239360  vmlinuz                                        1
 228.706970215 = 245.572239360  vmlinuz.old                                    1

=========================== sdb9/boot/grub/grub.cfg: ===========================

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

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd2,msdos9'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
else
  search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-66396b0d-5815-45ff-ad09-11c9d7002e95' {
recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
    else
      search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    fi
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-66396b0d-5815-45ff-ad09-11c9d7002e95' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-66396b0d-5815-45ff-ad09-11c9d7002e95' {
    recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
        else
          search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-66396b0d-5815-45ff-ad09-11c9d7002e95' {
    recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos9'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
        else
          search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
        fi
        echo    'Loading Linux 3.5.0-17-generic ...'
        linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-17-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
    else
      search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    fi
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos9'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos9 --hint-efi=hd2,msdos9 --hint-baremetal=ahci2,msdos9  66396b0d-5815-45ff-ad09-11c9d7002e95
    else
      search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Ubuntu 11.04 (11.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
    else
      search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    fi
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
submenu 'Advanced options for Ubuntu 11.04 (11.04)' $menuentry_id_option 'osprober-gnulinux-advanced-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
    menuentry 'Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-13-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-3.0.0-13-generic
    }
    menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.0.0-13-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-3.0.0-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-16-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-16-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-16-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-16-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-16-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-16-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-15-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-15-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-15-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-15-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-15-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-14-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-14-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-14-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-14-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-14-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-13-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-13-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-13-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-13-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-8-generic--55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
        initrd /boot/initrd.img-2.6.38-8-generic
    }
    menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-2.6.38-8-generic-root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single-55fdd28d-6d87-462d-8f61-d31d45f57a1a' {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  55fdd28d-6d87-462d-8f61-d31d45f57a1a
        else
          search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
        fi
        linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
        initrd /boot/initrd.img-2.6.38-8-generic
    }
}

menuentry 'Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
    else
      search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    fi
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu 12.04.1 LTS (12.04)' $menuentry_id_option 'osprober-gnulinux-advanced-211934fe-e4d8-49aa-b623-9552dec61563' {
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-27-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-27-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-25-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-25-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-25-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-24-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-24-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae--211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
    menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.2.0-23-generic-pae-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  211934fe-e4d8-49aa-b623-9552dec61563
        else
          search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
        fi
        linux /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
        initrd /boot/initrd.img-3.2.0-23-generic-pae
    }
}

menuentry 'Ubuntu 12.10 (12.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    insmod part_msdos
    insmod ext2
    set root='hd2,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
    else
      search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    fi
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-18-generic
}
submenu 'Advanced options for Ubuntu 12.10 (12.10)' $menuentry_id_option 'osprober-gnulinux-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
    menuentry 'Ubuntu (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
    menuentry 'Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710' {
        insmod part_msdos
        insmod ext2
        set root='hd2,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos7 --hint-efi=hd2,msdos7 --hint-baremetal=ahci2,msdos7  8c2490f6-1e27-4508-b54c-8c2c58cfb710
        else
          search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
        fi
        linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
        initrd /boot/initrd.img-3.5.0-17-generic
    }
}

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

=============================== sdb9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc9 during installation
UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a56125dc-39c1-4126-b23f-4cca1545df41 none            swap    sw              0       0
# swap was on /dev/sdc10 during installation
UUID=9f2ad884-e537-4732-bc2b-29c71a04f13f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 172.890972137 = 185.640267776  boot/grub/grub.cfg                             1
 175.183952332 = 188.102336512  boot/initrd.img-3.5.0-17-generic               1
 174.877834320 = 187.773644800  boot/vmlinuz-3.5.0-17-generic                  1
 175.183952332 = 188.102336512  initrd.img                                     1
 180.885204315 = 194.224009216  initrd.img.old                                 3
 174.877834320 = 187.773644800  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1e 1c 20 ae be fa 1a 38  93 c2 47 2c 2b 97 7b e5  |.. ....8..G,+.{.|
00000010  6f 67 1b 04 51 08 8b 94  d6 c0 99 e7 27 0c cb c4  |og..Q.......'...|
00000020  70 52 30 c8 ee 33 aa 7f  4d c1 6d 15 fc d6 6e 22  |pR0..3..M.m...n"|
00000030  07 e4 ac cc a4 2d e9 cd  ed c8 50 8e a1 2f f2 93  |.....-....P../..|
00000040  6c ee b3 c5 09 79 85 29  25 e6 85 57 34 2d 88 1f  |l....y.)%..W4-..|
00000050  64 d8 6c 52 64 93 e4 ad  41 68 a8 60 84 4e 6b d9  |d.lRd...Ah.`.Nk.|
00000060  72 42 07 f6 30 7c 1a 39  9f 9d c8 69 d4 83 58 ad  |rB..0|.9...i..X.|
00000070  77 e4 49 f7 c8 a3 4d 75  67 fe 54 54 af 60 08 1a  |w.I...Mug.TT.`..|
00000080  d7 f9 1c e2 de 46 2a e3  21 ee 69 23 7c 9e 9b 5c  |.....F*.!.i#|..\|
00000090  c6 25 bf b0 d5 ce dc e0  6d 19 f3 53 0a 35 aa 9d  |.%......m..S.5..|
000000a0  53 d9 da 11 c1 52 53 a9  48 58 87 d3 cb 61 79 8d  |S....RS.HX...ay.|
000000b0  57 ea 57 3c eb 68 27 fe  55 2d 08 9b 29 d8 37 18  |W.W<.h'.U-..).7.|
000000c0  96 fb 0b cf c1 cb c7 a9  de d6 11 5e f8 d7 c4 bb  |...........^....|
000000d0  4d 7a 2f 0a 34 fe 21 d1  01 1e 34 81 ce c6 d9 d7  |Mz/.4.!...4.....|
000000e0  fa 9d 0b 5f 19 7f bb 59  17 84 88 58 5d 11 99 5d  |..._...Y...X]..]|
000000f0  80 02 e5 28 ff bc 0e 66  c6 26 91 d1 d6 39 63 7c  |...(...f.&...9c||
00000100  56 be 73 fc 31 e9 05 e5  e7 fd 0f 74 86 5c de f8  |V.s.1......t.\..|
00000110  91 3e bb d3 d5 17 5c 90  db d8 f0 7e 74 54 b3 30  |.>....\....~tT.0|
00000120  82 8e 2e fc 81 e4 1e 28  63 c6 e3 82 4d f1 a6 97  |.......(c...M...|
00000130  06 57 94 eb 6b 89 ab 0e  28 7e bd 06 24 d1 0a 8e  |.W..k...(~..$...|
00000140  a1 d2 62 dd fa 22 55 da  7a 3c e2 f8 05 a5 fe 64  |..b.."U.z<.....d|
00000150  a2 21 13 89 c6 59 27 b0  d4 89 ab f3 e0 de 3a 59  |.!...Y'.......:Y|
00000160  48 d5 c1 c5 0c 5a 63 41  29 53 78 49 c6 e4 dd ca  |H....ZcA)SxI....|
00000170  2c c1 d2 8e e7 22 96 68  b1 cf ef c9 05 8f 7f 1a  |,....".h........|
00000180  11 d0 82 26 e5 5f a9 4d  02 01 28 b1 20 ac a3 21  |...&._.M..(. ..!|
00000190  09 d1 67 a3 c3 ea 42 8b  61 03 00 f9 b8 ab 38 51  |..g...B.a.....8Q|
000001a0  13 e2 50 d3 97 99 76 0e  1a 17 71 8b c2 41 b0 98  |..P...v...q..A..|
000001b0  f7 94 19 a0 19 90 8b 54  df 41 b5 b0 4b eb 00 fe  |.......T.A..K...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 28 2d 0f 00 fe  |...........(-...|
000001d0  ff ff 05 fe ff ff f9 3f  3c 18 09 08 80 00 00 00  |.......?<.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt


```Here is the set up. sda is my internal hard drive (with Ubuntu 11.04 and Fedora 17) sdb is an external hard drive which can be booted off any computer.  Ubuntu 12.04 is in sdb1 and it controls grub.

I have also attached a screen shot from grub customizer, a truncated version of which is what shows up at the boot screen. These are the bottom lines of boot script output (e.g Ubuntu 12.04 in sdb7 and sdb 9 which no longer exists  and entries for sdc which is what the external drive is called when I booted from a live usb to install Ubuntu 12.10)

---

### Post by grahammechanical on 2012-10-29
You may be interested to know that the command sudo update-grub actually runs a script that in turn runs the command grub-mkconfig and all that does is update the grub.cfg script.

To get the updated script into the MBR you need to run

```
sudo grub-install /dev/sda
```

where sda is the first hard disk if you want grub in the MBR of the first hard disk.

Then when you reboot you will see a difference.

Regards.

---

### Post by ajgreeny on 2012-10-29
I am a bit muddled about the setup you have and what grub is booting the computer.

How is your BIOS set?  You say that the external disk is the one you usually boot of, ie sdb, and that ubuntu 12.04 grub is the one usually used by the machine.  Presumably it boots off sda if the external disk is not present, and then goes straight to 11.04.

Just to be certain that all the grub configuration is up to date everywhere I suggest you boot to each OS in turn and run ```
sudo update-grub
``` in the ubuntu OSs and ```
grub-mkconfig
```from a root terminal of fedora.  You also seem to have so many different kernels in each OS that I am completely baffled about what I am looking at.  I would therefore remove all the unwanted kernels from the OSs, ie all except the current latest kernel version and the previous kernel.  That is easy in ubuntu if you have synaptic installed; I'm not sure how easy in the software-center as I have never used it.  I also do not know how easy it is in fedora as I gave up on that distro quickly when I tried it.  Removing all but the latest kernels plus previous ones will make the grub.cfg files so much easier to read.

If that simplification and updating grub on all OSs does not solve the problem then I am really out of ideas and can only presume that grub on one or other of the OSs is broken in some way

---

### Post by monkeybrain2012 on 2012-10-29
> **grahammechanical said:**
> You may be interested to know that the command sudo update-grub actually runs a script that in turn runs the command grub-mkconfig and all that does is update the grub.cfg script.

To get the updated script into the MBR you need to run

```
sudo grub-install /dev/sda
```where sda is the first hard disk if you want grub in the MBR of the first hard disk.

Then when you reboot you will see a difference.

Regards.

Hi, I  just did what you say and run "sudo install-grub  /dev/sdb" and the output was "no error to report" . Reboot and it is still the same.

---

### Post by monkeybrain2012 on 2012-10-29
Hi, ajgreeny.

Here is my setup: I have an external hard drive (sdb)which has 3 oses at the moment : Ubuntu 12.04 in sdb1, Ubuntu 12.10 in sdb7 and sdb9 (one has a Nvidia driver so only boot on right machines and the other doesn't so boot anywhere) Ubuntu 12.04 in sdb1 control grub, this is  where I update-grub. The other partitions may house different OSes and sometimes I even repartition the drive.

sda is the internal drive of the host machine I happens to  be booting the external drive from at the moment and this machine happens to be a dual boot with Ubuntu 11.04 and Fedora 17 (I haven't a chance to upgrade 11.04 yet)  In this machine Ubuntu 11.04 controls grub. But what happens in sda is irrelevant because I can take the same external hard drive and boot it off a different machine, if I do that and run sudo update-grub in Ubuntu 12.04 (sdb1), then the boot menu would change to reflect the setup of the host machine, or at least it should until now. The problem right now is that the grub menu appears to contains the whole history of where this external drive has been and what it has contained instead of just the current state so the whole boot screen is cluttered up with  old information.

I can't boot into all the partition because I can't even find Ubuntu 12.10 is sdb7. The whole boot screen is full and I can't scroll down any further.

EDITED: If you look at the bootscript result towards the bottom, there is mention of sdc, but there is no sdc, sdc is the same as sdb, it is the same drive. It was labelled sdc when I boot from a live usb in the same machine and then attach this hard drive in order to install Uuntu 12.10 (so internal drive =sda,  live usb= sdb, external drive=sdc) Normally after such installation I reboot into the os that controls grub(12.04 in sdb1 in this case) and run sudo update-grub and only the new configuration would remain (so no sdc).

---

### Post by oldfred on 2012-10-29
I have installed a lot of Ubuntu, every version since 9.10 is still on my system. (I will houseclean soon.) But I had to give up on os-prober as it takes too long to run and adds entries I really do not want anymore. I just turn the os-prober off. If I happen to install something I do not know a boot-stanza for I might turn it one once.

I first try to maintain only two kernels in my main install. For Ubuntu (and Debian I think) there is a link to the most current kernel in /, so you can boot the link and always be booting the most current kernel without having to boot all your installs, updating grub, and then updating grub in main install.

Cavsfan has documented the procedure.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by monkeybrain2012 on 2012-10-29
Hi, oldfred,  

Thanks for the link, I will check it out later when I have the time. So you are saying os-prober is the culprit for the confusing boot screen and it is not really needed? I haven't had this problem until very recently, maybe there has been an upgrade in os-prober?

---

### Post by oldfred on 2012-10-29
The only way you get extra boot entries for other installs is with os-prober. And os-prober for most users is great. With old grub legacy we just about had to give users boot stanzas to boot anything more than XP.

But once you get multiple installs then you start to get too many entries and it is better just to manage it yourself.

To start you can just turn-off os-prober and copy & edit some entries from your current grub.cfg.

In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
#Copy & edit entries from this:
gedit /boot/grub/grub.cfg
#Copy them to and edit  titles:
gksudo gedit /etc/grub.d/40_custom
#Then do:
sudo update-grub

---

### Post by monkeybrain2012 on 2012-10-29
Hi, thanks for the reply. 

I am a little bit unclear about gediting grub.cfg

This is the output of sudo update-grub

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-25-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-25-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Ubuntu 12.10 (12.10) on /dev/sdb7
Found Ubuntu 12.10 (12.10) on /dev/sdb9
done
```In addition to sda1(11.04), sdb7 and sdb9 (12.10) I have 12.04 in sdb1 (from which I run update-grub) 

Here  is my grub.cfg
```
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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
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
menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.5.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.5.0-17-generic ...'
    linux    /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.5.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-27-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-25-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 211934fe-e4d8-49aa-b623-9552dec61563
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-3.0.0-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-16-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-16-generic
}
menuentry "Ubuntu, with Linux 2.6.38-16-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-16-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-16-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-15-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-15-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-15-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu, with Linux 2.6.38-14-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-14-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-14-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-13-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-13-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro quiet splash profile vt.handoff=7
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 55fdd28d-6d87-462d-8f61-d31d45f57a1a
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=55fdd28d-6d87-462d-8f61-d31d45f57a1a ro single
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-18-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset-a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-66396b0d-5815-45ff-ad09-11c9d7002e95 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04) (on /dev/sdc7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
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

```Where should I start editing and can you show me an example? It seems that it just lists the partitions and kernel but not the oses. 

Then what should I copy to /etc/grub.d/40_custom (or should it be 41_custom)?

Thanks again for the help.

---

### Post by monkeybrain2012 on 2012-10-29
Oh actually, can I leave os-prober on at the moment, then just erase all the oses in grub.cfg and starting with the line after "BEGIN  /etc/grub.d/30_os-prober" and update grub to re-generate the entries?  Now that the configuration is simple os-prober shouldn't be confused. After that I can turn it off to start afresh.

---

### Post by oldfred on 2012-10-29
You have to run sudo update-grub to regenerate grub.cfg. It is automatically regenerated on every kernel or grub software update, so any changes to it will not be saved. 

This is my 40_custom. Some are copies of  a full boot stanza but then adjusted to use link in /, so I do not have to specify exact kernel to use to boot. Windows entry is an exact copy from os-prober, but I should delete that as I do not boot Windows anymore. I have some odd chainload entries also. Even to my old grub legacy which I do not think can boot anything anymore. Some of the entries with nothing are just to put spaces in the menu. And I use grub2 to boot all my ISO directly and use a config file in my ISO folder on another drive.

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry " " {
set root= 
}

menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    insmod part_msdos
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

menuentry " " {
set root= 
}

menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

menuentry " " {
set root= 
}

menuentry 'Ubuntu 12.10, (on /dev/sdd4 from hd0' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root=(hd0,gpt4)
    linux /vmlinuz root=/dev/sdd4 ro quiet splash vt.handoff=7
    initrd /initrd
}

menuentry "Ubuntu 12.04, (on /dev/sdd3)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt3)'
    linux /vmlinuz root=/dev/sdd3 ro quiet splash vt.handoff=7
    initrd /initrd
}

menuentry " " {
set root= 
}

menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd3,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}

menuentry "Chainboot hd2" {
set root=(hd2)
chainloader +1
}


menuentry " " {
set root= 
}
menuentry "Chainboot hd1" {
set root=(hd1)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}


menuentry "Kubuntu, Natty 11.04 (on /dev/sdc14)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos14)'
    search --no-floppy --fs-uuid --set 5c703dd6-c2aa-4b09-a690-7d1cb88283a9
    linux /vmlinuz root=/dev/sdc14 ro quiet splash
    initrd /initrd.img
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

```

---

### Post by monkeybrain2012 on 2012-10-29
Hello,

My entries in grub.cfg are like 
```
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb9)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--a44f9715-e2a3-4422-88c1-29f171dfbddc (on /dev/sdb7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 8c2490f6-1e27-4508-b54c-8c2c58cfb710
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=a44f9715-e2a3-4422-88c1-29f171dfbddc ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}
```

How can I tell which Ubuntu is it?  (can be 12.04 or 12.10 because I have upgraded 12.04's kernel)

---

### Post by oldfred on 2012-10-29
Do you have separate /boot partitions? If not the UUIDs have to be the same, your are not.

You show a mix of sdb9 & sdb7 and a UUID that does not exisit??
a44f9715-e2a3-4422-88c1-29f171dfbddc

You have labeled two of your partitions, it does make it a bit easier to keep track if you label all of them with Disk Utility or gparted.

If this is your 12.10 on sdb9 Then try these:
```

menuentry "Ubuntu 12.10  (/dev/sdb9)"  {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}

menuentry "Ubuntu 12.10  (/dev/sdb9) partition boot"  {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    linux /vmlinuz root=/dev/sdb9 ro quiet splash $vt_handoff
    initrd /initrd.img
}


```
If drive does change from sdb to sdc or you boot from sdb from BIOS the hd1 has to be hd0 even if still sdb9 and if sdc then you have to change sdb to sdc. I have had to edit drive number (with e in grub menu) when using above type entry in flash drive where its number changes.

---

### Post by monkeybrain2012 on 2012-10-30
> **oldfred said:**
> Do you have separate /boot partitions? If not the UUIDs have to be the same, your are not.

You show a mix of sdb9 & sdb7 and a UUID that does not exisit??
a44f9715-e2a3-4422-88c1-29f171dfbddc

You have labeled two of your partitions, it does make it a bit easier to keep track if you label all of them with Disk Utility or gparted.

If this is your 12.10 on sdb9 Then try these:
```

menuentry "Ubuntu 12.10  (/dev/sdb9)"  {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
    linux /boot/vmlinuz-3.5.0-17-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.5.0-17-generic
}

menuentry "Ubuntu 12.10  (/dev/sdb9) partition boot"  {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos9)'
    linux /vmlinuz root=/dev/sdb9 ro quiet splash $vt_handoff
    initrd /initrd.img
}


```If drive does change from sdb to sdc or you boot from sdb from BIOS the hd1 has to be hd0 even if still sdb9 and if sdc then you have to change sdb to sdc. I have had to edit drive number (with e in grub menu) when using above type entry in flash drive where its number changes.

Hi, the attached picture is the layout of the hard drive. sdb9 is the small partition (~10G) after the swap. Ubuntu 12.04 in sdb1 (/ partition) and sdb5 (/home) and it controls grub.

sdb7 and sdb9 are only for testing and they have no separate /home, they used to be 12.04 but 12.04 has been erased and replaced by 12.10.  My problem is exactly that the boot menu doesn't get updated and still shows lines of these partition being 12.04. 

I am thinking of deleting all the lines for these no longer exist 12.04 in sdb7 and sdb9 (and for sure everything with sdc) from grup.cfg but I can't tell what OS is running for lines like the ones I posed on the last post. Kernel 3.5.0-18 is definitely 12.10 and those lines do show up, 3.5.0-17 can be either.

Is it ok if I erase them all and run update-grub for the system to discover the oses again?

---

### Post by oldfred on 2012-10-30
You can delete anything. But do not delete the partition that has grub in the MBR. Or boot into the install you want to boot and run this. 

sudo grub-install /dev/sda

Then after deleting partitions, you should be able to boot back into the same install and rerun the

sudo update-grub

Note that any old or defective entries from other installs grub.cfg get copied into your current install. Often you have to boot into all your other installs and run update grub there first so you main install then has current entries. Or why we prefer to boot with partition entries that always boot most current kernel.

You so have to use gparted from LiveCD or USB to be sure all partitions are unmounted. And you still may have to click on swap(s) and right click swap off as liveCD like to use swap to speed things up.

---

### Post by monkeybrain2012 on 2012-10-30
Hi,

There is only one partition that controls grub (sdb1 here), so are you saying I can delete everything else which is not sdb1 and then run sudo update-grub while in sdb1? Sorry, it is not clear if I need to reboot first to run update-grub, I would think that it is not necessary as long as sdb7 and sdb9 are mounted. 

There is a problem about updating grub in other partitions (sdb9 and sdb7) because I can't find them with the cluttered boot menu (more exactly I can't find the line for 12.10 in sdb7 on the boot screen, plenty of lines with sdb7 turn out to be non existent 12.04) and secondly when I installed these test oses I put grub in the partition (sdb7 rather than sdb) so sdb1 would always control grub (for example, if I get a kernel update in sdb7 I will reboot to sdb1 and update-grub so when reboot again the new kernel for sdb7 would show on the boot screen)  I am not sure I can even update grub in those oses.

Thanks again for your patience.

---

### Post by oldfred on 2012-10-30
You should be able to run sudo update-grub anytime. All it does is update grub's menu with new or remove deleted systems.

But with multiple systems you have to run it in secondary installs first, then reboot into primary boot install so it can then pick up the changes to secondary install. Again why booting partition and using manual entries is easier.

---

### Post by monkeybrain2012 on 2012-11-01
Hi, oldfred,

I am finally being able to log into all the partitions but I still cannot get rid of some superfluous entries.

I disabled os-prober and then purged it, update-grub in sdb1 (which controls grub). I checked that all entries in grub.cfg are gone except 12.04 in sdb1. I rebooted (only 12.04 in sdb1 is on the boot screen) and checked that grub.cfg is clean. 

I then reinstalled and re-enabled os-prober and update-grub. But then some of the entries for non-existent OS is back (12.04 in sdb7) on grub.cfgI rebooted into the partitions to update grub, boot into the sdb1 and update grub again but still can't get rid of the non existent 12.04 on sdb7.

This is the part of my current grub.cfg which involves sdb7

```
menuentry "Ubuntu (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-18-generic (recovery mode) (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-18-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
	initrd /boot/initrd.img-3.5.0-18-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu, with Linux 3.5.0-17-generic (recovery mode) (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic-root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset-8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=8c2490f6-1e27-4508-b54c-8c2c58cfb710 ro recovery nomodeset
	initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.04.1 LTS (12.04) (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-17-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-17-generic root=UUID=211934fe-e4d8-49aa-b623-9552dec61563 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-17-generic
}
menuentry "Ubuntu 12.10 (12.10) (on /dev/sdb7)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-/boot/vmlinuz-3.5.0-18-generic--8c2490f6-1e27-4508-b54c-8c2c58cfb710 (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos9)'
	search --no-floppy --fs-uuid --set=root 66396b0d-5815-45ff-ad09-11c9d7002e95
	linux /boot/vmlinuz-3.5.0-18-generic root=UUID=66396b0d-5815-45ff-ad09-11c9d7002e95 ro quiet splash $vt_handoff
	initrd /boot/initrd.img-3.5.0-18-generic
}
### END /etc/grub.d/30_os-prober ###
```

As you can see somehow 12.04 is still here, is this a bug in os-prober?

I am not sure why sdb7 and sdb9 shows up in the same line.

Boot screen used not to be so verbose and is a lot easier to read. Did they change something?

Thanks for the help/

---

### Post by oldfred on 2012-11-01
If the run of os-prober in your other installs have bad entries, they just get copied into your current install's os-prober. It looks for other grub.cfg and uses those entries.

Turn os-prober off. Create manual boot entries in 40_custom, one each for your two other installs. Then boot into them and run sudo update-grub.

---

### Post by monkeybrain2012 on 2012-11-10
Thanks oldfred for the patient help.

I did the following, still rather odd but I guess it is the best that I could do. :(

I disabled os-prober and delete everything in grub.cfg in my main partition (sdb1 with 12.04) Ran sudo update-grub and reboot and notice that all os information from boot screen is gone except for kernel versions, so I boot back into sdb1 (it is automatic if I just wait) and re-enable os-prober. I reboot into the other partitions (sdb7 and sdb9 both with 12.10), remove all entries in grub.cfg and update grub and reboot. Now the boot screen is more readable and I can find the proper partitions to boot into, but still there is some mention of 12.04 in sdb7 and sdb9 and it seems that the entries for 12.04 in sdb1 are displayed twice. 

I think they have changed something in grub or os-prober because I haven't seen before long and confusing lines such as this

```
Ubuntu 12.04.1 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option 'osprober-gnulinux-simple-211934fe-e4d8-49aa-b623-9552dec61563 (on /dev/sdb7)
```

Does it say 12.04 is on sdb7???

---

### Post by oldfred on 2012-11-10
I am also confused on what is where.

May be best to run a new copy of BootInfo report and post link.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

