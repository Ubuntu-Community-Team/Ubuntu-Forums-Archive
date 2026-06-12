---
title: "Sync folders between Linux distros?"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by HomesteadMommy on 2012-04-12
I have Ubuntu 11.10 (64 bit) on my laptop and love it, but since it only has 2 Gigs of memory when I do video or photo editing it really maxes out.  
I've installed Bodhi 1.4 (32 bit, dual boot) and it's much faster for my pc!  But I do like Ubuntu as well.  

Is there a way that I can sync the documents, photos and video folders between them?  I've tried some searches but the only topics I could find were on syncing the home folders.  It seems from these older threads that it's not a good idea to do this.
I would also like to sync Thunderbird mail between the two if I can.

My laptop does have 2 hard drives, so if the folders could be moved to the second hard drive and linked some how, would that work?

Thanks!

---

### Post by cortman on 2012-04-12
I would recommend making a new ext4 partition for data storage. It will be accessible to both Bodhi and Ubuntu, and you can keep all your files on it. When you set up Thunderbird on both OS's, just make sure you use the same storage folder on that partition.
If you're not sure how to create a new partition, let us know.

---

### Post by HomesteadMommy on 2012-04-12
> **cortman said:**
> I would recommend making a new ext4 partition for data storage. It will be accessible to both Bodhi and Ubuntu, and you can keep all your files on it. When you set up Thunderbird on both OS's, just make sure you use the same storage folder on that partition.
If you're not sure how to create a new partition, let us know.

Ok, how would that be different then just keeping my data files on my second hard drive?  I think my second drive is NTSF as my pc came with vista.  I've used it to back up my things to.  My first dh is ext4, I remember Ubuntu formated it that way when I took vista off.
Are you meaning make a new partition and have the home folder in it, and they share that 1 folder?  Sorry I'm a confused newbie! lol


I haven't done much partitioning before.  When I installed Bodhi today it asked me if I wanted to unmount the drives before installing, so I could resize/partition them.  I said yes, but then when I got to the partition section it would not let me make the Bodhi side larger then 18 gigs.  I don't know why as the disk had 80ish gigs of free space.  I could make it smaller but not larger then that. :confused:


Thunderbird is already set up in Ubuntu, I've been using it for a few months now.  I haven't set it up in Bodhi yet.  I'm guessing I would have to move what ever folder the Thunderbird in Ubuntu is using?

---

### Post by cortman on 2012-04-12
So your PC has two internal HDDs? In a one HDD situation it would just be 
a) shrinking your existing partitions enough to make sufficient continuous free space
b) creating a new partition out of the free space.

This partition would be accessible from all Linux operating systems on the computer.
Since you have two drives, you can create it on whichever one you want, whichever has the most space.

To give us an idea of your partitioning setup, please download and run [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") and post the full results.

---

### Post by HomesteadMommy on 2012-04-12
> **cortman said:**
> So your PC has two internal HDDs? In a one HDD situation it would just be 
a) shrinking your existing partitions enough to make sufficient continuous free space
b) creating a new partition out of the free space.

This partition would be accessible from all Linux operating systems on the computer.
Since you have two drives, you can create it on whichever one you want, whichever has the most space.

To give us an idea of your partitioning setup, please download and run [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") and post the full results.

Yes I have two internal hard drives.  The second one only  has 10 gigs free right now, there's more room on the first.  I'm ok with keeping a shared data partition on the first dh if it's easier and makes better use of the room.  Then back them up to the second hd.


  
```
                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
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
    Operating System:  Bodhi Linux 10.04.2
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sda7: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr


sdb2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048   195,053,508   195,051,461  83 Linux
/dev/sda2         195,053,566   234,440,703    39,387,138   5 Extended
/dev/sda5         230,268,928   234,440,703     4,171,776  82 Linux swap / Solaris
/dev/sda6         195,053,568   228,704,255    33,650,688  83 Linux
/dev/sda7         228,706,304   230,258,687     1,552,384  82 Linux swap / Solaris




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1                  63   139,899,731   139,899,669   7 NTFS / exFAT / HPFS
/dev/sdb2         139,900,926   156,301,311    16,400,386   5 Extended
Empty Partition.




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda1        31a636f0-32b8-4bdb-b78f-4b638be22e92   ext4       
/dev/sda5        f80ead03-07e4-4502-9b1a-d53d73a56595   swap       
/dev/sda6        39443f70-9742-426a-a68a-6ee27d95c8fb   ext4       
/dev/sda7        4ad16a3b-1558-475a-a76b-5eb527659dc1   swap       
/dev/sdb1        6060B44860B426A6                       ntfs       DATA


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sda1        /media/sda1              ext4       (rw)
/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)




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
search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
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
menuentry 'Ubuntu, with Linux 3.0.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-17-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    echo    'Loading Linux 3.0.0-17-generic ...'
    linux    /boot/vmlinuz-3.0.0-17-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    echo    'Loading Linux 3.0.0-16-generic ...'
    linux    /boot/vmlinuz-3.0.0-16-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
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
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 31a636f0-32b8-4bdb-b78f-4b638be22e92
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
UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=f80ead03-07e4-4502-9b1a-d53d73a56595 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


  68.419662476 = 73.465053184   boot/grub/core.img                             1
  86.185543060 = 92.541022208   boot/grub/grub.cfg                             1
  85.555664062 = 91.864694784   boot/initrd.img-3.0.0-12-generic               2
   1.510929108 = 1.622347776    boot/initrd.img-3.0.0-16-generic               2
  12.050231934 = 12.938838016   boot/initrd.img-3.0.0-17-generic               2
  66.133979797 = 71.010820096   boot/vmlinuz-3.0.0-12-generic                  1
   0.907688141 = 0.974622720    boot/vmlinuz-3.0.0-16-generic                  1
  19.442844391 = 20.876595200   boot/vmlinuz-3.0.0-17-generic                  2
  19.442844391 = 20.876595200   vmlinuz                                        2
   0.907688141 = 0.974622720    vmlinuz.old                                    1


=========================== sda6/boot/grub/grub.cfg: ===========================


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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
insmod png
if background_image /usr/share/backgrounds/grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
menuentry 'Bodhi Linux, with Linux 3.2.0-19-generic' --class bodhi --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
    linux    /boot/vmlinuz-3.2.0-19-generic root=UUID=39443f70-9742-426a-a68a-6ee27d95c8fb ro   splash quiet pcie_aspm=force
    initrd    /boot/initrd.img-3.2.0-19-generic
}
menuentry 'Bodhi Linux, with Linux 3.2.0-19-generic (recovery mode)' --class bodhi --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
    echo    'Loading Linux 3.2.0-19-generic ...'
    linux    /boot/vmlinuz-3.2.0-19-generic root=UUID=39443f70-9742-426a-a68a-6ee27d95c8fb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-19-generic
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 39443f70-9742-426a-a68a-6ee27d95c8fb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-17-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-17-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-17-generic
}
menuentry "Ubuntu, with Linux 3.0.0-17-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-17-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-17-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-16-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-16-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-16-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 31a636f0-32b8-4bdb-b78f-4b638be22e92
    linux /boot/vmlinuz-3.0.0-12-generic root=UUID=31a636f0-32b8-4bdb-b78f-4b638be22e92 ro recovery nomodeset
    initrd /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------


=============================== sda6/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=39443f70-9742-426a-a68a-6ee27d95c8fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4ad16a3b-1558-475a-a76b-5eb527659dc1 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sda6: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


  95.140842438 = 102.156701696  boot/grub/core.img                             1
 107.151630402 = 115.053187072  boot/grub/grub.cfg                             1
  93.282226562 = 100.161028096  boot/initrd.img-3.2.0-19-generic               2
  95.388290405 = 102.422396928  boot/vmlinuz-3.2.0-19-generic                  1
  93.282226562 = 100.161028096  initrd.img                                     2
  95.388290405 = 102.422396928  vmlinuz                                        1


======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda2


00000000  f2 be ed cd 7e a6 c4 78  c6 d1 88 d0 31 0d a8 11  |....~..x....1...|
00000010  5a 82 52 99 0c b1 2c a4  e0 29 12 24 0d 31 b4 c4  |Z.R...,..).$.1..|
00000020  e0 3d 75 db 3e 95 ab da  24 42 32 e8 21 25 33 4e  |.=u.>...$B2.!%3N|
00000030  ba 12 54 f2 9d df 7e 40  b2 5c 86 e4 24 f4 89 ef  |..T...~@.\..$...|
00000040  06 b5 87 cf a5 06 e5 36  b6 9d 05 e8 51 be 5c a2  |.......6....Q.\.|
00000050  de 56 de 3e 38 04 4b 36  15 f1 7b 2a 1c 3b 0d 3e  |.V.>8.K6..{*.;.>|
00000060  89 00 4d 39 18 f7 0b 84  0a 24 40 76 02 26 db 84  |..M9.....$@v.&..|
00000070  71 34 e6 c6 d3 a9 4d 3d  2b 3c af 9b 01 d0 28 a2  |q4....M=+<....(.|
00000080  11 c2 1d 12 02 17 12 05  18 44 fc 9a 27 25 ab 24  |.........D..'%.$|
00000090  35 a7 b0 1b 4c 27 20 be  8b 43 51 89 c3 2c b7 01  |5...L' ..CQ..,..|
000000a0  a7 40 07 3a 28 a3 92 e3  46 c1 e3 b7 39 13 f0 54  |.@.:(...F...9..T|
000000b0  59 28 86 a5 17 e8 12 4e  12 aa 2c 4e 16 16 22 3b  |Y(.....N..,N..";|
000000c0  c4 04 d4 19 8c c1 c0 c2  6b 4a fa f8 d9 9e 0a 67  |........kJ.....g|
000000d0  40 7b 0e dd 3e 9b 77 e3  9f 57 df 34 f6 0d fa 60  |@{..>.w..W.4...`|
000000e0  4f a0 33 d1 f3 1e e9 d8  f8 56 a0 e5 fc b7 07 c7  |O.3......V......|
000000f0  bb fc 00 d7 39 b5 2a d9  ea 8b 60 84 0f cb 5e b0  |....9.*...`...^.|
00000100  2d 07 a3 80 00 00 01 34  08 00 02 6b 05 82 cb 00  |-......4...k....|
00000110  00 00 00 af 01 21 6a cf  ff ff ff ff ff 9e 60 c0  |.....!j.......`.|
00000120  68 30 1a 13 06 c5 01 90  b0 60 2c 3a 0c 09 83 01  |h0.......`,:....|
00000130  62 40 d0 32 16 0c 05 02  c1 40 b0 50 2a 11 2a be  |b@.2.....@.P*.*.|
00000140  7a cd fd 7e 9c 5f 1a 5f  38 c9 ad db 58 67 1b eb  |z..~._._8...Xg..|
00000150  bb ca b9 7f f5 f3 a9 e4  77 ea c9 fe bd 47 d0 78  |........w....G.x|
00000160  59 46 bf 59 f1 2b 7d 7e  67 7f df fd a6 61 d6 e4  |YF.Y.+}~g....a..|
00000170  fb 7f 4b b1 97 fa d3 09  50 eb a3 77 9e 7d 2f ea  |..K.....P..w.}/.|
00000180  a7 9b f9 bc 22 06 4f 88  e9 3d c3 ae cd 56 46 47  |....".O..=...VFG|
00000190  91 66 67 4b 1d 9d 77 ea  a1 cc af 8a f0 fc 34 cc  |.fgK..w.......4.|
000001a0  93 d3 5f 44 b1 fa b5 67  d2 d9 a7 b4 95 e2 6f 0b  |.._D...g......o.|
000001b0  af e9 f5 96 6c ca d4 a4  e5 c7 64 82 c6 b2 00 fe  |....l.....d.....|
000001c0  ff ff 82 fe ff ff 02 58  19 02 00 a8 3f 00 00 fe  |.......X....?...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 78 01 02 00 00  |...........x....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


Unknown BootLoader on sdb2


00000000  74 0d 71 82 22 b3 10 77  60 0c d6 53 5c db ec 54  |t.q."..w`..S\..T|
00000010  77 3d 26 0b 74 bc 8f e6  38 e3 35 c2 f8 97 40 64  |w=&.t...8.5...@d|
00000020  8d ca ae 06 0e 00 fe 55  70 82 83 6e 2b 73 59 bd  |.......Up..n+sY.|
00000030  0f 22 b9 b1 91 5d c9 c0  38 c8 04 55 27 dc bf 20  |."...]..8..U'.. |
00000040  38 07 bf 6a 6d f7 30 45  8b 78 5b 81 bb 19 e8 6b  |8..jm.0E.x[....k|
00000050  d2 34 4b ac a0 5d c3 0a  46 68 e5 bd 8a 4e c4 ba  |.4K..]..Fh...N..|
00000060  d5 b1 d8 ee 39 07 9e 6b  cf 1b ce 56 fb ff 00 29  |....9..k...V...)|
00000070  cb 1c 53 96 8e de 40 db  6d b6 2c 2a 0b 26 dd c7  |..S...@.m.,*.&..|
00000080  07 bd 76 d6 b6 b9 55 1b  3e f7 3c 74 e6 a5 bb ee  |..v...U.>.<t....|
00000090  08 e8 34 bd 01 66 70 30  0b 1e c7 a5 76 93 fc 3e  |..4..fp0....v..>|
000000a0  57 84 33 28 39 5e 82 a1  38 c7 99 be ac b6 ae 8f  |W.3(9^..8.......|
000000b0  17 f1 1f 86 1a c6 52 c9  19 20 1e 48 ae 02 42 59  |......R.. .H..BY|
000000c0  dc 75 3d b7 56 9e eb d8  cc 8c b9 3d 54 03 9e 71  |.u=.V......=T..q|
000000d0  48 49 55 23 ae 79 c5 56  fd 00 48 f3 82 1b d3 3f  |HIU#.y.V..H....?|
000000e0  5a b0 55 80 c8 23 00 73  f9 52 b5 c4 42 c9 d3 e6  |Z.U..#.s.R..B...|
000000f0  00 91 c7 bd 43 8c 61 0f  1c 80 5b 14 5a c0 5b cc  |....C.a...[.Z.[.|
00000100  80 7f 09 c7 19 f5 a9 6d  a2 0f 22 ed 1c 93 c8 a3  |.......m..".....|
00000110  cc 0f 67 f0 b6 93 14 50  87 7c 96 1c e2 bd 02 67  |..g....P.|.....g|
00000120  5f 2c 05 18 38 e9 ed 58  49 45 b6 ed 7d 0e ba 71  |_,..8..XIE..}..q|
00000130  e5 d5 f6 39 09 2d d9 e5  24 ee ca 9e 06 69 f6 d2  |...9.-..$....i..|
00000140  5c ef 18 5c 0c f0 0d 47  3a 50 56 ea c1 d9 c8 dc  |\..\...G:PV.....|
00000150  52 c1 06 ee a2 ab 31 67  24 3f dd ce 41 15 9c d3  |R.....1g$?..A...|
00000160  7a 79 d8 13 d6 c8 71 02  24 26 43 b5 7a 03 df 15  |zy....q.$&C.z...|
00000170  42 4b c8 9d b0 8a 48 cf  00 d3 a7 19 59 ab ec 35  |BK....H.....Y..5|
00000180  7b f9 12 c9 0a 30 60 70  bc f2 2a 8b e9 d1 7d ec  |{....0`p..*...}.|
00000190  64 13 d2 b4 52 72 77 6b  a1 32 87 52 26 d3 59 9c  |d...Rrwk.2.R&.Y.|
000001a0  ab 2e c0 1f 19 07 d2 ba  76 97 cb 87 cb 87 20 11  |........v..... .|
000001b0  82 4f 5a a9 cd 36 af b9  11 56 16 33 22 e4 00 00  |.OZ..6...V.3"...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200







```

---

### Post by cortman on 2012-04-12
Hi,

This tells me that on your first hard drive (sda) you have five partitions:

sda1 = 93 GB - Ubuntu
sda2 = 18 GB (this one contains the following three)
sda5 = 2 GB
sda6 = 16 GB - Bodhi
sda7 = 758 MB

On the second hard drive

sdb1 = 67 GB MS Windows
sdb2 = 8 GB

You mentioned that you have some 80 GB free in the Ubuntu partition. If indeed you have a lot of free space, you should shrink the Ubuntu partition to within 15 GB of its current size.
To do this, boot into Bodhi and open gparted (open a terminal and type "gparted"). If GParted is not installed, install it by running

```
sudo apt-get install gparted
```

Find sda1 in the list of partitions in GParted. Right click and select "unmount". If the option is grayed out, that means it's already unmounted. Now select "Resize/Move". specify the new size of the Ubuntu partition.
Next, right click on sda7. Click "Delete". This is an unused swap partition. Both your Linux systems will share the same swap partition on sda5.
Now click Edit>Apply All Operations. When that's done, open a terminal and type

```
sudo fdisk -l
```

Post the output of this command so I can confirm it completed successfully. Then we'll move to creating a new partition.
Good luck!

---

### Post by HomesteadMommy on 2012-04-12
> **cortman said:**
> 
```
sudo fdisk -l
```Post the output of this command so I can confirm it completed successfully. Then we'll move to creating a new partition.
Good luck!

Thank you so much for your help!  I followed the steps and took sda1 down to 41 gb.  Ubuntu was using 25 gb on its own.


```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00076212


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5440    43692032   83  Linux
/dev/sda2           12142       14594    19693569    5  Extended
/dev/sda5           14334       14594     2085888   82  Linux swap / Solaris
/dev/sda6           12142       14237    16825344   83  Linux


Partition table entries are not in disk order


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b0a256d


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8709    69949834+   7  HPFS/NTFS
/dev/sdb2            8709        9730     8200193    5  Extended 

```

---

### Post by cortman on 2012-04-13
Always glad to help. :)

Now you want to resize your extended partition (sda2) to eat up all that free space between it and sda1. So open GParted, right click the partition, select resize/move, and resize it to include all the empty space. Do the same Edit>Apply all operations.
Now right click the "unallocated space" within sda2 and create a new partition. Under "filesystem" select ext4. Make the label say "data". Make this one use up all the unallocated space. Click Apply all operations.
Now you have the new partition. All that's left is to get it to mount as /data and you'll be ready to go!

---

### Post by oldfred on 2012-04-13
I use both a NTFS shared partition for data that I share with my old XP install and an ext3 data partition where most of my newer data goes. I now use XP very little, but still have my Firefox & Thunderbird profiles in the NTFS partition which I have used in XP and every install of Ubuntu. I also copy profiles to my laptop when traveling and back to desktop when I return.

If you do not have a Windows install, and you are keeping a NTFS partition get a Windows repairCD or find your XP install disk. Ubuntu runs fsck on its boot partition every 40 to 60 reboots and you really should run chkdsk on the NTFS partition regularly and you cannot do that from Ubuntu. Also NTFS does not support Linux ownership and permissions, so only use for data files. If not using Windows best to plan eventually  to convert to Linux partitions, but it requires full backup and restore.

Update to tb3 - also same profile editing for Firefox
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by HomesteadMommy on 2012-04-13
> **cortman said:**
> Always glad to help. :)

Now you want to resize your extended partition (sda2) to eat up all that free space between it and sda1. So open GParted, right click the partition, select resize/move, and resize it to include all the empty space. Do the same Edit>Apply all operations.
Now right click the "unallocated space" within sda2 and create a new partition. Under "filesystem" select ext4. Make the label say "data". Make this one use up all the unallocated space. Click Apply all operations.
Now you have the new partition. All that's left is to get it to mount as /data and you'll be ready to go!

Ok, GParted wouldn't let me add the extra space to sda2, but it would let me add it to the partition Bodhi was installed on, sda6.

The area that had the large unallocated space was in sda1, not sda2.  But I was able to set it up as "data".

Now do I need to just remember to save my data into that drive, or can Ubuntus documents, photos & vid folders be moved there and linked to easily?

How do I move my Thunderbird so it's synced between Ubuntu and Bodhi?  

Thanks!

---

### Post by HomesteadMommy on 2012-04-13
> **oldfred said:**
> I use both a NTFS shared partition for data that I share with my old XP install and an ext3 data partition where most of my newer data goes. I now use XP very little, but still have my Firefox & Thunderbird profiles in the NTFS partition which I have used in XP and every install of Ubuntu. I also copy profiles to my laptop when traveling and back to desktop when I return.

If you do not have a Windows install, and you are keeping a NTFS partition get a Windows repairCD or find your XP install disk. Ubuntu runs fsck on its boot partition every 40 to 60 reboots and you really should run chkdsk on the NTFS partition regularly and you cannot do that from Ubuntu. Also NTFS does not support Linux ownership and permissions, so only use for data files. If not using Windows best to plan eventually  to convert to Linux partitions, but it requires full backup and restore.


No I don't have Windows on my laptop anymore, I took it off a few weeks ago after trying Ubuntu out for a few months.
I didn't know I couldn't check the NTFS second drive in Linux though, thanks for the heads up on that.  I'll back the data off it and reformat is soon as I can.

I'll check out the links for Firefox and Thundbird, but I would like to sync them with out copying them each time I switch back and forth in Ubuntu/Bhodi.

---

### Post by HomesteadMommy on 2012-04-13
I found this on [sharing Thunderbird profiles between Windows and Linux]("http://web.archive.org/web/20050207141558/http://texturizer.net/thunderbird/share_mail.html"), I think you could use the same method for sharing between two Linux distros?

---

### Post by cortman on 2012-04-13
OK, so now you have a blank partition right after sda1?
I didn't realize you didn't have windows installed anymore; you still have the partitions on the second hard drive, so if there's nothing on there you want to save you would probably be better off using all that empty space there, rather than putting it all on one HDD.
You probably have enough GParted experience now to delete the old Windows partitions and create a new one. Just remember that HDD is called sdb, not sda. You can get to sdb by selecting it from the drop down menu in the upper right.
The Thunderbird issue is something I'm not real knowledgeable about. You'd probably do best to start a second thread on it.

---

### Post by oldfred on 2012-04-13
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

All you have to do is start Thunderbird, so it creates a new profile.ini and XXXXXX.default. The XXXXXX.default is your profile and if you copy the one you use to a shared partition then you can edit profile.ini to use the new location.

This is my edited profile.ini, you change the IsRelative and the Path to where you have saved it. In my case the /home/fred/shared is really a link to my shared NTFS partition and is not really in /home. And the mozilla is a folder at the top level of the shared partition where I have both my thunderbird and firefox profiles.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

```I do this all in a bash script. So I do not show sudo and edit fstab directly from script. I have a  note to myself to change from UUID to labels, so I can use same script in desktop & laptop, otherwise I currently have to remember to change UUIDs.

```
# windows shared NTFS
mkdir /mnt/shared
chown $USER:$USER /mnt/shared
chmod 777 /mnt/shared
# edit fstab to add mounts, UUIDs of data partitions do not change
cp /etc/fstab /etc/fstab.backup
#Edit fstab first Need to change from UUID to labels, so it works on both portable & DT

str5="# Entry for /dev/sdc2 :"
str6="UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g   defaults,uid=1000,nls=utf8,windows_names   0  0  "
fname=/etc/fstab

echo $str5 >> $fname
echo $str6 >> $fname

# link to /home
ln -s /mnt/shared
```

---

### Post by HomesteadMommy on 2012-04-13
> **HomesteadMommy said:**
> I found this on [sharing Thunderbird profiles between Windows and Linux]("http://web.archive.org/web/20050207141558/http://texturizer.net/thunderbird/share_mail.html"), I think you could use the same method for sharing between two Linux distros?

Cool it worked!  I copied the prefs.js to the new profile in Bodhi and edited the lines to point to the Thunderbird profile on Ubuntu.  They are reading each other nicely now.  Just love it when something works on the first try. lol
Now, maybe I should move it to the new "data" partition so I don't lose all my mail if I change anything in Ubuntu and forget that Bodhi is linked to it.

---

### Post by HomesteadMommy on 2012-04-13
> **oldfred said:**
> [http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

All you have to do is start Thunderbird, so it creates a new profile.ini and XXXXXX.default. The XXXXXX.default is your profile and if you copy the one you use to a shared partition then you can edit profile.ini to use the new location.


Thanks!  I'm still a bit confused though.  Do I copy the full profile folder to the shared data partition?  Then removed it from Ubuntu and add the links to the profile ini in both OS?

---

### Post by HomesteadMommy on 2012-04-13
> **cortman said:**
> OK, so now you have a blank partition right after sda1?
I didn't realize you didn't have windows installed anymore; you still have the partitions on the second hard drive, so if there's nothing on there you want to save you would probably be better off using all that empty space there, rather than putting it all on one HDD.
You probably have enough GParted experience now to delete the old Windows partitions and create a new one. Just remember that HDD is called sdb, not sda. You can get to sdb by selecting it from the drop down menu in the upper right.
The Thunderbird issue is something I'm not real knowledgeable about. You'd probably do best to start a second thread on it.

My second hard drive sdb, only has 10 or so gigs of free space right now.  It's full of my photos, docs and videos etc.  I kept a lot on it since when I was using vista = bloat my first hard drive would fill up fast.  You know I have software installed in Ubuntu that equals everything I used in vista AND a few programs in wine and it still uses way less room then everything in vista did.  Love that!
I would like to back everything off the second hd and format it for linux.  But I need to either move it to the first hd, or get more dvd's first.  An external drive is on my wish list to.

---

### Post by HomesteadMommy on 2012-04-13
Sorry for so many questions.  I'm trying to make a new folder in the new partition we set up.  It keeps telling me I don't have permissions to do so.  I've tried in Ubuntu and Bodhi. I tried to right click and changer permissions but it wont take any changes??

---

### Post by cortman on 2012-04-13
> **HomesteadMommy said:**
> My second hard drive sdb, only has 10 or so gigs of free space right now.  It's full of my photos, docs and videos etc.  I kept a lot on it since when I was using vista = bloat my first hard drive would fill up fast.  You know I have software installed in Ubuntu that equals everything I used in vista AND a few programs in wine and it still uses way less room then everything in vista did.  Love that!
I would like to back everything off the second hd and format it for linux.  But I need to either move it to the first hd, or get more dvd's first.  An external drive is on my wish list to.

OH, ok. I understand now. If you only have 10 GB free, it sounds as though everything that's on that drive won't fit on the new partition on sda.
If you don't have enough room to back up your second HDD to your first one, we're kind of stuck as far as that goes until you get some kind of external storage.
+1 to oldfred's Thunderbird instructions as well.

---

### Post by HomesteadMommy on 2012-04-13
> **HomesteadMommy said:**
> Sorry for so many questions.  I'm trying to make a new folder in the new partition we set up.  It keeps telling me I don't have permissions to do so.  I've tried in Ubuntu and Bodhi. I tried to right click and changer permissions but it wont take any changes??

Ok, kept digging until I found an answer I could understand. lol  Seems there are a few ways this can be done.  But so far this works.


```
sudo chmod -R +w <mount point>
```

---

### Post by cortman on 2012-04-13
> **HomesteadMommy said:**
> Ok, kept digging until I found an answer I could understand. lol  Seems there are a few ways this can be done.  But so far this works.


```
sudo chmod -R +w <mount point>
```

Sorry, I missed your question there. Are you satisfied with it as it is, or would you like to mount it somewhere more convenient?

---

### Post by HomesteadMommy on 2012-04-13
> **cortman said:**
> Sorry, I missed your question there. Are you satisfied with it as it is, or would you like to mount it somewhere more convenient?

Hmm, is there a better way?  I had it mount as /media/sda3


I was able to set up Thunderbird mail to sync thanks to you and Oldfred. :)  It took a bit of playing as Ubuntu reads the path as /media/data and Bohdi reads it as /media/sda3
Until I figured that out Thunderbird would open fine in Bohdi, but I kept getting a message in Ubuntu that Thunderbird was already running when I tried to open it.  Changing the profile ini to /media/data there fixed that.
I'm going to try it with firefox later to!

---

### Post by oldfred on 2012-04-13
I copy my entire profile the XXXX.default folder into my shared partition. I have both Firefox & Thunderbird in separate folders under Mozilla and then a profile folder in each also. I may not need the extra levels and not sure why I did it but am not changing now.

Another way to explain my setup.

/mnt/shared is really /dev/sdc2 by the mount in fstab.

And the link in /home makes /home/fred/shared really the same as my /mnt/shared.

Then in shared ( or really partition sdc2) I have these folders with the profiles copied into them
mozilla/firefox/profiles
mozilla/thunderbird/profiles

then I edit profile.ini in the regular .thunderbird hidden folder in /home to use new location for differnet profile than the one it created.
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default

Attached Nautilus view of above.

---

### Post by cortman on 2012-04-13
The way I was suggesting would only mount it one directory higher, in /. It may be marginally more convenient. If you're satisfied with it the way it is, go ahead and use it!
Just make sure Ubuntu and Bodhi automatically mount the partition at startup otherwise you'll have to mount it manually each time... info on that [here.]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by HomesteadMommy on 2012-04-16
> **cortman said:**
> The way I was suggesting would only mount it one directory higher, in /. It may be marginally more convenient. If you're satisfied with it the way it is, go ahead and use it!
Just make sure Ubuntu and Bodhi automatically mount the partition at startup otherwise you'll have to mount it manually each time... info on that [here.]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")


Sorry, I didn't get much time on the pc over the weekend.  But thanks to everyone's help I was able to get Thunderbird and Firefox synced to both distros. :D  No problems with either using the new data partition either!  Thank you!

---

### Post by cortman on 2012-04-16
> **HomesteadMommy said:**
> Sorry, I didn't get much time on the pc over the weekend.  But thanks to everyone's help I was able to get Thunderbird and Firefox synced to both distros. :D  No problems with either using the new data partition either!  Thank you!

Great! Always glad to help.
Mark the thread [SOLVED] using the thread tools in the upper right, if you would.

---

