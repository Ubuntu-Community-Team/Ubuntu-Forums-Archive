---
title: "[SOLVED] boot loader question"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by chilimac02 on 2008-10-20
I had a windows crash (big surprise with vista). My bootloader stopped working when windows was installed, so I reinstalled Ubuntu. now, I have like 8 different options in the Grub menu for booting Ubuntu. How do I get rid of the ones I don't want up there, or uninstall them?

---

### Post by Elfy on 2008-10-20
Sounds like you have more than one instance of ubuntu installed now all you needed to do was reinstall grub, but we can check that first. Please open a terminal and run these commands - post the outputs here

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

If you've not used sudo yet - it will need your password, it won't appear as you type but it is there.

---

### Post by z.s.tar.gz on 2008-10-20
you need to edit your menu.lst

I don't have the code but if you do 'find -name menu.lst' it should show you where it is.

edit: Yeah, listen to FP, knows more than me.

However, if you ever need to reinstall grub, go to [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Works for me every time

---

### Post by LowSky on 2008-10-20
Editing you menu.lst will not delete the old kernels, that will need to still be done.

To delete old kernels just go to Synaptic and search for them, get rid of all but the 2 most recent. Doing it this way will also auto update grub

---

### Post by chilimac02 on 2008-10-20
justin@justin-linux:~$ sudo fdisk -1 
[sudo] password for justin:  
fdisk: invalid option -- '1' 
 
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table 
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s) 
       fdisk -s PARTITION           Give partition size(s) in blocks 
       fdisk -v                     Give fdisk version 
Here DISK is something like /dev/hdb or /dev/sda 
and PARTITION is something like /dev/hda7 
-u: give Start and End in sector (instead of cylinder) units 
-b 2048: (for certain MO disks) use 2048-byte sectors 
justin@justin-linux:~$ cat /boot/grub/menu.lst 
# menu.lst - See: grub(8), info grub, update-grub(8) 
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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
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
# kopt=root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro 
 
## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,6) 
 
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
 
title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro quiet splash  
initrd		/boot/initrd.img-2.6.27-7-generic 
quiet 
 
title		Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode) 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro  single 
initrd		/boot/initrd.img-2.6.27-7-generic 
 
title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro quiet splash  
initrd		/boot/initrd.img-2.6.24-19-generic 
quiet 
 
title		Ubuntu intrepid (development branch), kernel 2.6.24-19-generic (recovery mode) 
root		(hd0,6) 
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=fab24a9a-cbf7-4be8-8ce6-24f3b288fc80 ro  single 
initrd		/boot/initrd.img-2.6.24-19-generic 
 
title		Ubuntu intrepid (development branch), memtest86+ 
root		(hd0,6) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 
 
# This is a divider, added to separate the menu items below from the Debian 
# ones. 
title		Other operating systems: 
root 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda1 
title		Windows Vista/Longhorn (loader) 
root		(hd0,0) 
savedefault 
makeactive 
chainloader	+1 
 
 
# This entry automatically added by the Debian installer for a non-linux OS 
# on /dev/sda3 
title		Windows Vista/Longhorn (loader) 
root		(hd0,2) 
savedefault 
makeactive 
chainloader	+1 
 
 
# This entry automatically added by the Debian installer for an existing 
# linux installation on /dev/sda5. 
title		Ubuntu hardy (development branch) (8.04) (on /dev/sda5) 
root		(hd0,4) 
kernel		/boot/vmlinuz-2.6.24-12-generic root=/dev/sda5  
savedefault 
boot 




that's a lot of text, but that is what the commands yielded.

---

### Post by Elfy on 2008-10-20
ok - run the first one again please - the l is a L not a 1
To make things like that easier to read use code tags - if you use New Reply there's a button #

or put [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end


Edit - I see you're running intrepid and hardy as well as windows, you might be better to just leave it for the moment - intrepid is a beta release at the moment and could stop working, hardy will continue to work.

---

### Post by chilimac02 on 2008-10-20
it yields:

justin@justin-linux:~$ sudo fdisk -l
[sudo] password for justin: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44ff78b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11027    88574346    7  HPFS/NTFS
/dev/sda2           11028       29324   146970652+   5  Extended
/dev/sda3           29325       30401     8651002+   7  HPFS/NTFS
/dev/sda5           26267       29192    23503063+  83  Linux
/dev/sda6           29193       29324     1060258+  82  Linux swap / Solaris
/dev/sda7           22343       26099    30178039+  83  Linux
/dev/sda8           26100       26266     1341396   82  Linux swap / Solaris
/dev/sda9           11028       21876    87144529+  83  Linux
/dev/sda10          21877       22342     3743113+  82  Linux swap / Solaris

Partition table entries are not in disk order
justin@justin-linux:~$

---

### Post by Elfy on 2008-10-20
Looks to me like you have hardy on sda5, intrepid on sda7 and something else on sda9.

First thing I'd say is that I see you're running intrepid and hardy as well as windows, you might be better to just leave it for the moment - intrepid is a beta release at the moment and could stop working, hardy will continue to work.

But it's up to you what we do - you could lose the last 3 partitions - sda8-10 and reclaim the space.

Editing the menu list will do just that - you'll still have 3 installations of ubuntu on the disc - what do you want to do.

Personally if intrepid is working ok at the moment I'd keep it and one of the hardy's just in case - later you can get rid of the other hardy

---

### Post by chilimac02 on 2008-10-21
how do I remove/uninstall one of the hardy's?

---

### Post by Duck2006 on 2008-10-21
> **chilimac02 said:**
> how do I remove/uninstall one of the hardy's?

Edit your /boot/grub/menu.lst to remove the install that you don't want to show at start-up, Then boot up to the live ubuntu cd and run the partition editer, format the unwanted install and you should be left with the one you want.

---

### Post by chilimac02 on 2008-10-21
hmm... i'm using bootit ng right now to uninstall linux, and remove the partitions.

I'll be reinstalling with a bigger partition later :)

---

