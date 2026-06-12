---
title: "Can't find repair option on my live cd"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by wsfield99 on 2011-09-23
Hi, 

I was trying to install ubuntu on an externally attached hard drive and in the process I messed up the boot sector on my machine (an ageless Panasonic Toughbook cf-48  I've been pulling my hair out trying to fix this and I keep seeing that when you boot from a live cd on of the options is supposed to be a repair option.  I'm not seeing this, at least on the disk I've got.  It seems my only options are to run without installing or to install.  I'm sure there are many wise ones out there who know the answer to my dilemma.  Much thanks in advance, Scott

---

### Post by sanderd17 on 2011-09-23
There is no option to repair it, but you can repair it by booting it in live mode (try ubuntu).

Now, an Ubuntu CD can only repair an Ubuntu mbr.

I assume you wanted Ubuntu on your external HDD, and that Ubuntu changed the mbr of the internal HDD. This makes you able to boot any OS you want when the external HDD is connected, but when the HDD isn't connected, you can't boot a thing.

Is this correct?

If this isn't correct, give us the output of the boot info script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) (follow each step, also the last one, carefully)

Now if you only want Windows when the external HDD isn't connected, you need to repair the mbr with a Windows installation CD.

---

### Post by wsfield99 on 2011-09-25
O.K.  I was able to make a new installation on my hard drive of Ubuntu as a dual boot.  This allows me the option of booting into my original install.  However, I'd much prefer to repair my install than have to do this.  It works even if the external hard drive is not attached.  Here are the results of the boot scrip run:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 10 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /etc/fstab

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    29,139,034    29,136,987  83 Linux
/dev/sda2          29,140,990    58,603,519    29,462,530   5 Extended
/dev/sda5          56,385,536    58,603,519     2,217,984  82 Linux swap / Solaris
/dev/sda6          55,521,280    56,371,199       849,920  82 Linux swap / Solaris
/dev/sda7          54,669,312    55,519,231       849,920  82 Linux swap / Solaris
/dev/sda8          37,650,432    53,839,871    16,189,440  83 Linux
/dev/sda9          53,841,920    54,667,263       825,344  82 Linux swap / Solaris
/dev/sda10         29,140,992    37,165,055     8,024,064  83 Linux
/dev/sda11         37,167,104    37,640,191       473,088  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        3536ac82-a5a0-42ec-96f3-4861cc4dff44   ext4       
/dev/sda10       812d83de-5957-45c1-a6ee-7062296f7824   ext4       
/dev/sda11       df6566ff-a4f6-441a-9816-b76a6ff24d80   swap       
/dev/sda5        ade580fc-d9ba-4813-a01e-7e744467efeb   swap       
/dev/sda6        3df3f39d-f492-4db4-9325-511ff20c8959   swap       
/dev/sda7        6ac38de8-de42-4180-b696-32bec6f2da56   swap       
/dev/sda8        d0678528-c1b3-476d-aaea-137c78865892   ext4       
/dev/sda9        6579be80-8a9b-4548-b360-d7c6c5d6b9b9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-32-generic ...'
    linux    /boot/vmlinuz-2.6.32-32-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-31-generic ...'
    linux    /boot/vmlinuz-2.6.32-31-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-30-generic ...'
    linux    /boot/vmlinuz-2.6.32-30-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 3a320d0b-67ee-4475-93c5-122f53c24bbd
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3a320d0b-67ee-4475-93c5-122f53c24bbd ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 3a320d0b-67ee-4475-93c5-122f53c24bbd
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3a320d0b-67ee-4475-93c5-122f53c24bbd ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ade580fc-d9ba-4813-a01e-7e744467efeb none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.115070343 = 1.197297664    boot/grub/core.img                             1
   9.385761261 = 10.077884416   boot/grub/grub.cfg                             1
   8.309570312 = 8.922333184    boot/initrd.img-2.6.32-21-generic              3
   1.821369171 = 1.955680256    boot/initrd.img-2.6.32-24-generic              1
   1.828800201 = 1.963659264    boot/initrd.img-2.6.32-25-generic              1
   1.880992889 = 2.019700736    boot/initrd.img-2.6.32-26-generic              3
   1.888423920 = 2.027679744    boot/initrd.img-2.6.32-27-generic              1
   1.629966736 = 1.750163456    boot/initrd.img-2.6.32-28-generic              3
   3.238876343 = 3.477716992    boot/initrd.img-2.6.32-29-generic              2
   1.691997528 = 1.816768512    boot/initrd.img-2.6.32-30-generic              3
   1.903388977 = 2.043748352    boot/initrd.img-2.6.32-31-generic              1
   1.258365631 = 1.351159808    boot/initrd.img-2.6.32-32-generic              2
   1.914070129 = 2.055217152    boot/initrd.img-2.6.32-33-generic              1
   1.680503845 = 1.804427264    boot/vmlinuz-2.6.32-21-generic                 3
   1.739154816 = 1.867403264    boot/vmlinuz-2.6.32-24-generic                 1
   1.781345367 = 1.912705024    boot/vmlinuz-2.6.32-25-generic                 1
   1.838317871 = 1.973878784    boot/vmlinuz-2.6.32-26-generic                 1
   1.842079163 = 1.977917440    boot/vmlinuz-2.6.32-27-generic                 1
   1.892189026 = 2.031722496    boot/vmlinuz-2.6.32-28-generic                 1
   1.720104218 = 1.846947840    boot/vmlinuz-2.6.32-29-generic                 1
   1.895957947 = 2.035769344    boot/vmlinuz-2.6.32-30-generic                 1
   1.848018646 = 1.984294912    boot/vmlinuz-2.6.32-31-generic                 1
   1.789566040 = 1.921531904    boot/vmlinuz-2.6.32-32-generic                 2
   1.863517761 = 2.000936960    boot/vmlinuz-2.6.32-33-generic                 1
   1.914070129 = 2.055217152    initrd.img                                     1
   1.258365631 = 1.351159808    initrd.img.old                                 2
   1.863517761 = 2.000936960    vmlinuz                                        1
   1.789566040 = 1.921531904    vmlinuz.old                                    2

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=d0678528-c1b3-476d-aaea-137c78865892 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=6579be80-8a9b-4548-b360-d7c6c5d6b9b9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  23.130706787 = 24.836407296   boot/vmlinuz-2.6.32-21-generic                 1
  23.130706787 = 24.836407296   vmlinuz                                        1

========================== sda10/boot/grub/grub.cfg: ===========================

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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
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
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=812d83de-5957-45c1-a6ee-7062296f7824 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=812d83de-5957-45c1-a6ee-7062296f7824 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set 812d83de-5957-45c1-a6ee-7062296f7824
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-33-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-33-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-33-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-32-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-32-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-31-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-30-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-30-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-30-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-29-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-29-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-29-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3536ac82-a5a0-42ec-96f3-4861cc4dff44
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=3536ac82-a5a0-42ec-96f3-4861cc4dff44 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sda8)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set d0678528-c1b3-476d-aaea-137c78865892
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda8
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=812d83de-5957-45c1-a6ee-7062296f7824 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda11 during installation
UUID=df6566ff-a4f6-441a-9816-b76a6ff24d80 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

  15.442935944 = 16.581726208   boot/grub/core.img                             1
  16.394329071 = 17.603276800   boot/grub/grub.cfg                             1
  15.831054688 = 16.998465536   boot/initrd.img-2.6.32-21-generic              3
  15.542766571 = 16.688918528   boot/vmlinuz-2.6.32-21-generic                 1
  15.831054688 = 16.998465536   initrd.img                                     3
  15.542766571 = 16.688918528   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  06 2f 2e f0 30 e9 58 90  0d 55 20 f8 a4 95 19 1f  |./..0.X..U .....|
00000010  fe ab ed f7 fb 3c 74 ba  80 6f 8b b8 10 42 00 92  |.....<t..o...B..|
00000020  01 9f 03 3d aa 85 82 58  94 25 89 43 f9 9e 08 6a  |...=...X.%.C...j|
00000030  87 ec a8 a3 a0 cd 7b e9  c1 2d 5c c9 47 57 cd 06  |......{..-\.GW..|
00000040  3e 03 bb 0c 30 18 7e 3b  34 98 78 d0 a9 a3 e6 b1  |>...0.~;4.x.....|
00000050  af ee 2f 40 9b a6 3f 11  85 0a bf a7 8b c7 96 41  |../@..?........A|
00000060  dc 39 d0 69 eb e0 50 c5  7e 9f 66 06 6e 4d 2e 56  |.9.i..P.~.f.nM.V|
00000070  cc 0e 89 fe 0c 07 c0 3a  d5 0a 81 9e 23 8a c6 62  |.......:....#..b|
00000080  25 7f 12 95 2b 96 5b 9c  30 25 fb c3 e1 f7 a6 4e  |%...+.[.0%.....N|
00000090  fb 84 6c 37 c3 e0 a2 82  5c 51 7f 47 ba 90 fc 3e  |..l7....\Q.G...>|
000000a0  98 62 56 ad 5c fd 03 16  f0 90 4b 03 df c1 df 29  |.bV.\.....K....)|
000000b0  1f 81 43 3c a4 4a 03 55  53 74 02 fd ff ab 53 75  |..C<.J.USt....Su|
000000c0  5e 97 60 cd 31 12 bc fb  2e a2 30 8b c0 b8 7c 5d  |^.`.1.....0...|]|
000000d0  42 0c f7 ec 05 1a a3 02  52 b0 0f 1f 7a 41 ed 51  |B.......R...zA.Q|
000000e0  fa 61 37 2e 9e 51 da 77  d6 79 5a a5 7e be 53 2f  |.a7..Q.w.yZ.~.S/|
000000f0  2b 87 c3 e1 ff ab 47 55  d5 72 03 18 0d 92 07 81  |+.....GU.r......|
00000100  fe ae 32 0a 0d 04 04 ad  15 45 1c b5 1a d5 10 c9  |..2......E......|
00000110  13 8f fb e0 80 ac b9 45  c6 1a 65 17 6d e3 c7 8c  |.......E..e.m...|
00000120  97 2d 6d 91 c3 36 52 2e  f2 ca 19 85 04 2b 83 ef  |.-m..6R......+..|
00000130  f8 18 14 be 56 a1 6a 7c  be 09 36 71 47 bf 06 7e  |....V.j|..6qG..~|
00000140  cc 39 30 f4 b4 f0 cd cb  e0 43 1f 0f e2 8c 1e 55  |.90......C.....U|
00000150  f4 f5 12 fc 5c a8 18 c8  42 f8 f8 e0 30 91 f6 59  |....\...B...0..Y|
00000160  c6 2b e1 f4 d9 7b 33 d3  fe 2f d3 fe 9f df 8e e3  |.+...{3../......|
00000170  a1 77 c1 bd cf 0f 47 94  0c 3e 0f d5 2b 06 60 14  |.w....G..>..+.`.|
00000180  73 4e a6 7f 81 ca 6c 49  05 06 83 1a ec 26 11 e7  |sN....lI.....&..|
00000190  7d 4f 26 13 d5 31 b7 43  ea 15 ab 96 68 ed c5 f4  |}O&..1.C....h...|
000001a0  bc 4a f8 89 8b 98 4c 2d  7e 58 cb a8 28 34 76 5d  |.J....L-~X..(4v]|
000001b0  c7 0f fe 5d 15 cd 2e 7f  d4 04 32 e1 13 84 00 fe  |...]......2.....|
000001c0  ff ff 82 fe ff ff 02 b8  9f 01 00 d8 21 00 00 fe  |............!...|
000001d0  ff ff 05 fe ff ff 82 85  92 01 80 fa 0c 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Thanks, Scott

---

### Post by oldfred on 2011-09-25
What needs repair. If it is just booting from sda1, and you can boot into it just reinstall its grub2 boot loader to the MBR of the internal drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If you have an external drive with Ubuntu you need to install its grub2 boot loader to the MBR of the external drive. That does not happen with auto installs as grub defaults to sda. If you use manual install then you get the choice on where to install grub2's boot loader.

If you run the sudo update-grub with the external installed it should also find that install and let you boot it. Then you can run the same commands as above but with sdb.

have you been using auto install? It looks like you have lots of swaps  and you really only need one. But you have to update fstab with the UUID  of the one you keep.

You may also want to houseclean out older kernels. We usually suggest keeping one older one just in case, but remove all the others.

Manual way or grub customizer:
Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by wsfield99 on 2011-09-27
Hi, Thank you very much it worked!:popcorn:

---

