---
title: "Sudo does not update?"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by Garland Fox on 2011-11-13
i run sudo grub-update.
it runs and adjusts entries as expected.
I reboot and nothing has changed.
Did I miss a step?

---

### Post by PaulW2U on 2011-11-13
Post deleted as the post I was answering was changed. :)

---

### Post by Cyclane on 2011-11-13
Paulw2u is correct

apt-get update is used to check if there are new updates
apt-get upgrade is used to actually upgrade

---

### Post by PaulW2U on 2011-11-13
> **Cyclane said:**
> Paulw2u is correct

apt-get update is used to check if there are new updates
apt-get upgrade is used to actually upgrade

No I wasn't - Garland Fox changed his post while I was replying. :)

@ Garland Fox - What were you expecting to happen? Why did you need to run update-grub? What did you expect to see changed?

---

### Post by Garland Fox on 2011-11-13
Sorry we got crossed up someway...
I need to update my GRUB file.
thanks

---

### Post by Garland Fox on 2011-11-13
Thanks for reply...
Wife's dual boot had crashed. After recovery grub has 6 linux entries that do not exist.
Just trying to clean those up.
Again - thanks.

---

### Post by Cyclane on 2011-11-13
Are you booting to the right HD from the BIOS. It seems you're updating a different grub.

---

### Post by Garland Fox on 2011-11-13
I only have one physical drive - I think you are correct - Grub is seeing a false installation partition.

I may try the grub customizer and see if I can work it out without doing any damage.

I don't yet feel comfortable editing the files in grub.d folder.

Thanks much

---

### Post by Cyclane on 2011-11-13
I saw one of the ubuntu forums staff members with a boot diagnostics script. Might be helpful now, but will have to find it.

---

### Post by westie457 on 2011-11-13
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) Download and usage instructions are here.

---

### Post by Cyclane on 2011-11-13
> **westie457 said:**
> [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) Download and usage instructions are here.

Thank you

---

### Post by Garland Fox on 2011-11-13
Many thanks - I will give that a trial run later when I can get back on her 'puter.

---

### Post by Garland Fox on 2011-11-13
Figured out maybe:
had 10.04 - updated to 10.10 - then updated to 11.04.
system crashed finishing up update to 11.04.
fdisk shows 3 generics of linux on sda5 with a swap disk on sda6.
THEN installed 11.10 that PROBABLY why fdisk showing the 11.10 generic on sda7 (swap on sda8).
Of course win 7 on sda1 and sda 2?
Sda3 is marked as extended partition.
Sda4 not noted.

---

### Post by Garland Fox on 2011-11-13
I wonder if there a good way to clean up everything off of sda5 and sda6 without having to reinstall this whole pie.

---

### Post by Garland Fox on 2011-11-14
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   374,469,624   374,469,562   7 NTFS / exFAT / HPFS
/dev/sda2         595,866,915   625,137,344    29,270,430   7 NTFS / exFAT / HPFS
/dev/sda3         374,470,654   595,865,599   221,394,946   5 Extended
/dev/sda5         374,470,656   486,940,834   112,470,179  83 Linux
/dev/sda6         586,782,720   595,865,599     9,082,880  82 Linux swap / Solaris
/dev/sda7         486,942,720   580,747,263    93,804,544  83 Linux
/dev/sda8         580,749,312   586,774,527     6,025,216  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        FC7EA3297EA2DBA0                       ntfs       HP
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE
/dev/sda5        f7871bc6-c2f0-4e6b-865f-98c259ea1e24   ext4       
/dev/sda6        05fda929-7d7d-40ee-b594-44df290f4e2f   swap       
/dev/sda7        18768f13-bf51-469c-a696-bf696d892a61   ext4       
/dev/sda8        56e23a39-494b-48b0-89dd-bf6ac5f277d7   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set default="6"
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.38-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    echo    'Loading Linux 2.6.38-12-generic ...'
    linux    /boot/vmlinuz-2.6.38-12-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    echo    'Loading Linux 2.6.35-30-generic ...'
    linux    /boot/vmlinuz-2.6.35-30-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-34-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    echo    'Loading Linux 2.6.32-34-generic ...'
    linux    /boot/vmlinuz-2.6.32-34-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-34-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root FC7EA3297EA2DBA0
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=05fda929-7d7d-40ee-b594-44df290f4e2f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.32-34-generic              2
               =                boot/initrd.img-2.6.35-30-generic              1
               =                boot/initrd.img-2.6.38-12-generic              2
               =                boot/vmlinuz-2.6.32-34-generic                 1
               =                boot/vmlinuz-2.6.35-30-generic                 1
               =                boot/vmlinuz-2.6.38-12-generic                 1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

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
set default="4"
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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=18768f13-bf51-469c-a696-bf696d892a61 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=18768f13-bf51-469c-a696-bf696d892a61 ro recovery nomodeset 
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root 18768f13-bf51-469c-a696-bf696d892a61
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root FC7EA3297EA2DBA0
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 949CA48C9CA46A86
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.38-12-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single
    initrd /boot/initrd.img-2.6.38-12-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.35-30-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.35-30-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single
    initrd /boot/initrd.img-2.6.35-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.32-34-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.32-34-generic
}
menuentry "Ubuntu, with Linux 2.6.32-34-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f7871bc6-c2f0-4e6b-865f-98c259ea1e24
    linux /boot/vmlinuz-2.6.32-34-generic root=UUID=f7871bc6-c2f0-4e6b-865f-98c259ea1e24 ro single
    initrd /boot/initrd.img-2.6.32-34-generic
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
# / was on /dev/sda7 during installation
UUID=18768f13-bf51-469c-a696-bf696d892a61 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=56e23a39-494b-48b0-89dd-bf6ac5f277d7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  a0 ff ff ff 30 00 30 00  30 00 30 00 37 00 36 00  |....0.0.0.0.7.6.|
00000010  30 00 31 00 63 00 30 00  65 00 35 00 37 00 61 00  |0.1.c.0.e.5.7.a.|
00000020  63 00 64 00 63 00 62 00  34 00 35 00 31 00 63 00  |c.d.c.b.4.5.1.c.|
00000030  39 00 64 00 65 00 63 00  33 00 37 00 66 00 66 00  |9.d.e.c.3.7.f.f.|
00000040  34 00 32 00 63 00 62 00  64 00 61 00 30 00 30 00  |4.2.c.b.d.a.0.0.|
00000050  30 00 30 00 66 00 66 00  66 00 66 00 00 00 00 00  |0.0.f.f.f.f.....|
00000060  e0 ff ff ff 76 6b 08 00  5a 00 00 00 80 ee 67 00  |....vk..Z.....g.|
00000070  03 00 00 00 01 00 00 00  41 65 46 69 6c 65 49 44  |........AeFileID|
00000080  a0 ff ff ff 30 00 30 00  30 00 30 00 32 00 64 00  |....0.0.0.0.2.d.|
00000090  33 00 32 00 36 00 37 00  39 00 34 00 37 00 61 00  |3.2.6.7.9.4.7.a.|
000000a0  38 00 62 00 64 00 65 00  62 00 61 00 64 00 36 00  |8.b.d.e.b.a.d.6.|
000000b0  62 00 31 00 31 00 35 00  62 00 39 00 38 00 62 00  |b.1.1.5.b.9.8.b.|
000000c0  33 00 61 00 64 00 31 00  64 00 35 00 37 00 38 00  |3.a.d.1.d.5.7.8.|
000000d0  30 00 64 00 34 00 38 00  34 00 35 00 00 00 00 00  |0.d.4.8.4.5.....|
000000e0  e0 ff ff ff 88 8b 66 00  a8 8c 66 00 f0 8c 66 00  |......f...f...f.|
000000f0  20 8d 66 00 68 8d 66 00  60 ee 67 00 00 ef 67 00  | .f.h.f.`.g...g.|
00000100  d8 ff ff ff 76 6b 0b 00  5a 00 00 00 28 ef 67 00  |....vk..Z...(.g.|
00000110  03 00 00 00 01 00 00 00  41 65 50 72 6f 67 72 61  |........AeProgra|
00000120  6d 49 44 00 00 00 00 00  a0 ff ff ff 30 00 30 00  |mID.........0.0.|
00000130  30 00 30 00 37 00 36 00  30 00 31 00 63 00 30 00  |0.0.7.6.0.1.c.0.|
00000140  65 00 35 00 37 00 61 00  63 00 64 00 63 00 62 00  |e.5.7.a.c.d.c.b.|
00000150  34 00 35 00 31 00 63 00  39 00 64 00 65 00 63 00  |4.5.1.c.9.d.e.c.|
00000160  33 00 37 00 66 00 66 00  34 00 32 00 63 00 62 00  |3.7.f.f.4.2.c.b.|
00000170  64 00 61 00 30 00 30 00  30 00 30 00 66 00 66 00  |d.a.0.0.0.0.f.f.|
00000180  66 00 66 00 00 00 00 00  e0 ff ff ff 76 6b 08 00  |f.f.........vk..|
00000190  5a 00 00 00 20 70 68 00  03 00 00 00 01 00 00 00  |Z... ph.........|
000001a0  41 65 46 69 6c 65 49 44  e0 ff ff ff 60 87 66 00  |AeFileID....`.f.|
000001b0  80 88 66 00 c8 88 66 00  f8 88 66 00 40 89 00 fe  |..f...f...f.@...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 a3 28 b4 06 00 fe  |...........(....|
000001d0  ff ff 05 fe ff ff 02 80  a7 0c 00 b8 8a 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

Maybe I did this correctly - Thanks
I don't understand this text as yet - but sure looks like install is bad?
Thanks for looking. I have to be away for now.

---

### Post by westie457 on 2011-11-14
> **Garland Fox said:**
> I wonder if there a good way to clean up everything off of sda5 and sda6 without having to reinstall this whole pie.

Hi there is a way, please explain clearly what you want and advice will be given to help you. Whatever your choices of action you want it is vital that you have a LiveCD/USB of which ever OS you want to keep. 
Another thing/s to have are backups of your Windows as well. It is never too early to make a backup and quite often far too late when things go wrong. A Windows Recovery Disc or better still is an Install disc.

Here is something to read about because you might have to do at least some of this. [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

let us know what you want and we will help.

Good luck.

---

### Post by Cyclane on 2011-11-14
Ok so there's Ubuntu with 2.6 kernel on /dev/sda5 and Ubuntu with a 3.0 kernel on /dev/sda7. Did I understand correctly that you wanna remove the install on /dev/sda5 as you are currently booting to /dev/sda7?

Well off course you can format this partition but the question you wanna ask yourself first, is there any data on the drive you'd like to safe.

I advise mounting it to look if you wan't to back up any files.
```
sudo mount /dev/sda5 /mnt
```
Now go to /mnt and all the files will be there.

---

### Post by Garland Fox on 2011-11-14
Good morning from here Cyclane- yes I would like to remove the installs from sda5- yes I boot from the sda7 where 11.10 Oneiric is installed.

---

### Post by Garland Fox on 2011-11-14
Thanks for the answer - will read up on all this -I have a live cd for the 11.10 Oneiric I want to keep .I guess it is what you call a live cd- I downloaded the iso and burned it.(DVD)
On the windows 7 area - all I have is an update disk from hp to upgrade the computer from Vista which it was sold installed, to Windows 7. Should I remake another windows recovery disk. 
What does the recovery disk do that will help?
Thanks

---

### Post by Garland Fox on 2011-11-14
Backing up some data now - back in a little bit.
Thanks

---

### Post by Cyclane on 2011-11-14
westie457 is just suggesting you make proper backups before you play around with your OS'. Especially when you don't exactly know what you are doing, you can break your system. Although most of the time your errors are recoverable, sometimes it's easiest to just roll back to your backup.

If you bought your laptop from a big vendor like HP you probably got some software with your laptop that's focused on backing up your data. It will create a new set windows install CD's but this time with your personal data on it.

##EDIT:
Ohhh and before you delete/format anything, be sure to have a live USB Ubuntu ready in case something goes wrong.

---

### Post by Garland Fox on 2011-11-14
Have to return to this later - Having problems getting Brasero to burn my data.
Keeps ejecting dl disks as if they are bad.

---

### Post by Garland Fox on 2011-11-14
Should have data backup completed by am. Now 3 pm here.
Do we have to format sda 5 and or sda 6 or can the data just be erased?
It is already a linux partition.
If it is erased and or formatted does that release the space for linux to reuse?
If the space is wanted for windows partition - then it would have to be reformatted to NTFS, correct?
I think that covers my questions - except for the "how to" part.

Thanks so much for the help you are giving.

---

### Post by Cyclane on 2011-11-14
Deleting the partitions will do. After that you can create a new partition (or multiple partitions) and format them any way you want. If you want some extra drive space for windows you could format a partition with NTFS.

To do the above as a beginner you might want to boot to the live USB and use gparted (comes installed on the live USB). It has a nice GUI that should be easy to understand. If you need help with this, let us know.

---

### Post by Garland Fox on 2011-11-14
Have not used USB - only dvd live disk. What size thumb drive needed for that - or are you speaking of an external drive?
Thanks

---

### Post by westie457 on 2011-11-14
Size of USB stick for Live is 1GB minimum upto 4GB maximum. Anything over 8GB and you can do a full install to it. However that is not the main purpose of this thread so it can wait.

An idea for you to think about when you have free space on your hard drive. Make it into a DATA partition formatted as NTFS for storage of files. That way it can be read by Linux and Windows.

Will post more info when you have finished your back ups.

---

### Post by Garland Fox on 2011-11-14
That is a cool idea on the data partition - I will probably plan on doing that.

I will have to make sure the bios will boot from usb - I don't remember seeing it in there.

The hp desktop is only 2 years old so it should.

I have a 1gb usb drive handy - where u go to make it? Download a file?

I on 11.10 / win 7 dual boot.

Thanks

---

### Post by Miljet on 2011-11-14
Just so you understand -- you do NOT have to make a live USB. If you already have a Live CD, use that.

---

### Post by Garland Fox on 2011-11-14
OK I will just use the live CD.

---

### Post by Garland Fox on 2011-11-15
Cyclane - if you are monitoring this, I have decided to wait until I can pickup an external hard drive to back up the wife's computer before I attempt any more changes.

You have been a great help in all this but if I proceed before I am ready I know how it will end.

As of now both windows 7 and Oneiric 11.10 are stable and usable - so even if the install isn't clean and I have lost some disk space, I  can hold off for now.

Gotta study up on this gparted stuff - may play around with it on my old dell where I can't kill anything important.

Again - thanks much for all your help.

---

### Post by Garland Fox on 2011-11-15
Weird Question:
I HAVE a bad install.
2 partitions sda5 and sda7 both have grub files.
The older versions in sda5 I do not want but cannot uninstall because synaptic package manager looks at sda5 to remove the old files which I have done, but then boots with sda7, still showing the old linux versions.
My question:
If I erase all the data from sda5 partition and /or sda6, its swap partition; then will the grub in sda 7 update automatically or would anything along that line work.
Windows 7 in sda1 and 11.10 Oneiric in sda7 both booting stable.
HMMM?
   Don't feel bad telling me I don't have a clue type newbie

---

### Post by westie457 on 2011-11-15
> **Garland Fox said:**
> Weird Question:
I HAVE a bad install.
2 partitions sda5 and sda7 both have grub files.
The older versions in sda5 I do not want but cannot uninstall because synaptic package manager looks at sda5 to remove the old files which I have done, but then boots with sda7, still showing the old linux versions.
My question:
If I erase all the data from sda5 partition and /or sda6, its swap partition; then will the grub in sda 7 update automatically or would anything along that line work.
Windows 7 in sda1 and 11.10 Oneiric in sda7 both booting stable.
HMMM?
   Don't feel bad telling me I don't have a clue type newbie

Hi, boot up as normal which if everything you have said is true then you will be booting /sda7 (your 11.10 installation). Start Gparted if you have it installed, if not then install it through the Software Center. 
When Gparted is running look at the partitions listed in the window. You should have what looks like a key next to sda7 and you will also have one against sda6 and sda8. If you do not have a key next to sda7 **do not do anything ** to the partitions, instead take a screenshot of the Gparted window. The 'PrtSc' button should take the picture. Post it back here using the paperclip symbol to attach it to your post.

If the key is next to sda7 all is good. There should be one along side sda8 and sda6 which is also good.

Check and double check these next steps as one mistake will kill your system which we do not want to do. Feeling confident so far? Of course you are. Simple instructions from a simple person - me.

We will begin.

Still in the Gparted window. Unmount sda6 by right-clicking it and selecting unmount.
While that partition is highlighted select delete.
Do the same for sda5. There should now be a grey space on your hard drive where those partitions were. Actually they are still there until you click 'Apply' and agree to the message in the pop up that will appear. Until you agree to that message you can still cancel the changes.

When you agree to the final warning those partitions will be wiped freeing up the space they occupied.

Depending on what you want to use the free space for (storage or extend sda7 to cover the gap) is best done from a LiveCD Desktop.

You have now finished with Gparted however you now need to update Grub. Open a terminal Ctrl+Alt+t usually works. Type in and run ```
sudo update-grub
``` When that has finished everything should be okay.

One last reminder _**GET THE BACK UPS DONE FIRST**_.
Because of the dangers to your system these instructions are detailed and if you follow them carefully there should be no problems at all.

Do not rush anything and check every step before committing to anything.

Good luck and enjoy your Ubuntu experiences.

---

### Post by Cyclane on 2011-11-15
I just read up on the thread, I was little tied up at work.

What westie457 describes is installing gparted on the Ubuntu you are currently booting to. This way you won't need to boot to the live USB/CD. And another advantage you'll have is that the partition you're currently mounting to is locked, so you can't accidentally delete/format the wrong partition.

As for uses of the free space your generating. You could indeed format it to NTFS ,so you can easily use it with your Windows install and your Ubuntu install. You could also make your already existing partitions bigger. The last one will likely require you to boot to the live CD.

As for gparted, if you know a little stuff about partitions and formatting it's really easy to use. Most of the time you select a partition with your right mouse button and select what you want to do (for example 'delete').


P.S.
After playing around with your partitions there's a slight possibility you won't be able to boot to a OS. Your computer will boot to grub but grub will report an error. Don't be alarmed this is easily fixed with the live CD, just come here to the forum. (This could for example happen if you  forget to perform 'sudo update-grub' before rebooting)

---

### Post by Garland Fox on 2011-11-16
This is great stuff - will start studying it  thru as I wait on the External hard drive - I want a disk image first...haha.
Thanks again.

Westie & Cyclane thanks a bunch - workin' it thru..
Good morning all.

---

### Post by Garland Fox on 2011-11-16
I don't see the attachment here...
[ATTACH]207305[/ATTACH]


ok there it is

No Key next to sda6
All else looks like you said.
Symbol sda1 looks bad
sda1 and sda2 for windows 7

---

### Post by Cyclane on 2011-11-16
I believe if you want to read the error message bound to sda1 you can richt click it and select properties or something. You'll see the error message somewhere. It's probably nothing to worry about. Espacially because we're not doing anything to that partition at the moment.

Ok It's perfectly safe to delete sda5 and reformat it to any filesystem you want. The others might form a little problem. deleting and formatting sda5 will however clean up your grub menuscreen (DON'T FORGET TO RUN 'sudo update-grub'). So you can go ahead and do that.

---

### Post by westie457 on 2011-11-16
> **Garland Fox said:**
> I don't see the attachment here...
[ATTACH]207305[/ATTACH]


ok there it is

No Key next to sda6
All else looks like you said.
Symbol sda1 looks bad
sda1 and sda2 for windows 7

Hi that little symbol against sda1, your Windows partition is Gparted's way of letting you know there is a problem with it. Gparted will not allow you to do anything with sda1. The easiest way to cure that is to boot into Windows and allow an automatic run of CHKDSK. If CHKDSK does not run automatically you will have to force it. To do that open Windows Explorer, right click on the C:\ drive select Properties. In the window that opens select the Tools tab. Here you are looking for 'Error Checking', click on that and follow the prompts.

Hope this helps.

---

### Post by Garland Fox on 2011-11-16
OK I use gparted to DELETE sda5.
Do I have to create anything before I format that space to NTFS.
just delete sda5 - format to ntfs - exit then update grub in terminal - thats all?

So the deleted space is still "sda5"
When I format it to NTFS - then it will not extend any other partition
I got it I think.

Only terminal command I need to run is sudo update-grub, correct?

Then reboot.
Thanks much for the info.

---

### Post by Cyclane on 2011-11-16
correct.

You could extend other partitions but don't do this while you're booting to your HD. Do this when booting from a live CD/USB (gparted protects you from this by locking the partition in other words, the key symbol next to the partition).

---

### Post by Garland Fox on 2011-11-16
OK we gonna try and c what happens - If it blows up wife will do me in and you won't have to listen to me whine anymore.

---

### Post by Garland Fox on 2011-11-16
gparted will not let me unmount sda5 or sda6 - it says unmount higher numbered partitions first.
It says those cannot be unmounted from "the" mount point.
The only thing it seems it might do is to reformat sda5 to ntfs.
I selected that but did not try it .
Ideas?

What if: I use gparted to simply reformat sda5 to NTFS?
If it would do that - would that work or does it have to be deleted first?

---

### Post by westie457 on 2011-11-17
Reformat sda5 to NTFS that should work. Unmount [s]and delete[/s] sda8 and sda6 - your swap partitions - you only need one so delete sda6 if allowed. If not then delete sda8. Do not forget to update Grub afterwards.

---

### Post by Cyclane on 2011-11-17
Silly me, when you just want to reuse the same partition and format it as NTFS, there's no need to delete the partition.

So yes go to gparted and format sda5 to NTFS.
Unlike the previous poster I don't advise to do any work on the other partitions until you know what to do with them. Because I don't think its likely that you will use one of them as a partition.

Its possible to extend your partitions but in your situation you'll have to boot to the live CD. Because you'll need to get work done to the partition you're working on.

---

### Post by Garland Fox on 2011-11-17
Good morning all - we havin fun any how.
Cyclane - What means "go to hosted"
Did I skip over something in gparted?
Thanks...

---

### Post by Paqman on 2011-11-17
> **Garland Fox said:**
> 
Cyclane - What means "go to hosted"


I suspect his spellchecker has decided "gparted" is actually spelled "hosted".

---

### Post by Cyclane on 2011-11-17
> **Paqman said:**
> I suspect his spellchecker has decided "gparted" is actually spelled "hosted".

Correct I'm on my mobile and it seems Swype corrected me. I edited my post for later use.

---

### Post by Garland Fox on 2011-11-17
ok thanks - doesn't bother me at all - i have to reread and retype half of what i poke in. haha

---

### Post by Cyclane on 2011-11-17
Huh? you only need to launch gparted right click sda5 and choose format.

---

### Post by Garland Fox on 2011-11-17
I was only commenting on my typing skills -zero zilch nada

---

### Post by Garland Fox on 2011-11-17
You the REAL Numero Uno.
We running boot tests now -- looks ok.
All I did was reformat sda5 to NTFS.
I did nothing yet  to the other swap file sda6.
Then updated grub.
4 boots from 1 to the other win 7 and linux -- all ok
Great-GOODIE- Thanks a bunch.
Garland (&wife)
I stay out of doghouse and wife does not have to murderlate me!

---

### Post by Garland Fox on 2011-11-17
Westie457 thanks a bunch to you too-- problem fixed. as far as I need to go.

---

### Post by westie457 on 2011-11-17
Okay, glad it all worked for you and was not too stressful. Any questions in the future feel free to start a new thread. 

Could you mark this as 'Solved' please, using [COLOR="Red"]Thread Tools[/COLOR] at the top of the page.

Thank you and enjoy Ubuntuing.

---

