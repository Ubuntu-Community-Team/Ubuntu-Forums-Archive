---
title: "Filesystem  up by &#8220;Suspend&#8221;? GRUB Error 17 again"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by olhat on 2008-09-29
After many tries and long googling I found out that some of my USB stuff might stop &#8220;Suspend&#8221; from working.  So I removed all my USB devices and  wow! &#8220;suspend&#8221; suspended the computer.  And then the wake-up click (or something, anybody's guess, else) *<snip>* up my Linux OS filesystem, AGAIN.  

The hdd starts and then I can read the stage 1.5 and error 17 screen.

When I type
&#8220;sudo fdisk l&#8221; 
I get this 
&#8220;Unable to open l&#8221;.  
How should I interpret this?

---

### Post by Malta paul on 2008-09-29
give sudo fdisk -l a try:D

---

### Post by bumanie on 2008-09-29
As said above it is sudo fdisk -l, but grub error 17 is usally fixed by reinstalling grub via the live cd. Follow [this thread ]("http://ubuntuforums.org/showthread.php?t=224351")to reinstall grub.

---

### Post by olhat on 2008-09-30
> **bumanie said:**
> As said above it is sudo fdisk -l, but grub error 17 is usally fixed by reinstalling grub via the live cd. Follow [this thread ]("http://ubuntuforums.org/showthread.php?t=224351")to reinstall grub.



Because the FAT, MBR or sth similar is XXXXed up by the "Suspend" button in the Logoff window I can NOT mount the hd with Ubuntu CD.  GParted can see the harddrive and partitions, Diskinternals Linux recovery can pick thousands of picturefiles from this harddrive but I would like to retrieve the OS unchanged if possible.



olhat@nyl:~$ sudo fdisk l
Unable to open l




ubuntu@ubuntu:~$ sudo fdisk /dev/hda

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)









grub> sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57f5bc26

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            1786        4865    24740100    f  W95 Ext'd (LBA)
/dev/hda5            1786        4732    23671746   83  Linux
/dev/hda6            4733        4865     1068291   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 




root (hd0,x) where x = the the # of the root partition minus 1 (grub starts counting from 0)

setup (hd0)

quit



grub> root (hd0,4)
root (hd0,4)
grub>         
grub> setup (hd0,4)
setup (hd0,4)

Error 17: Cannot mount selected partition
 The same goes for (hd0,5) too.

---

### Post by unutbu on 2008-09-30
Try plugging in all the USB drives you usually have plugged in, and then reboot.

The presence of other drives can affect the GRUB numbering, (hdX,Y), for your Linux partition.

If that does not work, please tell us if you are getting the GRUB Error 17 before you can get to the GRUB menu, or only after. And also please post your menu.lst.

---

### Post by olhat on 2008-09-30
> **unutbu said:**
> Try plugging in all the USB drives you usually have plugged in, and then reboot.

The presence of other drives can affect the GRUB numbering, (hdX,Y), for your Linux partition.

If that does not work, please tell us if you are getting the GRUB Error 17 before you can get to the GRUB menu, or only after. And also please post your menu.lst.



Thanks for your suggestions!  No help though.

I have tried with and without USB drives. Makes no difference.

Tried with several hdd settings. Makes no difference


When powering on immediately after BIOS the short hyphen blinks for a few seconds and then I get the doing 1.5 line and Error 17.  I never see the GRUB menu.


sudo gedit /dev/hda5/boot/grub/menu.lst  gives sudo gedit /dev/hda5/boot/grub/menu.lst

** (gedit:9311): WARNING **: Hit unhandled case 19 (Not a directory) in gedit_io_loading_error_message_area_new.

Could not open the file /dev/hda5/boot/grub/menu.lst. Unexpected error. Not a directory.


I can't mount the hda drive at all though it can be mounted through Windows and gparted shows the keyring on this hda5 and extended hda2.

This attached menu.lst file is from the sda drive that is a previously taken mirror image of the hda drive.  Maybe it can give some hints.





&#65279;# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$xxx/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=198c978f-bd33-40c5-8d6f-026ea32f1a47 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=198c978f-bd33-40c5-8d6f-026ea32f1a47 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=198c978f-bd33-40c5-8d6f-026ea32f1a47 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by unutbu on 2008-10-01
Okay, it sounds like boot process is getting to stage 1.5, and then failing when GRUB tries to mount the Linux partition:
> 
Error 17: Cannot mount selected partition

Perhaps the suspend somehow corrupted the filesystem. (Maybe a file was supposed to be written to disk before the suspend, but the suspend script failed to sync the hard disk.)
This could be wrong, it's just a conjecture.

However, since it looks like the machine is failing to mount the filesystem,
perhaps try
```

sudo e2fsck -pv /dev/hda5
```

---

### Post by olhat on 2008-10-05
> **unutbu said:**
> Okay, it sounds like boot process is getting to stage 1.5, and then failing when GRUB tries to mount the Linux partition:


Perhaps the suspend somehow corrupted the filesystem. (Maybe a file was supposed to be written to disk before the suspend, but the suspend script failed to sync the hard disk.)
This could be wrong, it's just a conjecture.

However, since it looks like the machine is failing to mount the filesystem,
perhaps try
```

sudo e2fsck -pv /dev/hda5
```



Latest suggestion was too late.  I already had lost my patience with this can of bugs and reinstalled the OS.  We'll see how many days it takes 'til I hit the next snaFU system-non-bootY.:tongue:

---

### Post by caljohnsmith on 2008-10-05
If you are using a AMD64 processor, there is a known bug where you can get a Grub error 17 after a suspend or hibernate because of a file system corruption, but fortunately there is a solution:

[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Does that apply to you?

---

### Post by olhat on 2008-10-07
> **caljohnsmith said:**
> If you are using a AMD64 processor, there is a known bug where you can get a Grub error 17 after a suspend or hibernate because of a file system corruption, but fortunately there is a solution:

[http://ubuntuforums.org/showthread.php?t=927831](http://ubuntuforums.org/showthread.php?t=927831)

Does that apply to you?


It might apply to me since I have quite identical hardware setup with that one.  My old 64xtwo processor I bought over four years ago and the architecture hasn't changed since, I thinks.  This current one I bought last spring and the only practical differences between these two are probably the close to tenfold drop in price and a bigger cache.  But for how many years can this kind of a bug hang around unfixed.

I dare not touch the suspend or hibernate buttons til I have made a new mirror image of my latest install and drunk a gallon of liquid courage.

---

