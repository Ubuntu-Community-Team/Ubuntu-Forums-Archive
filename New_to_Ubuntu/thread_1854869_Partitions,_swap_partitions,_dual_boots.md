---
title: "Partitions, swap partitions, dual boots"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by be0562 on 2011-10-05
Hi everyone,

I've been searching for answers to my questions, but to no avail. Apologies if I've missed them elsewhere and apologies for the long read!

1st - I seem to have 2 swap partitions, both 2.1 GB. I have 2GB RAM. From what I've read, swap files/partitions are usually twice the size of the RAM. So this makes sense, only I have 2 at 2.1GB. Is there a maximum Swap partition size? Otherwise I don't see why I don't have 1 at 4GB.

2nd - I am interested in splitting the file system partition for a couple of reasons. Reading here that having the '/' and the '/home' separate can have advantages if you want to change the OS without changing personal files. Also I would like to erase/wipe unused disc space every now and then and doing that on a smaller partition as opposed to the whole drive would save a lot of time and wear on the drive. (I only need to wipe personal files, web history, desktop files etc. not the OS.)

3rd - Ubuntu is awesome, but some higher end programmes I can't get working with Wine (in fact I can't get much working with Wine), so I may need to install a dual boot with Windows. How do I juggle and split my partitions about so that I can install? And can the /Home partition (if changed to NTFS) be used by Windows? Or do I need a separate shared user files partition?

Thanks for reading any help is appreciated.

---

### Post by audiomick on 2011-10-05
First of all, some links:

To find Ubuntu related help
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Found using the search window there
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I found them quickly, because I already knew they were there, but the search function there works pretty well, I find.

As far as swap goes, as you will read in the link, the reason for having a bit more swap than you do RAM is so that the hibernate function works. I don't think 2 x RAM is really necessary anymore. I have had HIbernate working properly with 4.5GB swap and 4GB RAM. I have more than that now, but that is due to my installation being in flux at the moment.

The logic that 2 swap partitions of 2GB for a total of 4GB should allow Hibernate does not seem to work. I had that for a while, and could not hibernate the computer. The Hibernate function only started to work after I had changed the swap setup to one partition that was bigger than the RAM. By coincidence, I currently have 2 swap partitions again, due to the transient state of my install. One of the 2 is larger than the amount of RAM I have, and the Hibernate function is working.

If you know you do not want to hibernate, and have a "modern" amount of RAM, you should not really need more than 2GB or so of swap. There is no upper limit that I am aware of to how big  swap can be. How much you assign is a question of whether you want to hibernate, how much RAM you have, and how much disk space you can spare. Have a look at you system monitor occasionally to see how much of your RAM and swap you are really using.

Regarding your data partition. I would not let Windows mess with my /home folder. Also, even if it is possible to make your /home an ntfs partition, and I don't think it is, I would not do it because ntfs does not support Linux permissions. You should set up an extra partition for data that both windows and Linux can access. If you want, you can tell things like Libre Office to store to there by default.

---

### Post by be0562 on 2011-10-05
Michael,

Thanks for your quick reply. I'll get reading those links.

---

### Post by Mark Phelps on 2011-10-05
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu.  Do NOT use the Ubuntu installer to do this.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by be0562 on 2011-10-05
Hi Mark

Thanks for your reply. I'm still reading the links from above and not got onto dual boot yet. But to clarify (I should've mentioned this earlier)

I have a 120Gb hd, originally Windows Vista. 12Gb is reserved for a Vista recovery partition. The remaining 108Gb I have installed Ubuntu (11.04) on. So I will be needing to reduce partition sizes in Ubuntu first before setting the empty space as windows partitions. - But which partition manager to use and when I'm still to find out.

I only have the legal Vista copy and I can't be bothered with all that MS copy protection any more, so if I do dual boot it will be with Vista for the time being.

@ Michael - Been reading the swapfaq, I think I will go to one and have 2.5Gb. Using my system monitor it only shows one 2Gb swap partition. So I think there are 2 swap partitions because it took a few installs before I got Ubuntu working for some reason. Perhaps one was set up and then another one later when I reinstalled. It seems like one isn't being used anyway.

---

### Post by Quackers on 2011-10-05
A couple of points.
Firstly one swap partition will be fine, but you must keep the one that Ubuntu is presently using and increase its size, then delete the second.  Otherwise you will need to edit the /etc/fstab file, as your new swap may not be found without it.
Your Ubuntu partition can be reduced in size using gparted from a live cd session - not from gparted within a normal Ubuntu session.
Swap will need to be unmounted (swapoff).

NOTE  As gparted will inform you, there is a risk when moving a bootable partition. Data can be lost or the system can become unbootable.

One last thing.
It will depend on how you re-install Windows. If you are using an installation disc you will be fine with the amended partitions.
If you intend to use a (set of) recovery discs to replace a pre-installed system, then those recovery discs may insist on using the whole hard drive when re-installing. This will over-write all your data - Ubuntu system included.

It is always good practice to have backups of everything you need before embarking on your journey :-)

---

### Post by be0562 on 2011-10-08
Hi all, right I've backed up my files and now plunged into gparted and changed the way I want it set up. It's not booting now however. I'm not too bothered, I can just reinstall both, either Ubuntu first or Windows first. However I would like to try to recover Ubuntu, that way any customisation I've made will remain.

So I found another forum, and found a way to get my boot details in text to post here. So here goes:

```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/BCD

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 36360 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,046   210,370,559   210,368,514   5 Extended
/dev/sda5               2,048   102,629,375   102,627,328  83 Linux
/dev/sda6         102,631,424   205,201,407   102,569,984   7 NTFS / exFAT / HPFS
/dev/sda7         205,203,456   210,370,559     5,167,104  82 Linux swap / Solaris
/dev/sda2         210,371,175   234,436,544    24,065,370   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8017 MB, 8017936384 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15660032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    15,660,031    15,659,969   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        2C88743C8874071C                       ntfs       PRESARIO_RP
/dev/sda5        817af9f6-d896-4b29-b3c0-42f24b11d776   ext4       Linux OS
/dev/sda6        1D6FF9073097E1AF                       ntfs       Windows partition
/dev/sda7        f08950ea-1c28-43e5-9045-8b8bf5b091dd   swap       Linux swap part
/dev/sdb1        822B-55CA                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=817af9f6-d896-4b29-b3c0-42f24b11d776 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=817af9f6-d896-4b29-b3c0-42f24b11d776 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=817af9f6-d896-4b29-b3c0-42f24b11d776 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=817af9f6-d896-4b29-b3c0-42f24b11d776 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 817af9f6-d896-4b29-b3c0-42f24b11d776
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 2C88743C8874071C
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
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8fb41829-e3de-45dc-a7a5-6580fa68c62b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  44.135009766 = 47.389605888   boot/grub/core.img                             1
  44.174705505 = 47.432228864   boot/grub/grub.cfg                             1
   3.880134583 = 4.166262784    boot/initrd.img-2.6.38-11-generic              1
   2.145759583 = 2.303991808    boot/initrd.img-2.6.38-8-generic               1
   3.638004303 = 3.906277376    boot/vmlinuz-2.6.38-11-generic                 1
  44.133281708 = 47.387750400   boot/vmlinuz-2.6.38-8-generic                  1
   3.880134583 = 4.166262784    initrd.img                                     1
   2.145759583 = 2.303991808    initrd.img.old                                 1
   3.638004303 = 3.906277376    vmlinuz                                        1
  44.133281708 = 47.387750400   vmlinuz.old                                    1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```If anyone can help me recover my OS that would be great!
Thanks

n.b. The sdb 8gb drive is the USB stick I'm running Ubuntu live from.

---

### Post by searchfgold6789 on 2011-10-08
Ideally, one would simply install Windows first and the install Linux because that way is easier. Much easier.
If you want to change your ~ (home) partition location, simply:

[LIST]
[*]Set up the partitions the way you want
[*]Move the data from your old ~ to your new ~
[*]Edit your fstab file and make sure to add the "user" option. You may have to modify the permissions on the mount point itself as well.
[/LIST]
I can provide detailed instructions if you wish; there is an automatic tool as well, it's called [Ubuntu Tweak]("http://ubuntu-tweak.com/").
You should be able to recover your Ubuntu customizations, just access the partition using Live media.
 - search

---

### Post by Elfy on 2011-10-08
I'd try to reinstall grub - but that's a guess as > It's not booting now however is quite vague :)

Be better to know exactly what happens

 [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by be0562 on 2011-10-08
Hi forestpiskie, it says this upon boot:

error: unknown filesystem
grub rescue>

I've just read the link so I'll try reinstalling grub. If that works and I get my ubuntu back, I'll add windows, then reinstall grub again if necessary.

---

### Post by Quackers on 2011-10-08
Grub is looking in /dev/sda6 for its boot files, but they are in /dev/sda5. This is your problem. I'm not sure how that happened but it did :-)
If you re-install grub with the following commands from a live session desktop the system should be bootable again.  ```
sudo mount /dev/sda5 /mnt  
sudo grub-install --boot-directory=/mnt /dev/sda
```

---

### Post by oldfred on 2011-10-08
It looks like you have moved partitions around. 

Grub & fstab are trying to boot from sda6, but your install is in sda5. The search by UUID will correct for that in grub.cfg but not the MBR, but you still have to manual update /etc/fstab as you must have changed it from UUID style to device style and now the device /dev/sda6 is wrong.

> proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sda6   [/COLOR]    /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8fb41829-e3de-45dc-a7a5-6580fa68c62b none            swap    sw              0       0
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by be0562 on 2011-10-08
Quakers and oldfred - sda6 used to be the partition with ubuntu on it, 5 + 7 were the swap partitions. In gparted I juggled it about, and then the main partition ended up as 5, the ntfs main as 6 and then swap as 7 which looked more ordered. I should've realised this discrepency.

Thanks for your responses. In the meantime I reinstalled ubuntu over the old one, but chose the 'don't touch my sh*t option' as opposed to a complete install.

The install doesn't work properly, but it does boot. However on the boot option 'previous linux installations', I can now load my previous Ubuntu with (apparent) complete control and usage, which is what I'm typing from.

During this I tried accessing the recovery partition for Vista, and then went through an install of this as I'd have to at some point anyway. The only option suitable was a complete recovery to factory settings (as there's no windows OS currently installed), so I figure all my ubuntu will go anyway.

During this the installation failed, so my Vista recovery is now not working. I don't know if this is because the hard disc has different partitions to what it had at the factory, but I see no reason as to why the recovery partition wont work, I haven't touched the files on there.

Unless there are any ideas, I supposed my next options are:

Phone the techguys to do a factory reset of the pc.
Update vista
Boot from the SDHC card with Ubuntu on it and partition the disc (or partition from Vista first?)
Install Ubuntu from scratch on the new partition as a dual boot
Update Ubuntu
Install programmes on Vista and Ubuntu
Have a beer.

Any thoughts?

---

### Post by Quackers on 2011-10-08
It is likely that the factory reset (recovery) option will over-write the whole disc. When running it did you get offered a decision to restore the C: drive or the whole system?
Didn't you make the set of recovery dvd's from your Windows system? That should be the first thing you do really.
I suspect that if your recovery partition is not working and you don't have the recovery dvd set you are likley to be asked to pay for a set of discs.

I would try the recovery process again using the key press during boot (it may be F11 or a combination of keys - your manual will tell you) and explore any options available.

EDIT  Actually looking again at your boot script output I see no recovery partition at all! It may have been over-written during the installation of Ubuntu.

---

### Post by be0562 on 2011-10-08
Quackers

I only had the option to restore a previous os,  and there were none listed so I clicked continue and it took me to the factory reset page. I'll try again and note the error message.

I didn't make recovery dvds because I had the recovery partition, and I also have damage insurance for the laptop, which includes fixing it when it's broken. Seeing as I've been paying out I think it's about time I made the most of my money!

Here's the recovery partition from the printout

/dev/sda2         210,371,175   234,436,544    24,065,370   7 NTFS / exFAT / HPFS

5 = ubuntu os now
6 = ntfs blank
7 = swap partition
2 = ntfs recovery partition

I'll try the recovery again now, and note down the error message this time...

---

### Post by Quackers on 2011-10-08
Always make the recovery dvd's :-)  Recovery partitions can break!

Good luck with the recovery. However if it fails and it goes back I would recommend deleting all partitions so they don't know what's been done. It may save some argument :-)

sda2 looks small for a recovery partition.

---

### Post by be0562 on 2011-10-08
Yep fair one, should've backed up the OS.

SDA2 is 12 Gb, I've just checked again, it's still there with HP's software and windows on it! Plus the windows recovery is working to a degree.

Right the latest is this:

Same error when trying the vista recovery option. It takes me to 'factory image recovery' then there are 2 check boxes.
1st is 'reformatting the windows part of your hard disc drive'  - which is checked,
2nd is 'reinstalling the original content' - which is unchecked.

The progress bar shows 0% and the error that comes up is
"Error. 0x4001100 20000 100A
If this issue continues please contact HP support"

Googling the code shows a lot of failed hdd, but I am inclined to think that it's trying to re-format my main partition which is now split differently to how it was at the factory. Therefore it's looking for it and can't find it.

I'm thinking:
Delete all partitions and either leave it unallocated, or start a new partition, then try again.
Contact HP support and tell them the situation and ask for their advice - could take a while
Contact the techguys (or whoever they are) and explain. -I'll check it's covered first before telling them what I've done...

Any other ideas?

Thanks

---

### Post by oldfred on 2011-10-08
Windows only knows and understands active NTFS primary partitions or boot flag. In boot script above you have boot flag on the extended partition so it cannot see that as the active NTFS partition. Move boot flag with gparted or disk utility to your NTFS partition and see if that makes a difference.

---

### Post by be0562 on 2011-10-08
Changed the boot flag to the NTFS and still no luck. Exactly the same error.

I'm confused as to how it booted though, as the boot flag was no longer in the extended partition (sda1) but in the NTFS (sda6). Surely it would try to boot to a partition with no OS in it and therefore fail?

---

### Post by Quackers on 2011-10-08
The boot flag needs to be on a primary partition I would think. Try moving it to sda2 and see what happens. The recovery may run, perhaps.

---

### Post by be0562 on 2011-10-08
Nope. Again exactly the same.

---

### Post by Quackers on 2011-10-08
So what happens when you get to the factory reset page?
What options are available, if any?
How do you arrive at that page - is it by pressing a particular key during boot?

---

### Post by be0562 on 2011-10-08
To get to the factory reset page I boot as normal. The ubuntu (grub?) boot loader screen shows
ubuntu
ubuntu safe mode (or words to that effect)
previous ubuntu installs
something else I can't remember
and the vista one.

I choose the last option. Windows starts loading and then you end up with this window entitle 'windows recovery options' (2nd screenshot on this forum)

[http://digiex.net/downloads/download-center-2-0/applications/956-windows-vista-32-bit-x86-recovery-disc.html](http://digiex.net/downloads/download-center-2-0/applications/956-windows-vista-32-bit-x86-recovery-disc.html)

I choose startup repair as none of the other options apply, then it says  it may reboot. It does, then I have the boot loader menu again and  choose the last option again. This time it goes straight to the HP recovery 

[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00809678&lc=en&product=18703](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&dlc=en&docname=c00809678&lc=en&product=18703)

where there are advanced options (scroll 3/4 way down the page in the above link). Then you move on to the restore options which when you start it stops with the error I mentioned before.

---

### Post by Quackers on 2011-10-08
On that advanced options page are you selecting "system recovery"?
If so are there further options after that?

---

### Post by be0562 on 2011-10-09
Sorry made a mistake. That advanced page on mine only has 2 options, so is not as illustrated in the webpage. Computer checkup and system recovery. Computer checkup doesn't do anything.

When clicking system recovery there are then 2 options, yes or no. So I click yes, then the problem as described earlier comes up.

I'll give the tech support a call and see if they can help. Otherwise maybe I'll call HP and they might know a bit more.

---

