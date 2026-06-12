---
title: "Can't boot anymore."
date: 2012-01-09
forum: New to Ubuntu
---

### Post by elmejorcabron on 2012-01-09
Hi there, 

So I thought I'd give Ubuntu a go, but I managed to screw it up. I had changed some settings, so I decided to re-install. I didn't know how to do this properly, so I went and wiped the partition in windows, didn't I? Very clever. So now my pc won't even boot. I keep getting "Grub Rescue," and I've tried using unetbootin to run a windows recovery ISO from USB; it doesn't work. I've also tried super grub disc; doesn't work. I get two options: "Default," and "List Devices / Partitions." Neither option does anything when selected. Very pretty blue selection screen though. I figure my MBR needs fixed, but I can't get my PC into recovery mode to fix it! Anyway, I would love you forever if you would take the time to help. My setup:

Windows 7 x64, 
Was dual booting with Ubuntu 11.10.
PC is a custom build, and I *ahem* somehow don't have a legit Windows installation disc. 

Thanks a million.

---

### Post by Basher101 on 2012-01-09
bad juju for piracy.

but for your ubuntu install, see if you can get a Live CD running, then choose "Try Ubuntu" on the login screen and run Gparted. Make a screenshot from your partitions and post it here

regards

---

### Post by KdotJ on 2012-01-09
If you have wiped your Windows partition, are you hoping there is a chance you can rescue some of the files off of it? This of course could be a possibility... 

If not, you could just install Ubuntu again from the media you used before, after all you was doing a fresh install anyway. 

Then again, I don't know your configuration so you have not have wiped your Windows partition and files

---

### Post by wildmanne39 on 2012-01-09
Hi, this > PC is a custom build, and I *ahem* somehow don't have a legit Windows installation disc. can not be discussed here but someone can help with getting ubuntu going.
Thanks

---

### Post by varunendra on 2012-01-10
> **KdotJ said:**
> you could just install Ubuntu again from the media you used before, after all you was doing a fresh install anyway. 
+1

If having problems with this, boot into live mode using a live cd, download [boot info script]("http://bootinfoscript.sourceforge.net/"), extract and run it as explained on the linked page, and post the contents of your RESULT.txt file here.

---

### Post by elmejorcabron on 2012-01-10
First, thanks for your willingness to help. [IMG]http://i167.photobucket.com/albums/u158/smelldepitts/stuff/Screenshotat2012-01-10214012.png[/IMG]

[Basher101]("http://ubuntuforums.org/member.php?u=1377584"): Here you go. Before I checked the forum I tried to reinstall ubuntu, and I think it worked...although the partition that I wiped seems to be gone...? Windows should still be there. Varunendra:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 6 for .
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   976,768,064   976,768,002   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   781,678,312   781,678,250   7 NTFS / exFAT / HPFS
/dev/sdb2         781,678,590   976,771,071   195,092,482   5 Extended
/dev/sdb5         968,388,608   976,771,071     8,382,464  82 Linux swap / Solaris
/dev/sdb6         781,678,592   960,002,047   178,323,456  83 Linux
/dev/sdb7         960,004,096   968,382,463     8,378,368  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        00AB-D4C5                              vfat       HD-EU2
/dev/sdb1        68B4C0DEB4C0B03C                       ntfs       
/dev/sdb6        9fde7f86-417b-4ad0-b3f3-2c0d97afb039   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos6)'
  search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9fde7f86-417b-4ad0-b3f3-2c0d97afb039 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9fde7f86-417b-4ad0-b3f3-2c0d97afb039 ro recovery nomodeset 
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
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set=root 9fde7f86-417b-4ad0-b3f3-2c0d97afb039
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 68B4C0DEB4C0B03C
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=9fde7f86-417b-4ad0-b3f3-2c0d97afb039 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
#UUID=e55c3925-dc9b-4440-9bc4-84e4bd58ad8f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by Kniveau600s on 2012-01-10
use the Ubuntu Live CD/DVD and have it repair the partitions while it installs Ubuntu

---

### Post by varunendra on 2012-01-11
> **elmejorcabron said:**
> Before I checked the forum I tried to reinstall ubuntu, and I think it worked...although the partition that I wiped seems to be gone...? Windows should still be there.
What do you mean by "Windows **should** still be there"..? Are you still not able to boot Win7? Even though, with my very limited experience with the results of boot info script, a few things seem weird..:
                  > **elmejorcabron said:**
> ....
 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and[COLOR=Red][B] looks 
    in partition 6 for .[/B][/COLOR]
 => [noparse]Grub2 (v1.97-1.98)[/noparse] is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    [COLOR=Black]**looks in partition 5 for [COLOR=Red]/boot/burg[/COLOR].**[/COLOR]
....
..if you are able to boot into Ubuntu now, you should also be able to boot Win7 as its partition and files seem intact:
> **elmejorcabron said:**
> ....
sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

..as well as the existence of the option to boot Win7 in the grub menu-
> **elmejorcabron said:**
> ....
### BEGIN /etc/grub.d/30_os-prober ###
**menuentry "Windows 7 (loader) (on /dev/sdb1)"** ....

So if you don't see that option in the grub menu, you're probably booting from the wrong hard drive (although I don't understand how it can lead to boot Ubuntu then). If so, try changing hard drive order in the boot-priority list of your BIOS.

Additionally, when in Ubuntu, run the following command (although it doesn't seem to be required, but won't hurt):
```
sudo update-grub
```


**_PS_:**
Not related with the boot problems, but-

[LIST=1]
[*]For a 500GB partition, FAT32 is not a recommended file-system, to say the least. You should change it to NTFS (for using with windows and linux both), or ext4 (for use with linux only).
[*]You seem to have two adjacent swap partitions on sdb. Only one is sufficient, so the other one can be safely removed.
[*]The gparted screenshot you posted is not showing the drive we are interested in. If further help is required, please post the screenshot with **/dev/sdb** (with all those different partitions) showing in it, along with the details of what happens now when you try to boot Ubuntu/Win7.
[/LIST]

---

### Post by Lupajz on 2012-01-11
So why don't you boot from USB live download and install boot-repair software 

> 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair


Run the software and then choose automatic repair.

---

### Post by elmejorcabron on 2012-01-11
I managed to sort it! Hooray! I repaired my MBR from command on the win 7 repair disc. For some reason it worked, so I am now able to boot on both windows and linux. Winner. Thanks for your help!

---

