---
title: "Ubuntu 11.10 and Windows 7 do not work together"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by corncobman on 2012-02-07
Hi there.

Before installing Ubuntu 11.10, I had 2 partitions in Windows, the second of which I split into 2, the second of which was used for the Ubuntu installation.

However once the Ubuntu installation completed, I could no longer boot into Windows 7, every time I chose the option, the computer would restart and bring me back to the Grub menu. However the recovery partition worked fine.

I have tried searching for a solution, I've tried using Boot Repair to rebuild the MBR , after which Windows 7 would boot properly but I would need to use the live CD to boot back into Ubuntu. After I reinstalled Grub, Windows 7 still would not boot when the option was chosen, and after this there was a flashing indicator in the top left corner but nothing else would happen and the only way to exit was to push the power button.

I've also run the boot_info_script the results of which I have pasted below:

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
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda8 
                       and looks at sector 592177760 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

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

/dev/sda1               2,048    33,589,247    33,587,200  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     33,589,248    33,998,847       409,600   7 NTFS / exFAT / HPFS
/dev/sda3          33,998,848   329,570,303   295,571,456   7 NTFS / exFAT / HPFS
/dev/sda4         329,570,366   625,141,759   295,571,394   f W95 Extended (LBA)
/dev/sda5         329,570,368   521,694,809   192,124,442   7 NTFS / exFAT / HPFS
/dev/sda6         521,694,873   570,778,765    49,083,893   7 NTFS / exFAT / HPFS
/dev/sda7         617,041,920   625,141,759     8,099,840  82 Linux swap / Solaris
/dev/sda8         570,779,648   608,937,983    38,158,336  83 Linux
/dev/sda9         608,940,032   617,039,871     8,099,840  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        581A73011A72DC06                       ntfs       WinRE
/dev/sda2        C4D460D3D460C8EE                       ntfs       
/dev/sda3        C4D460D3D460C8EE                       ntfs       
/dev/sda5        C4D460D3D460C8EE                       ntfs       
/dev/sda6        01CCE4D4657492C0                       ntfs       Ubuntu
/dev/sda7        ccca39bc-de25-4a25-a481-565f14082f3a   swap       
/dev/sda8        a20e18aa-b75f-49c7-86d5-52a1586c0255   ext4       
/dev/sda9        cdc89230-afba-4a11-948d-b3fcce0b3f18   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0)


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

insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
  set locale_dir=($root)/boot/grub/locale
  set lang=en_HK
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a20e18aa-b75f-49c7-86d5-52a1586c0255 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=a20e18aa-b75f-49c7-86d5-52a1586c0255 ro recovery nomodeset 
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
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root a20e18aa-b75f-49c7-86d5-52a1586c0255
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 581A73011A72DC06
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root C4D460D3D460C8EE
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a20e18aa-b75f-49c7-86d5-52a1586c0255 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=cdc89230-afba-4a11-948d-b3fcce0b3f18 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 284.429065704 = 305.403383808  boot/grub/core.img                             1
 275.040012360 = 295.321964544  boot/grub/grub.cfg                             1
 272.802837372 = 292.919816192  boot/initrd.img-3.0.0-12-generic               2
 280.653934479 = 301.349867520  boot/vmlinuz-3.0.0-12-generic                  1
 272.802837372 = 292.919816192  initrd.img                                     2
 280.653934479 = 301.349867520  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  46 49 4c 45 30 00 03 00  00 00 00 00 00 00 00 00  |FILE0...........|
00000010  0f 00 00 00 38 00 01 00  20 01 00 00 00 04 00 00  |....8... .......|
00000020  00 00 00 00 00 00 00 00  03 00 00 00 0f 00 00 00  |................|
00000030  01 00 00 00 00 00 00 00  10 00 00 00 48 00 00 00  |............H...|
00000040  00 00 18 00 00 00 00 00  30 00 00 00 18 00 00 00  |........0.......|
00000050  75 3f 67 60 02 51 c9 01  75 3f 67 60 02 51 c9 01  |u?g`.Q..u?g`.Q..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  50 00 00 00 80 00 00 00  00 00 18 00 00 00 02 00  |P...............|
00000090  64 00 00 00 18 00 00 00  01 00 04 80 48 00 00 00  |d...........H...|
000000a0  54 00 00 00 00 00 00 00  14 00 00 00 02 00 34 00  |T.............4.|
000000b0  02 00 00 00 00 00 14 00  9f 01 12 00 01 01 00 00  |................|
000000c0  00 00 00 05 12 00 00 00  00 00 18 00 9f 01 12 00  |................|
000000d0  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
000000e0  01 01 00 00 00 00 00 05  12 00 00 00 01 02 00 00  |................|
000000f0  00 00 00 05 20 00 00 00  20 02 00 00 00 00 00 00  |.... ... .......|
00000100  80 00 00 00 18 00 00 00  00 00 18 00 00 00 01 00  |................|
00000110  00 00 00 00 18 00 00 00  ff ff ff ff 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 1a 96 73 0b 00 fe  |............s...|
000001d0  ff ff 05 fe ff ff 1c 96  73 0b 34 f6 ec 02 00 00  |........s.4.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```I noticed that the entry for sda2 has Windows 7 listed but has /bootmgr /Boot/BCD which I'm not sure is correct.

I also saw that there were 2 swap partitions, but that doesn't really concern me for the time being.

Can anyone help me fix this problem? Thanks

---

### Post by Mark Phelps on 2012-02-07
From what you've said, I'm not sure you even HAVE a problem ...

It's not uncommon for the os_prober to find two installations of Win7 on a drive, especially when one is the new Windows boot partition.  That is because it looks for three things to detect MS Windows -- and those three things are spread now across two partitions.  Thus, it thinks you have two Win7 installs, when in fact, you only have one.

Also, it often gets the two reversed -- labeling the actual boot partition as Recovery, and vice-versa.

If you are able to boot into Win7 successfully, even if you have to select the "other" Win7 entry, then there is no real problem to be solved.

---

### Post by corncobman on 2012-02-07
The recovery partition doesn't let me start up Windows 7 proper, it just runs a recovery utility which gives a choice of either restoring a backup of windows, wiping the hard drive or scanning to fix problems.

---

### Post by Mark Phelps on 2012-02-08
OK ... so if, when you select the OTHER Win7 option, it doesn't boot all the way into the desktop, then the boot loader could be damaged.

Try the Boot-Repair stuff from the link below:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by hildenbrandsteven on 2012-02-08
The MBR repair for Windows will completely remove the Ubuntu option since M$ doesn't really recongize the need for Linux dual-booting. This is why you always need to install Ubuntu after Windows. Check out the link above, and also look up "grub repair," which is Ubuntu's default bootloader.

---

### Post by HiImTye on 2012-02-08
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)
> Boot into your Linux OS and deleted or rename the folder /boot on the  Windows system partition. Make sure that your don't delete the /Boot  folder. The /Boot folder contains the file "bcd" which is necessary to  boot Windows Vista/7

---

### Post by flemur13013 on 2012-02-08
I recently had similar hassles (from moving partitions around), and fixed it with this "[boot-repair]("https://sites.google.com/site/tipsandtricksforubuntu/system-tips/repairing-grub2")" program running from the liveCD; it's far better - so far! - than the typical ridiculous processes usually advised for fixing these boot problems.

Edit: use these links for boot-repair:
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

There's also this: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) which I haven't tried.

---

### Post by Mark Phelps on 2012-02-08
> **HiImTye said:**
> [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Personally, recommend strongly AGAINST doing this from inside Ubuntu.  Messing around with the Win7 OS boot partition, or the files, is asking for trouble -- as Win7 is very finicky about changes being made to its filesystem from "outside".

Safer way to do this would be to boot into SAFE mode and remove the files from the command line -- from inside Windows.

---

### Post by HiImTye on 2012-02-08
> **Mark Phelps said:**
> Personally, recommend strongly AGAINST doing this from inside Ubuntu.  Messing around with the Win7 OS boot partition, or the files, is asking for trouble -- as Win7 is very finicky about changes being made to its filesystem from "outside".

Safer way to do this would be to boot into SAFE mode and remove the files from the command line -- from inside Windows.
this would be difficult to do, as windows doesn't handle the directory tree using case sensitivity

and also, theyre unable to boot into windows

---

### Post by corncobman on 2012-02-09
I finally got the dual boot working well.  I rebuilt the MBR within Ubuntu using Boot Repair. Then I was able to boot into Windows and install a utility called EasyBCD which allowed me to edit the Windows boot sequence. I then added an entry for Ubuntu and then pointed it to Grub2 which was already installed on ext8.  I was then able to boot into Windows 7 without a problem, and when I chose Ubuntu from the boot menu, it displayed the Grub2 menu which was good, I was then able to boot Ubuntu and set the Grub2 menu timeout to 0 so that I could boot straight into Ubuntu.  BTW I did install Ubuntu after Windows 7 but the dual boot never worked properly for me in Grub2. Grub repair did nothing whatsoever. Maybe it was the recovery partition screwing everything up, dunno, but at least it's working now.

---

