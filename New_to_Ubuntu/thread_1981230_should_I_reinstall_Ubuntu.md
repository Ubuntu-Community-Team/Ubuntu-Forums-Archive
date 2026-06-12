---
title: "should I reinstall Ubuntu?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by theflyingduck on 2012-05-16
So I'm super new to this whole Ubuntu thing. I've used Linux a little bit before, but only on the school computers. 
 
Yesterday, I installed Ubuntu 12.04 LTS as a traditional dual boot with my Windows 7, and I installed it from a USB flash drive. However, after installing, I encountered a lot of problems. Unless i had my USB flash drive plugged in, the computer would just boot from Windows 7 as though I had never installed Ubuntu. When the USB flash drive was plugged in, the grub menu would show up and I could choose which system to boot from. So I burned a DVD of a boot repair I found on Ubuntu (I believe it basically reinstalled Grub or something along those lines). Then that problem was fixed. 
 
Then I noticed that every time I ran my computer from the Ubuntu OS, within minutes (~15min) it would start heating up like crazy and sometimes the fan would go nuts as well. But this didn't happen when I used my Windows 7 OS. I had installed the 32bit because it was the "recommended" version, but I'm now wondering if that's what's causing some of the problems as my computer is a 64bit one. After having done more research, I now  think I should have installed the 64 bit instead of the 32bit.
 
My computer is a Sony VAIO model PCG-4121GL (it came out around feb2012, if that helps).
 
On top of all that, I did this bootinfoscript thing to check that I had actually done a traditional dual boot install and not from within windows (there was a bit of a lag when I used Ubuntu). When doing this, I noticed all these error messages at the end. 

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/bcd /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    43,911,167    43,909,120  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     43,911,168    44,115,967       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          44,115,968   575,174,567   531,058,600   7 NTFS / exFAT / HPFS
/dev/sda4         575,174,654   976,771,071   401,596,418   5 Extended
/dev/sda5         575,174,656   964,362,239   389,187,584  83 Linux
/dev/sda6         964,364,288   976,771,071    12,406,784  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E0844D30844D0B0C                       ntfs       Recovery
/dev/sda2        0298436A98435B75                       ntfs       System Reserved
/dev/sda3        B27E44B87E4476DF                       ntfs       
/dev/sda5        65ca3e8c-b959-4b57-a8ab-5bc8c9a36038   ext4       
/dev/sda6        ed6b74b3-09f2-4c2c-826d-74dcdb1997e8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=65ca3e8c-b959-4b57-a8ab-5bc8c9a36038 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=65ca3e8c-b959-4b57-a8ab-5bc8c9a36038 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65ca3e8c-b959-4b57-a8ab-5bc8c9a36038 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=65ca3e8c-b959-4b57-a8ab-5bc8c9a36038 ro recovery nomodeset 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 65ca3e8c-b959-4b57-a8ab-5bc8c9a36038
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root E0844D30844D0B0C
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 0298436A98435B75
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=65ca3e8c-b959-4b57-a8ab-5bc8c9a36038 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ed6b74b3-09f2-4c2c-826d-74dcdb1997e8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              2
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

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

```I'm worried that the version I have may have been corrupted or something. My internet connection was being wonky when I was downloading the ISO image for Ubuntu, and the download had stopped and resumed. I'm not sure if this had somehow messed up my Ubuntu file. 
 
Basically, I'm wondering if I should just reinstall Ubuntu, with a 64bit version. And from my understanding I can either "uninstall" Ubuntu or just install the 64bit Ubuntu over my 32bit version. Do I need to "uninstall" Ubuntu first? From my understanding, I basically delete the Linux partitions and then use Windows Recovery discs to fix the "MBR" problem. The problem with this is that I can't seem to figure out which ones are my Linux partitions. 
Or to install the 64bit version directly over my 32bit version, I pick the "something else" option when I go to install the 64bit version, and then carefully select my Linux partition (the already installed 32bit Ubuntu). However, once again, I have no idea how I'm supposed to know which one is my Linux partition much less "carefully select" it. 
 
Sorry for the long post, I'm just extremely confused at this point and I feel like I've read a million threads trying to see what's wrong with my Ubuntu or if I've somehow done something to mess it up. Thanks in advance!

sudo fdisk -l command:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b692b4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    43911167    21954560   27  Hidden NTFS WinRE
/dev/sda2   *    43911168    44115967      102400    7  HPFS/NTFS/exFAT
/dev/sda3        44115968   575174567   265529300    7  HPFS/NTFS/exFAT
/dev/sda4       575174654   976771071   200798209    5  Extended
/dev/sda5       575174656   964362239   194593792   83  Linux
/dev/sda6       964364288   976771071     6203392   82  Linux swap / Solaris

```The attached image is the Computer Management window from Windows7 showing my partitions.

---

### Post by rai4shu2 on 2012-05-16
I think you can safely delete the 100% free partitions and try again. Ubuntu doesn't really need uninstalling. In fact, you have lots of options you could explore if you don't mind getting a little technical.

---

### Post by theflyingduck on 2012-05-16
I had a hunch that those were the ones I had to delete as those were the file systems that weren't recognized by Windows. However, just to check, is it alright to delete the first 100% free partition? I was a little unsure as it said it was the "Recovery partition" and I was afraid that it was the recovery thing for my Windows7.

And for "if i wanted to get my technical", I simply wish to get everything resolved in the simplest way possible for me. Would removing Ubuntu and reinstalling it be my best bet or would "getting more technical" be the way to go?

---

### Post by grahammechanical on 2012-05-16
Do not be too quick to delete those Windows partitions. Find out what they are actually for before you remove them.

Ubuntu is installed on sda5. You do not need to uninstall Ubuntu or delete the sda5 partition. You re-install Ubuntu into sda5.

When you choose Install from the live USB and you will get to a screen where you are asked how you want Ubuntu to install.

Select the Do Something Else option.

You will be given a screen showing you all the hard disk partitions. Draw a copy of that screen for future reference.

Select sda5 and click Change. And at the next screen from the drop down menu select to use the partition as ext4

tick format and give the partition a mount point of /  and then continue with the rest of the installation.

These links might help

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[http://www.youtube.com/watch?v=qBCHsgry2RQ&noredirect=1]("http://www.youtube.com/watch?v=qBCHsgry2RQ&noredirect=1")

Regards.

---

### Post by theflyingduck on 2012-05-16
Thanks a lot graham! I'm going to try that and re-install Ubuntu over my existing one tomorrow or tonight if I don't get home too late. I'll update with how it goes =)

---

### Post by theflyingduck on 2012-05-19
Thanks a lot to both of you who replied! I've managed to install Ubuntu 64bit directly over my Ubuntu 32 bit.

My fan still continues to go crazy, but at the very least, it's not actually as hot as it was before. I'll have to look into why my fan is overworking when I run my computer from the Ubuntu OS.

---

### Post by phibxr on 2012-05-22
Are we talking about the CPU fan or the fan on your graphics processor?

Usually, you will need to install the drivers from the manufacturer of your GPU to get proper fan management.

---

