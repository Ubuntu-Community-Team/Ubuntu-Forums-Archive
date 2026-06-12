---
title: "Anyone else having issues with separate /home?"
date: 2011-06-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yes_It's_Me on 2011-06-27
Hey guys,

Anyone else having issues with using a separate partition for /home? My old ubuntu installation (RIP) was following the dev cycle since oneiric opened for business. A few days ago BAM. I get the dreaded /home device not ready continue to wait or press S to skip/M for manual recovery message upon boot. I checked my fstab UUIDs against blkid's output, and tried using /dev/sdXX device names but it still couldn't get /home mounted.

When I enter manual recovery I can mount the partition, but exiting using Ctrl+D just results in a hang.

I reinstalled from the latest daily build but I get the same issue? Am I the only one with this problem? I might file a bug about this later when I have time.

---

### Post by sparker256 on 2011-06-27
> **Yes_It's_Me said:**
> Hey guys,

Anyone else having issues with using a separate partition for /home? My old ubuntu installation (RIP) was following the dev cycle since oneiric opened for business. A few days ago BAM. I get the dreaded /home device not ready continue to wait or press S to skip/M for manual recovery message upon boot. I checked my fstab UUIDs against blkid's output, and tried using /dev/sdXX device names but it still couldn't get /home mounted.

When I enter manual recovery I can mount the partition, but exiting using Ctrl+D just results in a hang.

I reinstalled from the latest daily build but I get the same issue? Am I the only one with this problem? I might file a bug about this later when I have time.
I have two installs 32 & 64 bit of 11.10 both with a separate /home and have not had the issues you describe.

Bill

---

### Post by Yes_It's_Me on 2011-06-27
Dammit. I hate it when stuff like this happens. :( The second time I tried it was a clean daily build install with nothing done except upgrades applied. 

Sucks. Apparently the latest unity builds are much improved, and I'm missing out by using this positively ancient natty install. :(

---

### Post by rbrick49 on 2011-06-27
> **Yes_It's_Me said:**
> Dammit. I hate it when stuff like this happens. :( The second time I tried it was a clean daily build install with nothing done except upgrades applied. 

Sucks. Apparently the latest unity builds are much improved, and I'm missing out by using this positively ancient natty install. :(
yes I tried to install on new hard drives same thing I guess no root patition can not install but gparted tells me sdc1 ext4,sdc2 extended,sdc5 linux swap I have no idea

---

### Post by jfernyhough on 2011-06-27
Try downgrading mount to 2.17. It was updated to 2.19 yesterday and it's been the cause of at least one problem - this sounds like another.

---

### Post by Yes_It's_Me on 2011-06-28
Yeah, I'll try that later tonight. I will dig around a bit and post a bug perhaps.

Nope. Downgrading to mount 2.17 produces no difference in results. I'm posting a bug to launchpad. Currently using links2 to write this reply. ;) There was a new kernel upgrade that hit my mirrors a few hours ago but it didn't help either. :(

I didn't file a bug last night, doing it over link2 was just oo hard.

But lucky I didn't because today's updates fixed this sucker right up and now Everything working again (for the first time in 2 weeks).

---

### Post by tlcstat on 2011-06-29
Greetings,
This is just me but I use 
256meg Primary ext2 boot for Grub
20gig Primary ext4 / root
20gig Extended ext4 usr
512meg swap ( I have 4 gig of ram )
remainding Extended ext4 home

There are several schemes for Swap but I've not seen Ubuntu use more than 200meg so I don't waste the space. 
I remove my primary hard drive before I install a test version so that the install doesn't mess with my boot partition. I prefer that the test drive have it's own boot sector.
tlcstat

---

### Post by seeker5528 on 2011-06-29
> **tlcstat said:**
> Greetings,
This is just me but I use 
256meg Primary ext2 boot for Grub
20gig  Primary ext4 / root
20gig Extended ext4 usr
512meg swap ( I have 4 gig of ram )
remainding Extended ext4 home

Do you have a reason for using that scheme or do you just like to make things overly complicated. ;)

Later, Seeker

---

### Post by tlcstat on 2011-06-29
Greetings,

Original quote by Seeker
> Do you have a reason for using that scheme or do you just like to make things overly complicated. 

An old timer on this site passed that scheme on to me and I liked the results more than a single partition. Like I said its just the way that I do it. You don't need to go to the trouble, some people don't have the extra sixty seconds to spare. I'm retired so I have plenty of time and a box full of hard drives. 
tlcstat
+
P.S. Of course the post was about having a problem with multiple partitions with the Ocelot as I recall.

Here's my boot info for my Natty partition, my Ocelot is at home.
```

Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks for b7can.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows XP
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________ _______________________

File system: ext2
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: /grub/grub.cfg /grub/core.img

sda3: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

sda4: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 11.04
Boot files/dirs: /etc/fstab

sda6: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

sda7: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

sda8: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

sda9: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 63 102,398,309 102,398,247 7 HPFS/NTFS
/dev/sda2 * 102,398,310 103,426,469 1,028,160 83 Linux
/dev/sda3 103,428,096 109,645,823 6,217,728 82 Linux swap / Solaris
/dev/sda4 109,647,870 976,773,119 867,125,250 5 Extended
/dev/sda5 109,647,872 150,607,871 40,960,000 83 Linux
/dev/sda6 150,609,920 191,569,919 40,960,000 83 Linux
/dev/sda7 191,571,968 232,531,967 40,960,000 83 Linux
/dev/sda8 232,534,016 771,158,015 538,624,000 83 Linux
/dev/sda9 771,160,064 976,773,119 205,613,056 7 HPFS/NTFS


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/sda1 DCE84B5BE84B32D6 ntfs 
/dev/sda2 c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e ext2 
/dev/sda3 a0dce929-cea3-431c-a378-981c4c0a8dc1 swap 
/dev/sda4: PTTYPE="dos" 
/dev/sda5 0b7b3222-f1ed-4a45-b90d-87eb80640754 ext4 
/dev/sda6 eeb5add6-f5f4-407b-b1a3-a317963721d8 ext4 
/dev/sda7 98821d98-28c3-4cb4-8130-30f297fd4c62 ext4 test 
/dev/sda8 ed52d2bc-79dc-42d6-bbc9-e444af7a820c ext4 
/dev/sda9 20F366DD2552C745 ntfs ntfs2 
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sda5 / ext4 (rw,errors=remount-ro,commit=0)
/dev/sda2 /boot ext2 (rw)
/dev/sda8 /home ext4 (rw,commit=0)
/dev/sda9 /windows fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
/dev/sda6 /usr ext4 (rw,commit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect

============================= sda2/grub/grub.cfg: =============================

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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root eeb5add6-f5f4-407b-b1a3-a317963721d8
if loadfont /share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
set locale_dir=($root)/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
set timeout=-1
else
set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root eeb5add6-f5f4-407b-b1a3-a317963721d8
insmod png
if background_image /share/images/desktop-base/spacefun-grub.png; then
set color_normal=light-gray/black
set color_highlight=white/black
else
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux	/vmlinuz-2.6.38-10-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro quiet splash vt.handoff=7
initrd	/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
echo	'Loading Linux 2.6.38-10-generic ...'
linux	/vmlinuz-2.6.38-10-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro single 
echo	'Loading initial ramdisk ...'
initrd	/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux	/vmlinuz-2.6.38-9-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro quiet splash vt.handoff=7
initrd	/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
echo	'Loading Linux 2.6.38-9-generic ...'
linux	/vmlinuz-2.6.38-9-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro single 
echo	'Loading initial ramdisk ...'
initrd	/initrd.img-2.6.38-9-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux	/vmlinuz-2.6.38-8-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro quiet splash vt.handoff=7
initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
echo	'Loading Linux 2.6.38-8-generic ...'
linux	/vmlinuz-2.6.38-8-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro single 
echo	'Loading initial ramdisk ...'
initrd	/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux	/vmlinuz-2.6.38-7-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro quiet splash vt.handoff=7
initrd	/initrd.img-2.6.38-7-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
echo	'Loading Linux 2.6.38-7-generic ...'
linux	/vmlinuz-2.6.38-7-generic root=UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 ro single 
echo	'Loading initial ramdisk ...'
initrd	/initrd.img-2.6.38-7-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e
linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root DCE84B5BE84B32D6
drivemap -s (hd0) ${root}
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

menuentry "Fluppy 13 (frugal on sda8)" {
set root='(hd0,8)'
linux /fluppy13/vmlinuz psubdir=fluppy13
initrd /fluppy13/initrd.gz
} 

menuentry "Pupeee 4.4 (frugal on sda8)" {
set root='(hd0,8)'
linux /pupeee/vmlinuz psubdir=pupeee
initrd /pupeee/initrd.gz
} 
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda2: Location of files loaded by Grub: ===================


52.5GB: grub/core.img
52.5GB: grub/grub.cfg
52.4GB: initrd.img-2.6.38-10-generic
52.4GB: initrd.img-2.6.38-7-generic
52.4GB: initrd.img-2.6.38-8-generic
52.5GB: initrd.img-2.6.38-9-generic
52.5GB: vmlinuz-2.6.38-10-generic
52.4GB: vmlinuz-2.6.38-7-generic
52.4GB: vmlinuz-2.6.38-8-generic
52.4GB: vmlinuz-2.6.38-9-generic

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=0b7b3222-f1ed-4a45-b90d-87eb80640754 / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda2 during installation
UUID=c1e40ce8-e93e-4e3a-9ccb-d9b610e61d9e /boot ext2 defaults 0 2
# /home was on /dev/sda8 during installation
UUID=ed52d2bc-79dc-42d6-bbc9-e444af7a820c /home ext4 defaults 0 2
# /usr was on /dev/sda6 during installation
UUID=eeb5add6-f5f4-407b-b1a3-a317963721d8 /usr ext4 defaults 0 2
# /windows was on /dev/sda9 during installation
UUID=20F366DD2552C745 /windows ntfs defaults,umask=007,gid=46 0 0
# swap was on /dev/sda3 during installation
UUID=a0dce929-cea3-431c-a378-981c4c0a8dc1 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


56.2GB: initrd.img
56.2GB: initrd.img.old
56.2GB: vmlinuz
56.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb

```

---

### Post by seeker5528 on 2011-06-30
> **tlcstat said:**
> An old timer on this site passed that scheme on to me and I liked the results more than a single partition. Like I said its just the way that I do it. You don't need to go to the trouble, some people don't have the extra sixty seconds to spare.

It's not about 'How much time does it take to set it up?' it's about 'What purpose does it serve?'.

In particular this is what stood out.

> 20gig Primary ext4 / root
20gig Extended ext4 usr

What purpose is served by having '/usr/' be a seperate partition? And since it is a separate partition, what need is there for '/' to be 20gig?

My whole single partition installations are on 15 to 20 GB partitions, 20 for the installation on my main machine and 15 for all my other machines. This is figuring that I will have 5 GB or less in my home directory since everything I want to keep gets stored, moved, or copied to other partitions mounted in '/media/something/' or '/mnt/something/' and leaving some room for expansion as new software becomes available and newer versions of installed software increase in size.

Later, Seeker

---

### Post by tlcstat on 2011-07-01
Greetings,

Original by Seeker
> It's not about 'How much time does it take to set it up?' it's about 'What purpose does it serve?'.

The OP was a question as to whether others were having trouble creating a separate Home partition with the Oneiric install. My response was that the multi partition feature was working and that I used it myself on my current install. 
If you don't get the reason for the partitioning I suggest you start a post in the general forum instead of this testing forum since it applies to all versions of Ubuntu and in fact Debian. 
tlcstat 

PS. this is my boot55.txt from my working Ocelot.
+

```


Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks for \d.

sda1: __________________________________________________ _______________________

File system: ext2
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: /grub/grub.cfg /grub/core.img

sda2: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu oneiric (development 
branch)
Boot files/dirs: /etc/fstab

sda3: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

sda6: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

sda7: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: 
Boot files/dirs: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 499,711 497,664 83 Linux
/dev/sda2 499,712 39,561,215 39,061,504 83 Linux
/dev/sda3 39,563,262 312,580,095 273,016,834 5 Extended
/dev/sda5 39,563,264 78,622,719 39,059,456 83 Linux
/dev/sda6 78,624,768 82,528,255 3,903,488 82 Linux swap / Solaris
/dev/sda7 82,530,304 312,580,095 230,049,792 83 Linux


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/sda1 13f791a7-13c2-47b9-81f7-0327707a8931 ext2 
/dev/sda2 48eaf3dd-e1d4-4623-8e66-589f1b5ce01e ext4 
/dev/sda3: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="3" 
/dev/sda5 07bf726c-89a1-4d02-87e4-08371f212b5d ext4 
/dev/sda6 57508767-04c1-456d-bb7d-d9671e855722 swap 
/dev/sda7 cb39fd2c-3e68-4fa7-b256-076b10176f0d ext4 
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sda2 / ext4 (rw,errors=remount-ro,commit=0)
/dev/sda1 /boot ext2 (rw)
/dev/sda5 /usr ext4 (rw,commit=0)
/dev/sda7 /home ext4 (rw,commit=0)


============================= sda1/grub/grub.cfg: =============================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 07bf726c-89a1-4d02-87e4-08371f212b5d
if loadfont /share/grub/unicode.pf2 ; then
set gfxmode=auto
load_video
insmod gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 13f791a7-13c2-47b9-81f7-0327707a8931
set locale_dir=($root)/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 13f791a7-13c2-47b9-81f7-0327707a8931
linux /vmlinuz-3.0-2-generic root=UUID=48eaf3dd-e1d4-4623-8e66-589f1b5ce01e ro quiet splash vt.handoff=7
initrd /initrd.img-3.0-2-generic
}
menuentry 'Ubuntu, with Linux 3.0-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 13f791a7-13c2-47b9-81f7-0327707a8931
echo 'Loading Linux 3.0-2-generic ...'
linux /vmlinuz-3.0-2-generic root=UUID=48eaf3dd-e1d4-4623-8e66-589f1b5ce01e ro single nomodeset 
echo 'Loading initial ramdisk ...'
initrd /initrd.img-3.0-2-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 13f791a7-13c2-47b9-81f7-0327707a8931
linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 13f791a7-13c2-47b9-81f7-0327707a8931
linux16 /memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f $prefix/custom.cfg ]; then
source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


.2GB: grub/core.img
.2GB: grub/grub.cfg
.0GB: initrd.img-3.0-2-generic
.0GB: vmlinuz-3.0-2-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda2 during installation
UUID=48eaf3dd-e1d4-4623-8e66-589f1b5ce01e / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=13f791a7-13c2-47b9-81f7-0327707a8931 /boot ext2 defaults 0 2
# /home was on /dev/sda7 during installation
UUID=cb39fd2c-3e68-4fa7-b256-076b10176f0d /home ext4 defaults 0 2
# /usr was on /dev/sda5 during installation
UUID=07bf726c-89a1-4d02-87e4-08371f212b5d /usr ext4 defaults 0 2
# swap was on /dev/sda6 during installation
UUID=57508767-04c1-456d-bb7d-d9671e855722 none swap sw 0 0

=================== sda2: Location of files loaded by Grub: ===================


.3GB: initrd.img
.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda3

00000000 5c c7 db dc 84 6e 6f 92 23 38 9e 1e 04 3a 3f 4b |\....no.#8...:?K|
00000010 3a be 8c 98 70 c3 2f ff a3 d4 dd 88 0e 2f b1 f8 |:...p./....../..|
00000020 42 a3 ec a9 0a cc 9b 27 d3 99 07 c4 e8 c2 e1 f2 |B......'........|
00000030 e0 fe 3d c7 54 79 3c 47 d1 8a 3e 9a 3f 0c 0f 22 |..=.Ty<G..>.?.."|
00000040 79 7f 5d 8a 9f 49 ab 0e 18 42 e8 6a 42 72 e4 42 |y.]..I...B.jBr.B|
00000050 7d b8 7f ff a3 c9 e0 58 d4 bb 71 c0 83 ec 21 78 |}......X..q...!x|
00000060 0d 1a b6 79 3e df c7 01 a1 0a 5e 2e 2d 1d 8a 96 |...y>.....^.-...|
00000070 38 15 73 28 73 35 4d 0e a9 d4 7a 18 b6 74 39 a7 |8.s(s5M...z..t9.|
00000080 93 27 26 a6 2e 07 04 a1 47 23 03 02 ef db 9b b1 |.'&.....G#......|
00000090 90 b9 3c 1a 9a 97 3c 38 15 30 70 28 dc 4c 12 e3 |..<...<8.0p(.L..|
000000a0 ab fc 5c a9 57 71 fd 28 78 13 73 76 c6 ed 46 a9 |..\.Wq.(x.sv..F.|
000000b0 46 a9 e4 6a e8 78 71 71 68 dd 2a 3c 13 4f ff a3 |F..j.xqqh.*<.O..|
000000c0 fa 61 ba 72 73 47 63 a9 f6 59 f4 ee fd 0e e5 0d |.a.rsGc..Y......|
000000d0 8a b4 6e 7e a7 17 83 42 cd 1a 98 8f 27 26 c7 63 |..n~...B....'&.c|
000000e0 23 53 ab 0a 0a 9d 0e c6 6d 07 bb 46 8c 20 21 e3 |#S......m..F. !.|
000000f0 c8 ea ea d5 c9 30 70 1b 1c 0b 3c 9b 35 1b 15 6c |.....0p...<.5..l|
00000100 e6 50 6c d8 e2 ea d9 b3 66 87 03 9a 50 6a 68 36 |.Pl.....f...Pjh6|
00000110 4c 1b 90 89 c4 b1 45 cd ec 37 1b 1d 5c dd 7f ff |L.....E..7..\...|
00000120 a3 ea 7b 21 d1 b3 cc c5 ea 64 98 be 5c 0a 3d 5b |..{!.....d..\.=[|
00000130 19 a6 ef 93 93 c5 d1 84 6f 11 e2 fe 34 2a 73 2e |........o...4*s.|
00000140 58 e0 38 15 61 19 f6 50 6a 50 fa 30 79 b9 b8 31 |X.8.a..PjP.0y..1|
00000150 2d b0 f8 32 33 78 3f 06 cf f3 73 73 03 23 67 61 |-..23x?...ss.#ga|
00000160 30 61 0b 51 35 74 6c 96 2a 76 2a 7e 97 1e e6 9f |0a.Q5tl.*v*~....|
00000170 ff a3 b9 0f 11 ab 07 c7 f1 c4 7d 38 0d 4e ad 0d |..........}8.N..|
00000180 cd de 07 47 34 6c fe 8d 0b 9a 27 01 37 68 59 fa |...G4l....'.7hY.|
00000190 1e 46 c6 05 cf b4 a1 72 ad cc 47 53 67 23 57 f5 |.F.....r..GSg#W.|
000001a0 c5 e2 50 4b 0f 16 c9 ba 72 38 34 3f 0e af 34 a1 |..PK....r84?..4.|
000001b0 47 99 e9 1b a5 4c 4c c7 47 17 23 c9 90 d1 00 fe |G....LL.G.#.....|
000001c0 ff ff 83 fe ff ff 02 00 00 00 00 00 54 02 00 fe |............T...|
000001d0 ff ff 05 fe ff ff 02 00 54 02 00 98 3b 00 00 00 |........T...;...|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb
+


```

---

### Post by seeker5528 on 2011-07-01
> **tlcstat said:**
> 
If you don't get the reason for the partitioning I suggest you start a post in the general forum instead of this testing forum since it applies to all versions of Ubuntu and in fact Debian.

What sizes used depend on what software you use and how much you think you need for future expansion, it's better to give too many GBs to some partitions than not enough.

There should still be plenty of stuff spread around the net that talks about the historical reasoning for different partitioning schemes and when you might use them.

I was just asking the question that might get you to question and investigate your own usage and you seem perfectly capable of doing 'df -h' to see how much of each partition is actually being used. 

If you are OK with it, I'm OK with it, no need to take up any more of this thread about it. 

Opening a new thread about it would be up to you if you want to discus if your partitioning scheme makes sense when '/usr/' is not a share that is on another machine on your network and what might be an improvement.

Later, Seeker

---

