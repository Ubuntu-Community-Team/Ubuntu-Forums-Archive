---
title: "Ubuntu 9.2 Grub is empty cannot login"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by protocoder on 2012-04-21
Hello Experts,
I had the windows xp Dell D610 which I made a partition of 20 gb for Ubuntu with Grub to allow me to login .. Every thing was fine, except that I had too many broken applications in Ubuntu and I have added the applications I could find, now I tries to remove some the application from Synaptic Manager, marked for complete removal and suddenly I noticed that system was unresponsive. so I restarted the Ubuntu and I only find Memory Test in the Grub, I cannot even enter windows. 

1. Please can you help me restore grub to ensure I can login to my windows.
2. To help me to upgrade Ubuntu to latest versions, or as if you advice me move lunux Mint as you advice. Any help would be appreciated. 
3. In order not to get into this situation please tell me few tips.

Here is the current status:
I get GNU GRUB version 1.97 beta
with 
Memory test (metest86+)
Memory test(memtest86+,serial console 115200)

and the rest of the login information is gone .. 
I can go to shell grub mode by pressing C. 

I ran help there and whole list is shown .. tried a few commands Login, windows .. etc but no use. 

PS: Please give me the links of the creating a USB ISO if I need to stick one to get back to normal state. treat me as completely new to Ubuntu.

Regards and Thanks in Advance
Anand

---

### Post by Baldrick_NZ on 2012-04-22
Hi Anand & welcome aboard!

First we'll need to know which version of Ubuntu you're actually using. You said 9.2, but there was no 9.2 version. If it was 9.04 or 9.1, then both are outdated and now obsolete.

It should be either 10.04, 11.04, 11.10 or maybe 12.04.

Cheers.

---

### Post by Silent Sam on 2012-04-22
If your careless in Synaptics you could accidentally delete essential packages your computer needs to boot. I did this earlier today and had to reinstall Ubuntu and upgrade back to Oneric (which is what I'm doing right now). If you didn't delete anything essential and this is just some weird glitch you could try using a boot CD (any one will do), opening a terminal and entering:
```
sudo update-grub
```This should auto-detect any operating systems on your computer.

Hope this helps.

PS.
you may have to run
```
sudo apt-get install grub
```Some boot CDs (like mine) dont have the grub commands included in the live CDs.

If this doesn't work then, I'm sorry. Your going to have to start over again from a clean install.

---

### Post by protocoder on 2012-04-22
Thank you very much Baldrick_NZ (Kia Ora) and Silent Sam.
Unfortunately I cannot confirm to you now .. I think it was karmic koala ..9.10 ..Sorry I should have mentioned it. I am completely new still to linux .. I successfully made partition using gparted, deleted the usb contents after I am done which is a big mistake.. and landed in this trouble .. I never knew that we could delete packages from synaptic which can lead to this. Any help to this new comer will be appreciated. Long way to learn. thanks in advance
Anand

---

### Post by protocoder on 2012-04-22
Here is the update. I created USB Ubuntu 9.10 drive and installed from USB.
 
I have tried the commands 
sudo update-grub - -DID NOT WORK then I tried
sudo apt-get install grub

It did not work as there my wireless connectivity is gone. I tried to connect with wired to the ethernet hub, but eth0 kept searching and did not find any. I remember my struggle to get the NDISwrapper and how I got the net connectivity on ubuntu earlier. 
Please suggest me any easier ways to do it. Thank you.

Note: I tried to install Ubuntu again, received the message that I already have Ubuntu installed, I did not want to mess up anything without advice. 

2. To Fix my Grub issues so that I can use my laptop as before, I tried the following command 
sudo fdisk -l to mount the drive. 
I am now confused as I have two drives of linux 
/dev/sda5 2570 4762 17615241 83 Linux
/dev/sda6 4763 4864 819283+ 82 Linux Swap / Solaris

I am guessing i should mount /dev/sda5 and tried the command
I get the following error 

mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab Please advice.

Did a lot of files got messed up while I was deleted application from synaptic manager ?

What is the best way to proceed.. Ultimately I want to upgrade Ubuntu as well to either latest or Mint as you suggest .. some say Mint is very good and others have different opinion. Looking for direction to bring my laptop to working mode with latest version.

As suggested in earlier posts, I have run the bootinfoscript and this is output "results.txt"

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => No known boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 9.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.86 2010-04-01
    Boot sector info:  Syslinux looks at sector 2568 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa5caa5ca

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    41,270,984    41,270,922   7 NTFS / exFAT / HPFS
/dev/sda2          41,270,985    78,140,159    36,869,175   5 Extended
/dev/sda5          41,271,048    76,501,529    35,230,482  83 Linux
/dev/sda6          76,501,593    78,140,159     1,638,567  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2021 MB, 2021654528 bytes
255 heads, 63 sectors/track, 245 cylinders, total 3948544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04dd5721

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,948,543     3,948,481   6 FAT16


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x58a22b45

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   156,296,384   156,296,322   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        0E28901B289003BD                       ntfs       
/dev/sda5        7d05bb88-15be-4298-b32e-20c9199beb23   ext4       
/dev/sda6        27b7a8d7-7b2e-4a24-8176-ac4d11f7ee21   swap       
/dev/sdb1        EC97-C426                              vfat       PENDRIVE
/dev/sdc1        4139-F3DE                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/0E28901B289003BD  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /media/7d05bb88-15be-4298-b32e-20c9199beb23 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/sdc1        /media/4139-F3DE         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/ PC Suite         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 7d05bb88-15be-4298-b32e-20c9199beb23
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7d05bb88-15be-4298-b32e-20c9199beb23 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=27b7a8d7-7b2e-4a24-8176-ac4d11f7ee21 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  cb 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  45 2b a2 58 00 00 00 01  |........E+.X....|
000001c0  01 00 0c fe ff ff 3f 00  00 00 82 e4 50 09 00 00  |......?.....P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


Any help would be appreciated.

Thanks a Ton
Anand

---

### Post by wildmanne39 on 2012-04-22
Hi, as stated 9.10 it is out dated even if you get it to work you will not be able to install updates for security or other applications because they have been removed from the server and you  will not be able to easily upgrade 9.10 to a later version it is best to install at least 10.04.
Thanks

---

### Post by protocoder on 2012-04-23
Thank you wildmanne39
I anyways wanted to upgrade now my question what version is the best .. how about Mint. 

1. How to upgrade from my current situation
2. If I have to reinstall any other version or even same version It goes to partition section where it recognizes there is already linux installed ..Please advise. I have to be careful so that my windows partition is not disturbed. .Is there a way I can completely clean (format ubuntu installed) and start afresh with Mint or whatever version experts here advice. Please give me step by step commands and bear with me as I am just a starter.

Thanks in Advance
Anand

---

### Post by wildmanne39 on 2012-04-23
Hi, I hear mint is good but I have never used it, I am going to give you a link or maybe 2 to help you with your questions.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://members.iinet.net.au/~herman546/p25.html#Gnome_Partition_Editor](http://members.iinet.net.au/~herman546/p25.html#Gnome_Partition_Editor)

You can go with any version from 10.04 up and 12.04 will be out in 3 days but I recommend 12.04 it will have a nice classic mode in case you do not like the new desktop.

To use the same partition when it asks to partition select manual or something else depending on the version of ubuntu you install then delete and reformat the partitions that already have linux on them and create new ones.
Thanks

---

### Post by audiomick on 2012-04-23
> **wildmanne39 said:**
> ... select manual or something else depending on the version of ubuntu you install then delete and reformat the partitions that already have linux on them and create new ones.
Thanks
You don't actually have to delete the existing partitions. Just select the mount point an choose to format them. You only have to change them if you want a different size.

---

### Post by protocoder on 2012-04-23
Hello wildmanne39 and audiomick

Thank you very much. Please can you put them in commands so that beginner can use them without touching the partition where I have windows, that would be great, I am worried anything wrong from me I would loose windows esp when I have rescue cd.

Is there a way I can format entire partition other than where I have windows and can make my system windows with partition in tact so that based on reviews and your advice I can use what ever is the latest updates. 

A step by step commands based on my partition information pasted below will help me as a beginner.

Thanks in Advance
Anand

---

### Post by audiomick on 2012-04-23
No partition info in that post, but that doesn't matter for now.

You should have a look at the partitions with Gparted.

Your best bet is probably to boot from a live CD / USB and do it from there. You can't work on a partition that is mounted, so if you boot from the installed Linux, you wont be able to work on the partitions without unmounting them. I believe you can't boot the installed Linux anyway, so a live CD is the easiest anyway. If you don't have an Ubuntu CD, you could also burn a Gparted CD-

I wanted to give you a link to the Gparted site, but I can't get to there right now for some reason, so here is the Wikipedia Article, which has a link at the bottom. If that doesn't work, get an Ubuntu ISO and burn that. It is on there too.

Look at your drive with Gparted. It is pretty obvious which partition it the Windows one. Anything that is NTFS  or FAT32 is windows. Linux partitions will be something else. Just don't touch the windows partitions.

---

### Post by wildmanne39 on 2012-04-23
Hi, here is a link for gparted.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Thanks

---

### Post by audiomick on 2012-04-23
Thanks for that. I could only find one at Sourceforge that came up with a blank page.

---

### Post by wildmanne39 on 2012-04-23
Hi audiomick, your welcome!

---

### Post by protocoder on 2012-04-24
Thank you wildmanne39 and audiomick.

Sorry still bit confused. Yes I do have the Ubuntu9.10 on the USB stick and I was able to boot it, In fact I tried to re-install and it was looking for space and took me to the partition. That's where I got scared and cancelled. I do not want to mess up anything more. The partition information is in the first page of my post, Is this information help me getting the command to unmount complete Ubuntu and format it so that I can use my system as windows bootable leaving the partition as it is. Then based on advice, I will install the relevant os.

sda1: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows XP: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP
Boot files: /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________ ________________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 9.10
Boot files: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info: 

As I see sda5 is linux and sda6 is linux swap. 

I tried to mount and unmount these drives but failed. I received this error 
mount: can't find /dev/sda5/mnt in /etc/fstab or /etc/mtab

In short I am looking for the following for immediate purpose.

1. Completely format the Ubuntu 9.10 stuff and ensure system boots with Windows like previously leaving aside the partition I have made keeping in mind that I can only boot from the USB.

Any help would be appreciated.
Note: I am not able to access Internet both via ethernet or wireless to upgrade grub.

Thanks a Ton.
Anand

---

### Post by audiomick on 2012-04-24
Ok, first of all, if you can get a USB stick with a newer Ubuntu on it organised, you should do so. 9.10 is out dated. Having said that, it will still work, of course. If you can't get a newer one right now, install that and download a newer ISO later on when you have your computer up and running. If you decide to do that, then this install is only temporary, so don't spend too much time customising it or anything. Just use it long enough to sort out your other problems and get the new ISO, then install again. 

It looks like you are nervous about working on your partitions. If you haven't already, look at the links that wildmanne39 posted in post #8, and have a look at these as well.
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")
Particularly, the link on the "how to partition" page about partitioning basics. That explains about Primary, Extended and Logical partitions, which is relevant to you.

As far as I can see, you have your windows install, hopefully intact, on sda1.
Sda2 is an extended partition with two logical partitions in it, one of which will have been your system partition for ubuntu, and one of which is a Linux swap partition.

The absolute simplest way to go would be to choose the "manual" option when the installer gets to the partitioning stage and simply re-use those partitions. You just have to choose a mount point and tell it whether it needs to format or not.

Note: on 9.10 it is the "manual" option. On newer versions, it is called "something else". The other options are things like "use the whole disk" and "install beside windows".

So, choose the mount point / for sda 5 and tell it to format.
Choose the mount point "swap" for sda6. I don't remember if it will let you re-format an existing swap partition that is being re-used as a swap. Doesn't matter much. If it does, then re-format it for the sake of it, if not, don't worry.

Let it do it's business, and it should install 9.10 fresh into the partitions you already have and set up grub new so that it finds the windows and the Ubuntu install.

When you get around to re-installing a newer version, give some thought to creating an additional partition for /home. The advantage in that is that if you should find yourself in a similar situation in the future, and have a nicely set up Ubuntu that you want to get back to, you can simply re-mount the existing /home in the new install with all your data and config files in it.


I should perhaps mention that it may well be possible to save the system without a new install, but going by what you wrote in earlier post, I gather the ubuntu is probably messed up over and above the problem with GRUB which is stopping you from booting it. I think re-installing is probably the easiest option.

---

### Post by protocoder on 2012-04-25
Hello Audiomick and wildmanne39,
Thanks a ton.
Thank you for the encouragement.I was scared when I got "no root file system is defined". I should have searched for that error and followed that line. Instead I was thinking I did terribly wrong in deleting the files. I got the confidence after your messages and changed the to tackle the error after choose the partition followed this [http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu](http://askubuntu.com/questions/80455/no-root-file-system-defined-error-while-installing-ubuntu) and I got Ubuntu installed, Grub is back and running and windows is good .. 
Next steps:

Only thing I need to get my Ethernet and Wireless up and running which I struggled the first time. That probably is next challenge. 

I know this is Ubuntu forum but if Linux Mint new release couple days back is good, as I hear issues with unity of Ubuntu, I will probably choose that and now I know what to do .. Thanks to you all. .awesome forum. 

I have marked this thread as solved but if you have any Opinion/Recommendation if Linux Mint, I would like to hear.

Thanks a ton again.
Anand

---

### Post by wildmanne39 on 2012-04-25
Hi, I am glad you got it going, what version did you install?
Thanks

---

### Post by protocoder on 2012-04-25
Hi wildmanne39 Thank a lot.
I had a readily available 9.10 from last install and used it. I think I need to repeat this exercise with the latest version. Please suggest me should I go for new linux mint launched couple days back or Ubuntu with unity, the reviews are scary. I need some recommendations. Please advice. Thanks a Ton. But I think I now know how to re-install atleast thanks to you.

---

### Post by wildmanne39 on 2012-04-25
Hi, it is your preference, with mint it will install all the extras that you need like wireless and codecs to play movies,  but I like ubuntu.
Thanks

---

