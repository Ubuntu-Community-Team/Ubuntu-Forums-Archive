---
title: "Windows 7 not in grub boot menu after installing ubuntu"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Robertjdr on 2011-09-27
Hello everyone,

Yesterday I installed Ubuntu 10.xx (can't remember) from a cd onto my laptop. After installation, I upgraded Ubuntu to 11.xx (whatever is the current version). 
However, when I now reboot I am unable to get back into windows 7, which is what I was using previously. (I installed ubuntu to try it out and see if it is something for me). At first I did not see any boot menu at all, but luckily google told me to hold shift during booting, which worked but the menu did not show my windows 7. At least GRUB installed correctly (at least partly).
I did google here and there and I found out that it probably has something to do with my /boot/grub/grub.cfg file, that it does not hold my windows 7 information. And adding an entry for it would help and that I would have to use the boot_info_script to get some necessary information for it etc etc. When running that script, however, I get an error message:  (EDIT: got the boot script to work! see below this post!)

rjd@RJD:~/Desktop$ sh boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: Syntax error: "(" unexpected (expecting "fi")


So this is where I get stuck really.

Here is some more information about my laptop's setup:
I have a single hard drive in my laptop with 3 partitions. The first is the standard recovery partition, which I formatted and put on Ubuntu. The second one would be my c: drive in windows, on which windows was installed. The 3rd parition would be d:/ in windows, on which I just had important data.

Lastly (dunno if it is of any value), during the installation of Ubuntu 10.xx it had to restart my laptop as well, but then I never saw the boot menu either.

I really hope someone is able to help me out here. Thanks in advance.

Robert


EDIT: I did get the boot info script to work. The results are shown below (as I do not know how to attach a file to the post):
```


                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

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

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    30,716,279    30,714,232  83 Linux
/dev/sda2          30,716,280   274,904,279   244,188,000   7 NTFS / exFAT / HPFS
/dev/sda3         274,904,341   976,768,064   701,863,724   f W95 Extended (LBA)
/dev/sda5         274,904,343   976,768,064   701,863,722   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        a8d0503a-4224-47e8-9aba-645452738ba0   ext4       
/dev/sda2        0E3E7F0F3E7EEED9                       ntfs       
/dev/sda5        2A3E68FD3E68C403                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    echo    'Loading Linux 2.6.38-11-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a8d0503a-4224-47e8-9aba-645452738ba0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
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
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a8d0503a-4224-47e8-9aba-645452738ba0
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.179298401 = 8.782454784    boot/grub/core.img                             1
   2.292476654 = 2.461528064    boot/grub/grub.cfg                             1
   1.253379822 = 1.345806336    boot/initrd.img-2.6.35-22-generic              2
   1.927013397 = 2.069114880    boot/initrd.img-2.6.38-11-generic              1
   4.934810638 = 5.298712576    boot/initrd.img-2.6.38-11-generic-pae          1
   8.262077332 = 8.871337984    boot/vmlinuz-2.6.35-22-generic                 1
   1.204410553 = 1.293225984    boot/vmlinuz-2.6.38-11-generic                 1
   1.270938873 = 1.364660224    boot/vmlinuz-2.6.38-11-generic-pae             1
   4.934810638 = 5.298712576    initrd.img                                     1
   1.927013397 = 2.069114880    initrd.img.old                                 1
   1.270938873 = 1.364660224    vmlinuz                                        1
   1.204410553 = 1.293225984    vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  81 0e 00 00 ff ff ff 0f  83 0e 00 00 84 0e 00 00  |................|
00000010  85 0e 00 00 86 0e 00 00  87 0e 00 00 88 0e 00 00  |................|
00000020  89 0e 00 00 8a 0e 00 00  8b 0e 00 00 8c 0e 00 00  |................|
00000030  8d 0e 00 00 ff ff ff 0f  8f 0e 00 00 ff ff ff 0f  |................|
00000040  ff ff ff 0f ff ff ff 0f  ff ff ff 0f ff ff ff 0f  |................|
*
000001a0  ff ff ff 0f ff ff ff 0f  eb 0e 00 00 ec 0e 00 00  |................|
000001b0  ed 0e 00 00 ee 0e 00 00  ef 0e 00 00 f0 0e 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 2a 97 d5 29 00 00  |..........*..)..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

### Post by coffeecat on 2011-09-27
I've edited your post to add code tags. This is the best way of posting output like this - it's easier to read and preserves formatting. Here's a forum guide to BBCode which includes the use of code tags:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Mark Phelps on 2011-09-27
It reads like you installed Ubuntu using Wubi -- which would create a file on your NTFS partition containing Ubuntu.

Wubi does not use GRUB -- and forcing an install of it will only hose up your Win7 install.

Since you probably did NOT use the Win7 Backup feature to create and burn a Win7 Repair CD, you probably have nothing to repair your Win7 boot.  So, go to the link below, select the appropriate CD image, download it and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

BTW, you will have to PAY for the CD image -- which you could have done for FREE had you done this BEFORE you installed Ubuntu.

---

### Post by drs305 on 2011-09-27
I'm not a Windows guy and so haven't used these links, but forum member Despotism posted links to recovery CDs which supposedly are still legal and free. Here is his post:
[URL="http://ubuntuforums.org/showpost.php?p=11249721&postcount=439"]
http://ubuntuforums.org/showpost.php?p=11249721&postcount=439[/URL]

---

### Post by bcbc on 2011-09-27
It looks like you installed ubuntu over /dev/sda1 which probably contained your windows boot files (it also has the boot flag set, which windows uses to indentify the boot partition).

You said it was your recovery partition, but if that's true then it wouldn't have the boot flag. It's possible it was the boot and recovery partition I suppose. These are the files you are missing: /bootmgr /Boot/BCD

e.g. on my dell, my C: is separate from the boot partition.

---

### Post by Gregorybekkers on 2011-09-27
Windows 7 uses 2 partitions.
1st is a boot partition (kinda like /boot in linux)
2nd is the system drive mostly C (like / in linux)

if those 2 partitions still excist there is no problem,
Then you can try 'sudo update-grub' and grub will update the menu.

Else you have to find out what partitions are what path in /dev/sd*

and create the records in you grub.conf

---

### Post by garvinrick4 on 2011-09-27
Post 3,4 and 5 gave you links and or missing files to repair and or get a disk for your version, you just have to have one and put your
boot files back in place using link below (most likely easiest for you) and get Windows booting.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
After you put Windows boot files back (only a couple of commands)
then need to put grub2 back in place as to boot both Ubuntu and windows.
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Now go into Ubuntu and 
```
sudo update-grub
```as to put Windows in as menuentry and in config files for grub2 Ubuntu's boot loader.

## I do believe having removed the /boot partition for Windows and installing Ubuntu in its spot
is of question (will recovery disk from windows repair without /boot partition) All you can do is try.
With Windows boot files placed back in sda2 I do not see why not though (not a Windows guy). Hope it works out for you.
##bcbc is quite efficient and seems to believe replacing the 2 boot files looks to be enough to do the trick most likely will work just fine. Have a nice day.

---

