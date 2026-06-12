---
title: "sda2 hogging 283GB that I can't access?"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by VE6EFR on 2012-05-26
Hi, everyone.

This is my first thread here even though I come here every day to read and learn. Most of the time I can find an answer to my question in a previous post by doing a bit of searching first  however this time I am stumped. 

I am a relatively new Ubuntu user. My system is a dual boot Windows 7 and Ubuntu 12.04 LTS. I have windows on half of my 600 GB hard drive and Ubuntu on the other.

The problem that I am having was discovered when I tried to move some music files from Windows over to my music directory on Ubuntu. I was told that there isn't enough room. I found this to be a little odd so I looked at file systems using system monitor. It shows that on /dev/sda8 I only have 11.4 GB total and 4.2 GB free. This would explain why I was having trouble moving my music over.

So I then wanted to get a better picture of what may be going on. I ran gparted. If I am reading this correctly, windows is in /dev/sda1 which is 298.09 GB. I see /dev/sda2 has 283.58 GB, 4.64 GB being used. 

It seems a bit odd that the Ubuntu install would allocate such a large chunk of the hard drive to a partition that I can't really use. So I was thinking just decrease the size of sda2 and increase the size of sda8 where my data is being stored. So I booted using the live install disk. I am able to shrink the size of the sda2 partition no problem, however I can't increase the size of sda8 so I can add my music files. It is telling me that this partition is as large as it can get.

Am I missing something here? I have plenty of space available, but for some reason I can't seem to figure out how to make it work for me. Like I said, I am probably at the level of knowledge that can get me into trouble so I am very glad that I have all of you to learn from. So with that said, what am I doing wrong here? Please let me know what information that you need in order to try and help me figure out what's going on.

Thanks in advance,

Jeff

---

### Post by Bapun007 on 2012-05-26
In between sda2 and sda8 at least 4 other logical partitions are present , so you can't give the free space from sda2 to sda8 directly .

---

### Post by VE6EFR on 2012-05-26
So would I have to resize each of the partitions individually and work the open space by handing it off from one partition to the next and finally get to sda8?

---

### Post by Miljet on 2012-05-26
In order for someone to help, you are going to have to furnish more information like do you have a separate /home partition? What is on partitions sda3 through sda7? Posting a screenshot of GParted would help. Or the results of ```
sudo fdisk -l 
```

Or better yet, download the boot info script, run it, and post the results here.

At this point, anyone trying to help are just guessing at what you have.

Thanks

---

### Post by Bapun007 on 2012-05-26
> **VE6EFR said:**
> So would I have to resize each of the partitions individually and work the open space by handing it off from one partition to the next and finally get to sda8?
Yes , you have to do that  . But before doing that make a backup of your important data . 

And this process is also going to take some time  , so best of luck .

---

### Post by coffeecat on 2012-05-26
In addition to what Bapun007 said, there will be an extended partition, numbered either sda3 or sda4, which acts as a container for your logical partitions, sda5, sda6, sda7, sda8, plus any others you have. The best thing would be to post a screenshot of the Gparted window so that we can see what is going on. You can take a screenshot of an open window with Alt+PrintScr. There may be another way round your problem, but we need to see all the details of your partition layout.

---

### Post by VE6EFR on 2012-05-26
> **Miljet said:**
> In order for someone to help, you are going to have to furnish more information like do you have a separate /home partition? What is on partitions sda3 through sda7? Posting a screenshot of GParted would help. Or the results of ```
sudo fdisk -l 
```


Here is the info of sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000d5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   625133567   312565760    7  HPFS/NTFS/exFAT
/dev/sda2       625133568  1219835903   297351168   83  Linux
/dev/sda3      1221027838  1250258624    14615393+   5  Extended
/dev/sda5      1249905258  1250258624      176683+  82  Linux swap / Solaris
/dev/sda6      1245026304  1246973951      973824   83  Linux
/dev/sda7      1246976000  1249904639     1464320   83  Linux
/dev/sda8      1221027840  1245024255    11998208   83  Linux

Partition table entries are not in disk order

If this isn't enough information, let me know and I'll figure out how to get the other method you mentioned in your post.

Thanks again for the help.

---

### Post by Miljet on 2012-05-26
We now know that all of your partitions are Linux except sda1, which is Windows. We also know that sda3 is the extended partition that contains sda5, sda6, sda7, and sda8. What we don't know is which partition your Ubuntu is installed on. Nor do we know what is on the remaining partitions.

Try running the boot info script. I'm sorry that I forgot to include a link to it. It is here:  [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oldfred on 2012-05-26
What are sda6, 7 & 8? They all are smaller partitions with / (root) as the larger partition. 
I normally suggest if storing data in a separate /home or /data partition(s) that / be only 25GB as Linux does not need a lot for programs.

post this also to see use of mounted partitions. If sda6, 7 & 8 are not mounted by fstab, click on them first, so the get mounted.
Partition sizes

```
df -Th | sort
```

---

### Post by VE6EFR on 2012-05-26
> **coffeecat said:**
> In addition to what Bapun007 said, there will be an extended partition, numbered either sda3 or sda4, which acts as a container for your logical partitions, sda5, sda6, sda7, sda8, plus any others you have. The best thing would be to post a screenshot of the Gparted window so that we can see what is going on. You can take a screenshot of an open window with Alt+PrintScr. There may be another way round your problem, but we need to see all the details of your partition layout.

Sorry, I missed your post. Here's the image as an attachment.

I will look through the other replies and provide the other information that was requested.

---

### Post by VE6EFR on 2012-05-26
> **Miljet said:**
> We now know that all of your partitions are Linux except sda1, which is Windows. We also know that sda3 is the extended partition that contains sda5, sda6, sda7, and sda8. What we don't know is which partition your Ubuntu is installed on. Nor do we know what is on the remaining partitions.

Try running the boot info script. I'm sorry that I forgot to include a link to it. It is here:  [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I'm not sure why, but I can't seem to get the script to run. I extracted the script to my desktop and according to the directions I would open up terminal and run the following command

sudo bash ~/Desktop/boot_info_script.sh

I then get the following:

bash: /home/jeff/home/Desktop/boot_info_script.sh: No such file or directory

I have tried a few variations of the command trying to point it to the correct place but get pretty much the same results. I even tried to double click on the script and select Run In Terminal but that appears to fail as well.

Any ideas on what I am doing wrong?

---

### Post by coffeecat on 2012-05-26
There's an error in the instructions. The extracted script is named bootinfoscript. Move it to your desktop and run:

```
sudo bash ~/Desktop/bootinfoscript 
```

By the way, please post terminal output or the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by VE6EFR on 2012-05-26
That worked. Here are the results:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

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
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   625,133,567   625,131,520   7 NTFS / exFAT / HPFS
/dev/sda2         625,133,568 1,219,835,903   594,702,336  83 Linux
/dev/sda3       1,221,027,838 1,250,258,624    29,230,787   5 Extended
/dev/sda5       1,249,905,258 1,250,258,624       353,367  82 Linux swap / Solaris
/dev/sda6       1,245,026,304 1,246,973,951     1,947,648  83 Linux
/dev/sda7       1,246,976,000 1,249,904,639     2,928,640  83 Linux
/dev/sda8       1,221,027,840 1,245,024,255    23,996,416  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9C14E86314E8423E                       ntfs       Acer
/dev/sda2        a0762220-af97-4495-9cee-4de5fdfa40ec   ext4       
/dev/sda5        22549210-c1ca-4a8c-935b-526dd67517b6   swap       
/dev/sda6        6507aa98-93e9-4f42-a609-99d848ab8e28   ext4       
/dev/sda7        51a21c9d-c11f-41c6-8c9c-d578dd433117   ext4       
/dev/sda8        fc9ea4d8-64a5-4e74-8f79-5ab30164bd61   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda8        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=fc9ea4d8-64a5-4e74-8f79-5ab30164bd61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=fc9ea4d8-64a5-4e74-8f79-5ab30164bd61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=fc9ea4d8-64a5-4e74-8f79-5ab30164bd61 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=fc9ea4d8-64a5-4e74-8f79-5ab30164bd61 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root fc9ea4d8-64a5-4e74-8f79-5ab30164bd61
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 9C14E86314E8423E
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
UUID=fc9ea4d8-64a5-4e74-8f79-5ab30164bd61 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=22549210-c1ca-4a8c-935b-526dd67517b6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               1
               =                boot/initrd.img-3.2.0-24-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  2
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        2
               =                vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf 

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
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by Miljet on 2012-05-26
OK, we now know that Ubuntu is installed on sda8. You need to make sure that there is nothing useful on sda2, sda6, or sda7. You can do that by mounting each one and checking what is on them.

Assuming there is nothing there worth saving, you now have several options.
1. You can reinstall to sda2. Probably fastest unless you have done lots of customisation and/or installed lots of programs.

2. The Gparted screenshot shows that sda8 is the first partition in the extended partition. Therefore you can shrink (or eliminate) sda2, expand the extended partition (sda3), and finally expand sda8. The down side is that it is somewhat complicated and any time you expand a partition to the left, it takes forever since every file has to be rewritten. This would probably be my last choice.

3. You could also just delete sda5, sda6, and sda7 and expand sda8 into that space. That would also require you to recreate a swap partition. It will also renumber your partitions so you might have to make corrections to Grub and /etc/fstab.

---

### Post by VE6EFR on 2012-05-26
Looking at your suggestions, I elected to go for number 2 even though I really didn't have much on sda8 yet. I haven't done much with moving partitions and resizing them so I decided to give it a try and learn something in the process. The way I saw it, if I messed something up I would then have the ability to fall on your suggestion number 1 and just reinstall.

Everything went really well. It didn't take very long, probably less than 10 minutes total and now I have plenty of space to explore just what Ubuntu can do for me.

Thanks, Miljet and everyone that replied. It is great to know that there is a group of people that are willing to help when needed. I look forward to the day when I will be able to pay it forward and help someone new solve a problem that they may be having.

Jeff

---

### Post by Miljet on 2012-05-26
Great! Glad everything worked out and just look at how much you learned today.  If you will, please mark this thread as solved.

---

