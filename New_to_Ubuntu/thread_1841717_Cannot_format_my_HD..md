---
title: "Cannot format my HD."
date: 2011-09-09
forum: New to Ubuntu
---

### Post by SkepticSon on 2011-09-09
Hello!

I've been trying to solve this for days, but I can't find a simple solution for my problem. I'm a Ubuntu newbie.

I had my brother install Ubuntu beside Windows XP some time ago, each OS in a different HD. After trying to upgrade to Windows 7 and facing conflicts with Ubuntu, I decided to format my HDs (probably a very stupid move, but now it's done). Then I tried installing Windows 7 again, but I still had the same issue: I get a message of "grub rescue" and it won't boot into Windows if the installation DVD is not on the drive.


I ended up downloading formatting programs from the manufacturers of each HD (Samsung and Seagate) and performed a Zero Fill on both HDs. I reinstalled Windows 7 again, and still I get the "grub rescue" message.

I don't understand how a zeroed HD still holds information regarding GRUB. Also, as I zeroed everything (or tried to), Ubuntu is obviously not working.

How do I clean up this mess to install Windows 7 and Ubuntu again? Why my zero-fill formatting didn't work as it should? :confused:

Thanks!

---

### Post by nm_geo on 2011-09-10
> **SkepticSon said:**
> Hello!

I've been trying to solve this for days, but I can't find a simple solution for my problem. I'm a Ubuntu newbie.

I had my brother install Ubuntu beside Windows XP some time ago, each OS in a different HD. After trying to upgrade to Windows 7 and facing conflicts with Ubuntu, I decided to format my HDs (probably a very stupid move, but now it's done). Then I tried installing Windows 7 again, but I still had the same issue: I get a message of "grub rescue" and it won't boot into Windows if the installation DVD is not on the drive.


I ended up downloading formatting programs from the manufacturers of each HD (Samsung and Seagate) and performed a Zero Fill on both HDs. I reinstalled Windows 7 again, and still I get the "grub rescue" message.

I don't understand how a zeroed HD still holds information regarding GRUB. Also, as I zeroed everything (or tried to), Ubuntu is obviously not working.

How do I clean up this mess to install Windows 7 and Ubuntu again? Why my zero-fill formatting didn't work as it should? :confused:

Thanks!

Hi welcome to the forums. I would recommend you go to this link and redo the Windows 7 MBR first before you try anything else.

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

Grub writes to the MBR typically and then you removed Ubuntu it has no correct path thus the grub error.

---

### Post by hansolo4949 on 2011-09-10
If that is still happening, that probably means the primary partition on your hdd is still there, and has grub on it. When you install windows, if you go to advanced at one point, you should see a map of all the partitions on your hdd. I would delete them all and install windows anew if you want to start completely fresh. This should work, and I do not believe grub would still ha g around even after deleting all your partitions. When you installed windows and zeroed the drive, you probably did that on one partition, and the one with GRUB on it was still intact.

---

### Post by fdrake on 2011-09-10
get a ubuntu live-cd and run this command in the terminal and post the results;

```
sudo fdisk -lu

```

also have you checked with gparted? (system>admin>gparted)

---

### Post by sidzen on 2011-09-10
I can sympathize!  On occasion, it has been necessary for me to use more than just a simple zero wipe on a used hard drive in order to install a linux distro, usually after Vista.  

What I have done is to use Dban (only 11MB in size) and choose the *ops2* method,

[PHP]Darik's Boot and Nuke: Quick Commands 
  You may enter these commands at the boot prompt. In each case, all disks in 
  the computer will be wiped automatically without confirmation. 
 
    dod       Wipe all disks with the DoD 5220.22-M method. 
    dodshort  Wipe all disks with the short DoD 5220.22-M method. (Default.) 
    ops2      Wipe all disks with the RCMP TSSIT OPS-II method. 
    gutmann   Wipe all disks with the Gutmann method. 
    prng      Wipe all disks with the PRNG Stream method. 
    quick     Wipe all disks with the Quick Erase method.[/PHP]it takes longer, of course, but not as long as others.  And, more importantly, it allowed me to partition and install whatever distro was desired at the time.  

It  can also be found integrated into [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/") (just hit F2 at the first opportunity to get to dban).

Best wishes!

---

### Post by coffeecat on 2011-09-10
Interesting story. 

> **SkepticSon said:**
> I ended up downloading formatting programs from the manufacturers of each HD (Samsung and Seagate) and performed a Zero Fill on both HDs. I reinstalled Windows 7 again, and still I get the "grub rescue" message.

Those apps could not have zeroed the whole drive if you are still getting a grub error message. Perhaps they only zeroed partitions?

Grub gets installed to the mbr (in the first 440 bytes of the first sector), to the embedding area (between the partition table and the first sector of the first partition) and the rest of it is in the root partition of Ubuntu. If you remove (or zero) the Ubuntu root partition, you get a grub error because the residual grub code in the mbr and embedding area has nowhere to go. Therefore - those zero fills could not have zeroed the mbr or embedding area. Actually, the mbr includes the partition table, which is perhaps why they did not.

> **SkepticSon said:**
> Then I tried installing Windows 7 again, but I still had the same issue: I get a message of "grub rescue" and it won't boot into Windows if the installation DVD is not on the drive.

Are you using a Microsoft Windows 7 installation DVD or your OEM manufacturer's recovery DVD? The former will install the Windows booting code to the mbr (overwriting grub) and you shouldn't need to have the Windows DVD in the drive. A manufacturers restore DVD usually doesn't write to the mbr and maybe this is what the problem is.

It would be helpful to see the output of the boot script to see what bootloaders are installed where and what your partition layout is like. Boot up with an Ubuntu live CD and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity.

If you do need to repair the Windows mbr and you do not have a Microsoft installation DVD, this is easily done with an Ubuntu live CD. But let's the the boot script output first.

---

### Post by SkepticSon on 2011-09-11
> **hansolo4949 said:**
> If that is still happening, that probably means the primary partition on your hdd is still there, and has grub on it. When you install windows, if you go to advanced at one point, you should see a map of all the partitions on your hdd. I would delete them all and install windows anew if you want to start completely fresh. This should work, and I do not believe grub would still ha g around even after deleting all your partitions. When you installed windows and zeroed the drive, you probably did that on one partition, and the one with GRUB on it was still intact.

That was the first thing I tried and didn't work. That's why I tried zero-fill on both HDDs.

I'm not sure how I would have zeroed only one partition, I followed the manufacturers instructions to zero everything.


Thanks for all the answers! I'll read them carefully step by step and I'll get back to you all if something worked or not! :D

---

### Post by SkepticSon on 2011-09-11
Here is the results.txt file.

I should say that I tried reinstalling Ubuntu, hoping that would fix grub, but I messed up again and installed in the wrong partition.

This is what I want to do: I want Windows 7 in one HDD and Ubuntu in the other HDD.


Thanks again!

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid ec2d1468-147a-476c-bdf1-dacf0d300bd9 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid d23d7c6b-4df2-4710-99ab-e9f7694270e0 root 
    set 
    prefix=($root)/boot/grub---------------------------------------------------
    -----------------------------.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   488,394,751   488,187,904   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   970,481,663   970,479,616  83 Linux
/dev/sdb2         970,483,710   976,771,071     6,287,362   5 Extended
/dev/sdb5         970,483,712   976,771,071     6,287,360  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        36B81ED0B81E8F0D                       ntfs       System Reserved
/dev/sda2        7C9C224E9C22036E                       ntfs       
/dev/sdb1        ec2d1468-147a-476c-bdf1-dacf0d300bd9   ext4       
/dev/sdb5        96f38f29-932c-4e21-b7be-8ff69ebd5ae8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos1)'
search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
set locale_dir=($root)/boot/grub/locale
set lang=pt_BR
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
menuentry 'Ubuntu, com Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ec2d1468-147a-476c-bdf1-dacf0d300bd9 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, com Linux 2.6.38-8-generic (modo de recuperação)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=ec2d1468-147a-476c-bdf1-dacf0d300bd9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root ec2d1468-147a-476c-bdf1-dacf0d300bd9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 36B81ED0B81E8F0D
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ec2d1468-147a-476c-bdf1-dacf0d300bd9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=96f38f29-932c-4e21-b7be-8ff69ebd5ae8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 148.135105133 = 159.058857984  boot/grub/core.img                             1
 296.212829590 = 318.056103936  boot/grub/grub.cfg                             1
   1.688476562 = 1.812987904    boot/initrd.img-2.6.38-8-generic               2
 148.133281708 = 159.056900096  boot/vmlinuz-2.6.38-8-generic                  1
   1.688476562 = 1.812987904    initrd.img                                     2
 148.133281708 = 159.056900096  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  00 00 00 00 00 00 01 00  0c 04 00 00 b8 1a 00 00  |................|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000020  0c 04 00 00 c8 1a 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 01 00  0c 04 00 00 d8 1a 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000050  0c 04 00 00 e8 1a 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 01 00  0c 04 00 00 f8 1a 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000080  0c 04 00 00 08 1b 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 01 00  0c 04 00 00 18 1b 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
000000b0  0c 04 00 00 28 1b 00 00  00 00 00 00 00 00 00 00  |....(...........|
000000c0  00 00 00 00 00 00 01 00  0c 04 00 00 38 1b 00 00  |............8...|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
000000e0  0c 04 00 00 48 1b 00 00  00 00 00 00 00 00 00 00  |....H...........|
000000f0  00 00 00 00 00 00 01 00  0c 04 00 00 58 1b 00 00  |............X...|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000110  0c 04 00 00 68 1b 00 00  00 00 00 00 00 00 00 00  |....h...........|
00000120  00 00 00 00 00 00 01 00  0c 04 00 00 78 1b 00 00  |............x...|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000140  0c 04 00 00 88 1b 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 01 00  0c 04 00 00 98 1b 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
00000170  0c 04 00 00 a8 1b 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 01 00  0c 04 00 00 b8 1b 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 01 00  |................|
000001a0  0c 04 00 00 c8 1b 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 01 00  0c 04 00 00 d8 1b 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 5f 00 00 00  |............_...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

```

---

### Post by coffeecat on 2011-09-12
> **SkepticSon said:**
> I should say that I tried reinstalling Ubuntu, hoping that would fix grub, but I messed up again and installed in the wrong partition.

This is what I want to do: I want Windows 7 in one HDD and Ubuntu in the other HDD.

As far as I can see, this is what you've got, and if you set the BIOS to boot from sda, the 250GB drive, then you should see a grub menu with a dual-boot Ubuntu and Windows choice. If you set the BIOS to boot from sdb, the 500GB drive, you'll get a grub error similar to what you saw before because grub in the mbr of sdb is pointing to a now non-existent partition. That doesn't matter because the mbr of sdb is unused if you boot from sda.

Your Windows C: partition (sda2) takes up most of sda, and you also have a small Windows 7 boot partition (sda1).

Your Ubuntu root partition is very large, taking up most of your 500GB sdb drive, the rest being the swap partition.

Is everything working OK? Do you wish to change anything? Do you have any other questions? I'll keep the thread subscribed if you want to take this further. By the way, zeroing a drive or partition is really only necessary if you need to securely delete sensitive personal data. If you ever want to re-install, re-format a partition or re-arrange the partitions on a hard drive, simply go ahead and do it. Old data will simply be overwritten in time. It takes a long time to zero things and is not necessary.

---

### Post by reptilezone2002 on 2011-09-12
the same thing happens to me on a old laptop i used to test CentOS cannot install any other OS beside CentOS i manage to format it a gain using a old windows 98 cd.. & that works after i formated the HDD with win98 cd ... after that i can put any OS again try using a win98 boot cd ... it worked for me

or

remove the HDD from ur motherboard fix it on a friends board as a slave hdd & format it that might work 2... 

good luck

---

### Post by SkepticSon on 2011-09-12
coffeecat, I'm actually not sure, because I'm sure how far I understood the results.txt file I posted. I still have several questions:

1 -What I'm trying to do is the following:
    - I want Windows 7 in the 250GB HDD and Ubuntu in the 500GB HDD.
    - As I need Windows 7 for larger programs, the 250GB HDD would be entirely for it.
    - The 500GB HDD would be, apart from Ubuntu, for the storage of files and personal documents **for both OS**.


2- So, from what I understood of results.txt, each OS is already installed in the right HDD in the right partitions, is that correct?


3- I have then 2 different grub2 installed, one in each HDD? Why? Is the grub2 that is not working some kind of residue of the old Ubuntu I had installed? How can I be sure I won't have trouble with that later, or how can I completely remove the unused grub2?

4- You said that the Ubuntu partition is too big, and that there is a "swap" partition. A swap partition is a partition that works for both Windows 7 and Ubuntu? I remember that the files and folders I had in Windows could be seen and opened in Ubuntu as well. So I assume my files should be in a "swap" partition?


I'll change the HDDs order and try to boot it again.


Thanks again!

---

### Post by SkepticSon on 2011-09-12
> **coffeecat said:**
> 
Those apps could not have zeroed the whole drive if you are still getting a grub error message. Perhaps they only zeroed partitions?

Grub gets installed to the mbr (in the first 440 bytes of the first sector), to the embedding area (between the partition table and the first sector of the first partition) and the rest of it is in the root partition of Ubuntu. If you remove (or zero) the Ubuntu root partition, you get a grub error because the residual grub code in the mbr and embedding area has nowhere to go. Therefore - those zero fills could not have zeroed the mbr or embedding area. Actually, the mbr includes the partition table, which is perhaps why they did not.


I don't understand why the MBR wasn't zeroed. What would be your suggestion if I ever have this kind of problem again and wish to zero it? As I said before, I used SeaTools in my Seagate HDD and a Samsung tool in my Samsung drive, and I don't remember having any kind of option regarding that. I followed the instructions believing I was completely removing everything and would not have any trouble like this again.

---

### Post by coffeecat on 2011-09-12
> **SkepticSon said:**
> 
    - I want Windows 7 in the 250GB HDD and Ubuntu in the 500GB HDD.
    

That you've got.

> **SkepticSon said:**
> 
- As I need Windows 7 for larger programs, the 250GB HDD would be entirely for it.

That's fine.

> **SkepticSon said:**
> 
    - The 500GB HDD would be, apart from Ubuntu, for the storage of files and personal documents **for both OS**.

That could be a problem. There are Windows drivers for Linux filesystems but I don't know of one for the ext4 filesystem of your Ubuntu partition. Or rather, I believe there is one, but I don't have a link and I personally wouldn't use it anyway. A better option would be to shrink the Ubuntu partition and create a NTFS partition for shared data. NTFS is the Windows native filesystem and Ubuntu can read and write NTFS reliably.

> **SkepticSon said:**
> 
2- So, from what I understood of results.txt, each OS is already installed in the right HDD in the right partitions, is that correct?


With the caveat above, yes.

> **SkepticSon said:**
> 3- I have then 2 different grub2 installed, one in each HDD? Why? Is the grub2 that is not working some kind of residue of the old Ubuntu I had installed? How can I be sure I won't have trouble with that later, or how can I completely remove the unused grub2?

Don't worry about grub in the mbr of sdb. That section of the drive will be entirely unused if you boot from sda. It won't do any harm. Indeed, it won't do anything.

> **SkepticSon said:**
> 4- You said that the Ubuntu partition is too big, and that there is a "swap" partition. A swap partition is a partition that works for both Windows 7 and Ubuntu? I remember that the files and folders I had in Windows could be seen and opened in Ubuntu as well. So I assume my files should be in a "swap" partition?

Nope. A swap partition is more or less equivalent to the pagefile.sys file in Windows. It's used for swapping out contents of RAM when RAM gets too full. The swap partition is used only by Ubuntu and reading files in Windows C: in Ubuntu is another matter. 

> **SkepticSon said:**
> 
I'll change the HDDs order and try to boot it again.

I think that will fail for reasons I've already explained. The sda drive needs to be the boot drive in your BIOS.

---

### Post by coffeecat on 2011-09-12
> **SkepticSon said:**
> I don't understand why the MBR wasn't zeroed. What would be your suggestion if I ever have this kind of problem again and wish to zero it?

Simple - don't zero. Zeroing a drive to "clean" it up before reformatting or re-installing is just technological voodoo. As I've mentioned, you really only need zeroing apps if you have sensitive data you want securely deleted beyond the reach of data recovery apps.

---

### Post by SkepticSon on 2011-09-12
> **coffeecat said:**
>  A better option would be to shrink the Ubuntu partition and create a NTFS partition for shared data. NTFS is the Windows native filesystem and Ubuntu can read and write NTFS reliably.

What is then the best way to shrink my Ubuntu partition and create a NTFS one?


> **coffeecat said:**
>  Nope. A swap partition is more or less equivalent to the pagefile.sys file in Windows. It's used for swapping out contents of RAM when RAM gets too full. The swap partition is used only by Ubuntu and reading files in Windows C: in Ubuntu is another matter.

So is my swap partition a good size? Would I ever need to change it for some reason? How then? 



> **coffeecat said:**
>  I think that will fail for reasons I've already explained. The sda drive needs to be the boot drive in your BIOS.

Well, then my main problem is here. When I turn on my computer, it says "grug error" and it gives the code of the grub2 on my sdb drive. I thought then I only needed to change their order. What should I do then for the grub2 in my sda drive to start working?

---

### Post by coffeecat on 2011-09-12
> **SkepticSon said:**
> 
Well, then my main problem is here. When I turn on my computer, it says "grug error" and it gives the code of the grub2 on my sdb drive. I thought then I only needed to change their order. What should I do then for the grub2 in my sda drive to start working?

Sorry, I may have made an assumption, or missed something. When you set the 250GB drive (sda) as the boot drive in the BIOS, does the system boot and give you the grub menu? Looking at your boot script output, it should do.

---

### Post by SkepticSon on 2011-09-12
> **coffeecat said:**
> Sorry, I may have made an assumption, or missed something. When you set the 250GB drive (sda) as the boot drive in the BIOS, does the system boot and give you the grub menu? Looking at your boot script output, it should do.

When I turn the computer on, I get a "no such device" error, with the code of the sdb grub. I opened BIOS to change the boot order, but I can't seem to be able to choose with HDD I want. I can only choose if I want to boot from Hard Disk, CDROM, Removable, Legacy LAN or Disabled. Why is it booting from the sdb drive then?

Swapping the HDDs places phisically wouldn't do the trick? That's what I meant in the previous post, and you said it wouldn't. What can I do then? :icon_frown:

---

### Post by westie457 on 2011-09-12
Hi somewhere in your BIOS is a section that lists the Hard drives attached to your system. This is usually in the BOOT tab and is called 'Hard drive boot order' or something similar. Move the drive you want to boot from to the top of this list. Exit the BIOS saving the changes and everything should be good to go.

---

### Post by coffeecat on 2011-09-12
> **SkepticSon said:**
> When I turn the computer on, I get a "no such device" error, with the code of the sdb grub. I opened BIOS to change the boot order, but I can't seem to be able to choose with HDD I want. I can only choose if I want to boot from Hard Disk, CDROM, Removable, Legacy LAN or Disabled. Why is it booting from the sdb drive then?

Swapping the HDDs places phisically wouldn't do the trick? That's what I meant in the previous post, and you said it wouldn't. What can I do then? :icon_frown:

OK, I can see your problem now. If your BIOS only gives you HDD, CDROM, etc for boot order, then it will have another entry to set the priority for the hard drives. That will be where you can give the 250GB drive priority over the 500GB drive. Sorry, I can't tell you exactly where to look - BIOSs vary - but it will be there.

If you are really stuck, then yes, you can change which headers each hard drive is plugged into. You don't have to move the hard drives. If these are SATA (and with a 500GB I would imagine they are) then simply swap the SATA leads around where they are plugged into the motherboard.

I will be logging of in a few minutes. I will have a look at this thread tomorrow and I can pick up the point about creating a NTFS partition then and anything else you need. Good luck finding your way around the BIOS. Keep looking. What you want is there! :)

Oh, one last point. It's a bit odd that your boot drive is designated sdb, but some BIOSs do strange things. If you change the wiring to the drives, sda may become sdb, and vice versa. This might happen if you change the BIOS settings as well. It's not a problem because all the configuration files and grub are using UUIDs. Just something to be aware of.

---

### Post by SkepticSon on 2011-09-12
I'll have a deeper look at my BIOS, and then I'll wait for your tips on making a new NTFS partition.

Thanks a lot!!! :D:D:D

---

### Post by coffeecat on 2011-09-13
@SkepticSon, apologies for not posting before if you are waiting for tips on creating an NTFS partition. I have been distracted with modding duties.

How did you get on with reconfiguring your BIOS? I think it would be better if you confirm that you can now boot into a dual-boot before you try to modify your partition layout. However, creating a NTFS partition in the 500GB drive would simply involve booting up with a live Ubuntu CD, and using Gparted to shrink your sdb1 Ubuntu partition and then creating a primary NTFS partition in the freed space. We can discuss the details when you post back.

I shall await news. :wink:

---

### Post by SkepticSon on 2011-09-16
@coffeecat

Sorry for my late answer, I was a bit busy these days!

I changed the boot order in BIOS and now both Ubuntu and Windows 7 are working perfectly! I also went to GParted already and made the partition that I wanted. Everything is perfect now!!! :D

I just wanted your opinion about one last thing: I read in some places about subpartitioning the ubuntu partition, so that if I ever need to install a new Ubuntu or something I wouldn't loose configurations. Is this really a good thing? I wanted to learn more about that, to see if I would need that or not.

I really can't thank you enough! You really helped me save my computer, and now I know some Ubuntu basics that makes it easier from now on.

Thanks!!! :D

---

### Post by coffeecat on 2011-09-16
I'm glad you sorted out the BIOS and booting, and also creating a data partition.

> **SkepticSon said:**
> 
I just wanted your opinion about one last thing: I read in some places about subpartitioning the ubuntu partition, so that if I ever need to install a new Ubuntu or something I wouldn't loose configurations. Is this really a good thing? I wanted to learn more about that, to see if I would need that or not.

I guess you mean a separate home partition. Some people prefer this, whereas some people prefer a separate data partition. I'm in the latter camp so I'm not the best person to advise about a home partition. A home partition has advantages in that all your personalisations and configurations are retained when you upgrade. But it has disadvantages in that upgrading can introduce problems if newer versions of software and their configurations are significantly different. With the forthcoming transition to a gnome3 base with a very different set of gnome configurations, I would prefer not keep a separate home when upgrading Natty -> Oneiric. In any event having a separate home and a separate data partition is wasteful of hard drive space.

But others may disagree with me and are welcome to comment! :)

Good luck!

---

