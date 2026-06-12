---
title: "Grub help"
date: 2014-09-03
forum: New to Ubuntu
---

### Post by ymurti2 on 2014-09-03
I did some cleaning on my ubuntu 12.10 and now when I turn on my computer comes it :

GNU GRUB  version   1.99-21ubuntu3 

Minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions 

grub  _

---

### Post by yancek on 2014-09-03
That would indicate changes to your boot files.  Not knowing what "cleaning" you did it's difficult to do more than guess.  Since you can't boot Ubuntu, do you have any Linux Live CD/flash drive to use?  If you do, you can go to the site below and download and run the bootinfoscript which will output a results.txt file containing enough information so that someone should be able to advise you if you post it here.  There are instructions on its use in a link in the Description box on that page:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by ymurti2 on 2014-09-03
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    147011584 of the same hard drive for core.img. core.img is at this 
    location and looks for (,gpt2)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /grub/core.img

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /BOOT/bcd

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.5 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 2048.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdc has 
                       2471936 sectors.. But according to the info from the 
                       partition table, it has 2497024 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648

---

### Post by ymurti2 on 2014-09-03
GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,435,647       614,400 EFI System partition
/dev/sda3       1,435,648     1,697,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,697,792   145,057,791   143,360,000 Data partition (Windows/Linux)
/dev/sda5     589,490,176   625,141,759    35,651,584 Data partition (Windows/Linux)
/dev/sda6     145,057,792   147,010,917     1,953,126 Swap partition (Linux)
/dev/sda7     147,011,584   147,013,631         2,048 BIOS Boot partition
/dev/sda8     147,013,632   589,490,175   442,476,544 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1967 MB, 1967128576 bytes
256 heads, 63 sectors/track, 238 cylinders, total 3842048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     3,842,047     3,840,000   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9622704522702C7D                       ntfs       Recovery
/dev/sda2        D073-1A41                              vfat       ESP
/dev/sda4        9E4C77D74C77A8A3                       ntfs       Acer
/dev/sda5        E6DE7A99DE7A622B                       ntfs       Push Button Reset
/dev/sda6        ccccc6c4-93af-4817-9d46-9f18cec59a61   swap       
/dev/sda8        40674a06-97d4-4b7d-8732-16d686cbf099   ext4       
/dev/sdb1        7F61-13E4                              vfat       
/dev/sdc         DD13-363A                              vfat       
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/7F61-13E4         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdc         /media/DD13-363A         vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1

=========================== sda8/boot/grub/grub.cfg: ===========================

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

insmod part_gpt
insmod ext2
set root='(hd0,gpt8)'
search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
if

---

### Post by ymurti2 on 2014-09-03
search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt8)'
  search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
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
menuentry 'Ubuntu, with Linux 3.13.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
	linux	/boot/vmlinuz-3.13.0-35-generic root=UUID=40674a06-97d4-4b7d-8732-16d686cbf099 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.13.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
	echo	'Loading Linux 3.13.0-35-generic ...'
	linux	/boot/vmlinuz-3.13.0-35-generic root=UUID=40674a06-97d4-4b7d-8732-16d686cbf099 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.13.0-35-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt8)'
	search --no-floppy --fs-uuid --set=root 40674a06-97d4-4b7d-8732-16d686cbf099
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda5)" --class windows --class os {
	insmod part_gpt
	insmod ntfs
	set root='(hd0,gpt5)'
	search --no-floppy --fs-uuid --set=root E6DE7A99DE7A622B
	drivemap -s (hd0) ${root}
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
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

=============================== sda8/etc/fstab: ================================

-----------------

---

### Post by yancek on 2014-09-03
In your initial post, you neglected to mention that you had a windows system also, a significant omission.  That's why the bootinfoscript.  You have Ubuntu Grub installed in mbr mode with its boot files present and you also have thee Grub boot code in the master boot record and the correct files for it on sda8.  Unfortunately, you have GPT partition and EFI files for Ubuntu on sda2 so you are mixing the two boot methods, the result of which you have seen.  Since I don't use EFI/GPT partitiong I would just wait for someone familiar to post.

---

### Post by ymurti2 on 2014-09-03
Dear Yancek, sorry for not saying that I have Windows 7 and fortunatuly I am being able to boot on it. I am attaching the whole bootinfoscript because yesterday I was sending through my phone and I did know how to send the whole file. Thank you!

---

### Post by mörgæs on 2014-09-03
12.10 is unsupported. You will be better off with a fresh install of 14.04.1, which will also give you a new Grub in the process. 

Remember to choose 'something else' during install if you want to carry on with the dual boot.

---

### Post by yancek on 2014-09-03
Your bootinfoscript output shows you have 12.04 installed not 12.10.  Which is it?
The problem is you're mixing MBR and EFI.  You have a FAT32 EFI partition on sda2, you have a BIOS boot partition on sda7, you have Ubuntu on sda8 and several other windows partitions in addition to sda2, sda1 (windows boot?), as well as sda4 & 5.   You have an Ubuntu efi file on sda2 but no windows file and they are generally (always?) on the same partition.  

So are you now able to boot windows 7 but not Ubuntu?  I don't really know how to repair the mix of mbr and efi.  Someone else should come along with advice.

---

### Post by ymurti2 on 2014-09-04
> **yancek said:**
> Your bootinfoscript output shows you have 12.04 installed not 12.10.  Which is it?
The problem is you're mixing MBR and EFI.  You have a FAT32 EFI partition on sda2, you have a BIOS boot partition on sda7, you have Ubuntu on sda8 and several other windows partitions in addition to sda2, sda1 (windows boot?), as well as sda4 & 5.   You have an Ubuntu efi file on sda2 but no windows file and they are generally (always?) on the same partition.  

So are you now able to boot windows 7 but not Ubuntu?  I don't really know how to repair the mix of mbr and efi.  Someone else should come along with advice.

Dear Yancek, I have used a live CD of 12.04 but I am quite sure that I have 12.10 installed. Yes, I can boot Windows 7 but I cannot boot Ubuntu. Thank You for your help.

---

### Post by grahammechanical on 2014-09-04
If you are going to re-install and I think that you need to re-install to fix this problem, then please follow the advice in this wiki page

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[/FONT]
[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


Windows 7 is installed in EFI mode. So, must Ubuntu be installed in EFI mode.

It is my guess that you decide to clean out some of the old kernels and you cleaned out all the kernels.

Please also remember that Boot Repair will put a copy of the report on pastebin and provide a URL to the page of pastebin where the report is stored. All you need to do is give us the URL and then we can click on it and the report will open in another browser tag. It will make things easy for you and it will keep the thread neater and that makes it easier for us the understand the situation.

I do not wish to download even a text file on to my machine. So, I have not seen the second most important part of the Boot Repair report - What Boor Repair was recommending to fix this problem. It is at the bottom of the report.

Regards.

---

