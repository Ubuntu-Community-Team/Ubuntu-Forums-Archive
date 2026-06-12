---
title: "try(hd0,0) ext2"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by desyer on 2012-06-30
Good Day,

I have windows 7 ultimate installed, I went and downloaded the windows installer for Ubuntu from its website.
I successfully installed Ubuntu and restarted, upon restarting error popped up saying this  "try(hd0,0) ext2"

Why is that?
I installed following all the instructions and installed Ubuntu on my primary drive where windows is also installed.

I have 2 other drives attached as well, with an external drive as well with my computer.

I have searched the website and search engines but cannot find an answer.

---

### Post by bcbc on 2012-06-30
That means that your first partition contains an ext2/3/4 file system. Which usually happens if you install linux (not using the windows installer wubi). So it looks like you did a normal dual boot or somehow have an ext2/3/4 partition as well as a wubi install.

Regarding that message...
Is that all that happens? If so how long did you wait and which version of Wubi.exe did you install. Older releases (prior to 11.10 or 11.04) would hang up on ext3 or ext4 file systems, but the newest version should not.

---

### Post by desyer on 2012-06-30
True I did break my drive into smaller parts so that I could install Ubuntu from a disc, but that didn't work so I wiped the small parts of the disk and extended my main drive back to normal.

I downloaded wubi.exe from the website and installed the latest Ubuntu, seeing that it was yesterday.

What happens is I start my copmuter, wait and it shows me which OS I want to load, win7 works fine and loads, but selecting Ubuntu, all that happens is that it goes to a black screen and just shows me that error.

---

### Post by bcbc on 2012-06-30
Some people have reported having to wait a minute or two for it to boot. So it's best to wait a little.

However, grub4dos (Wubi uses that to boot) is thinking that partition /dev/sda1 (what it refers to as (hd0,0)) is an ext2/3/4 partition. And if you think you've gotten rid of those partitions then maybe it is confused (it's possible to have a file system that doesn't correspond to the partition type)... I could speculate further but I have no way of identifying the problem.

First off I'd say, if you can partition, then it's better to do a normal dual boot. Wubi isn't ideal for long term use. What went wrong when you tried that?

If you really want to solve the wubi issue then I'd recommend booting from an Ubuntu CD and downloading and running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). The instructions on that link are a little out of date... you have to extract the bootinfoscript file from an archive and then run it like this:
```
sudo bash bootinfoscript
```

When you post the RESULTS.txt file it generates that will make things clearer.

---

### Post by desyer on 2012-06-30
see attached results.

---

### Post by oldfred on 2012-06-30
I did not know there was a wubi version for quantal yet. That is bleeding edge so only if testing and knowledgeable on wubi should you be even trying that version.

With all the drives and the sizes of the drives I would definitely partition and install to a different drive.

You have a left over /boot partition in sda1. I do not normally suggest /boot partitions for standard desktops.

Your sdb drive somehow was convert to SFS or dynamic partitions. Did you create partitions from Windows as that is what it does. Use Windows to shrink a NTFS partition, but use gparted to create partitions.

I would suggest unconverting the dynamic, but there is some risk so have good backups.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

When you have large drives like yours, you may want to consider this logic.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by bcbc on 2012-06-30
So this problem isn't supposed to happen anymore... might be a regression (wubildr hanging up on an ext4 partition). As *oldfred* mentions you have installed the development release so if that wasn't your intention then that's another bug.  If that's the case, boot Windows, go to the %TEMP% directory and copy the wubi-xx.xx-revxxx.log file so I can check what's going on.

To fix the ext4 problem, you can probably just delete and recreate it as NTFS from Windows. (Since partitioning always has a small risk, you should backup beforehand).

I copied the bootinfoscript result here to make it easier to read.
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid b09e2d98-862e-4f43-a9f0-3cc7e5700a9f root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Windows is installed in the MBR of /dev/sdc.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu quantal (development 
                       branch)
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       1820705616 sectors, but according to the info from 
                       fdisk, it has 1953523056 sectors.
    Operating System:  
    Boot files:        /wubildr

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
18 heads, 4 sectors/track, 6783294 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       206,847       204,800  83 Linux
/dev/sda2    *        206,848   488,391,215   488,184,368   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63 1,953,523,119 1,953,523,057  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048   976,768,064   976,766,017   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        cc4fc142-52f9-49db-822c-fc0f754d5e47   ext4       
/dev/sda2        F2E85DB8E85D7BB3                       ntfs       Alpha
/dev/sdb1        D81CF48F1CF46A40                       ntfs       Bravo
/dev/sdc1        D4A8780FA877EDFC                       ntfs       Chalie
/dev/sdd1        58DA24E5DA24C15C                       ntfs       Delta
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 7240bb22-7cf9-42b2-a161-225a68ce89c7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root cc4fc142-52f9-49db-822c-fc0f754d5e47
  set locale_dir=($root)/grub/locale
  set lang=en_NZ
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
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root cc4fc142-52f9-49db-822c-fc0f754d5e47
	linux	/vmlinuz-3.2.0-23-generic root=UUID=7240bb22-7cf9-42b2-a161-225a68ce89c7 ro   quiet splash $vt_handoff
	initrd	/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root cc4fc142-52f9-49db-822c-fc0f754d5e47
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/vmlinuz-3.2.0-23-generic root=UUID=7240bb22-7cf9-42b2-a161-225a68ce89c7 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root cc4fc142-52f9-49db-822c-fc0f754d5e47
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root cc4fc142-52f9-49db-822c-fc0f754d5e47
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root F2E85DB8E85D7BB3
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

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/core.img                                  1
               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    3
               =                vmlinuz-3.2.0-23-generic                       2

============================= sda2/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# UNCONFIGURED FSTAB FOR BASE SYSTEM
--------------------------------------------------------------------------------

================= sda2/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

               =                boot/initrd.img-3.5.0-2-generic               60
               =                boot/vmlinuz-3.5.0-2-generic                  21
               =                initrd.img                                    60
               =                vmlinuz                                       21
               =                vmlinuz.old                                   21

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
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

---

### Post by desyer on 2012-07-01
ok this is what I went and did, removed Ubuntu through windows Programs and Features.

Removed all drives except the primary and another drive. The second drive was dynamic so I converted it to normal drive.

Used the live CD to install Ubuntu off it, all went good and installed. Restarted the comp and it just took me to windows 7, like it skipped the part where it tells me what OS I want to use.

---

### Post by bcbc on 2012-07-01
You need to tell it where to install the bootloader (grub2). Whichever drive is booted first is the one whose bootloader will be selected. So e.g. if you're booting from /dev/sda with Windows' bootloader, but installed Ubuntu (and grub2) to /dev/sdb, then it won't be selected.

If you can select which drive to boot from BIOS when the computer boots, then perhaps you can just tell it to boot from the Ubuntu drive first (it will have detected Windows and so you can boot from either). Otherwise you'll have to install grub2 to the drive you boot from.

---

### Post by oldfred on 2012-07-01
With lots of drives it can be difficult to know what boot loader is in which drive. From BIOS or one time boot key you can change boot drive, but it helps to know what is installed where.

This script documents system and parses MBR so you know what is booting from where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

