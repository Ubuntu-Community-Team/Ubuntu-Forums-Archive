---
title: "[SOLVED] Grub woes with HD and USB HD"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by ubername on 2008-08-17
Hi, might not be the right place to post 'cos it's not quite Absolute Beginner, but here goes:

I have the following set-up:

Dell E520 with a single hard drive, four partitions, 1 bootable vista, 1 bootable linux (hardy), 1 linux home, and 1 linux swap.
I also have a USB drive (hereafter referred to as 'USB' for convenience)  with three partitions, 1 Linux storage, 1 windows storage and one bootable (supposedly) linux (intrepid).

Gparted tells me that they are assigned as /dev/sda1,2,3,4 respectively for the hard drive and /dev/sdf1,2,3 respectively for the USB.

My problem is that I cannot get the USB to boot (I used to be able to, until recently installing Intrepid upgrades - I know it's development so may not work but it would be nice to fix this). My BIOS is set to boot from 1: CD/DVD 2:USB 3:hard drive. If I have the USB switched on I get the grub menu from /boot/grub of the USB bootable linux partition but selecting linux
(extract from menu.lst)
title		Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.26-4-generic root=UUID=945d356d-ab6b-4f99-8327-3590f57de729 ro quiet splash 
initrd		/boot/initrd.img-2.6.26-4-generic
quiet

from the list I get Error 15: file not found

When selecting the Windows option (from USB menu.lst, pointing to the hard drive):
title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

I get Error 13: Invalid or unsupported executable format

and selecting the Hardy option (from USB menu.lst, pointing to the hard drive)
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7cd1b3db-ac92-4e97-a8aa-7742fa1556d6 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot

I get Error 17: Cannot mount selected partition


I am currently working from the hard drive which boots fine if the USB is switched off at boot, and I can then access the USB by switching it on after boot.

Worryingly this is what I get from fdisk (with the USB switched on)

john@e520:~$ fdisk -l
john@e520:~$ 


i.e. no output


and also from grub

grub> geometry (hd0)
geometry (hd0)

Error 21: Selected disk does not exist
grub> geometry (hd1)
geometry (hd1)

Error 21: Selected disk does not exist
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found


what I would like to be able to do is boot with the USB switched on, and then have the option to select either Intrepid from the USB, Hardy from the hard drive or Vista from the hard drive.


I have checked various threads already but I am struggling here. Can anyone help at all?

TIA

---

### Post by ubername on 2008-08-17
I forgot to mention that I have tried SuperGrubDisk easy switch but to no effect. It still performs as above.

---

### Post by ubername on 2008-08-17
OK, discovered you need to sudo fdisk.

Here's the output

john@e520:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9289    74609375    7  HPFS/NTFS
/dev/sda2            9290       10504     9759487+  83  Linux
/dev/sda3           10505       19330    70894845   83  Linux
/dev/sda4           19331       19452      979965   82  Linux swap / Solaris

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007a3e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       12803   102840066   83  Linux
/dev/sdf2           12804       31040   146488702+   7  HPFS/NTFS
/dev/sdf3           31041       38913    63239872+  83  Linux

---

### Post by ratthing on 2008-08-17
My first instinct would be to say that you need to make sure grub is only installed on one disk--the internal one.  Having two active partitions means that the computer doesn't know which one to use as the initial boot disk.  Hence it does one thing with the USB disk on and another with the USB disk off.

Using Windows, the common ways to remove grub are "fixmbr" or "fdisk /mbr".  On Linux, I think you just need to:
[LIST=1]
[*]set the USB disk's partitions to inactive (using fdisk or gparted, etc).  This is the key to resolve the confusion caused by multiple active partitions.
[*]mount the USB disk's partition where the grub menu is at and merge the info that's there into the grub menu that's on your internal hard drive.
[/LIST]

HTH--
=RT=

---

### Post by caljohnsmith on 2008-08-17
Those errors you got trying to do "geometry" and such in grub are because you have to run grub as root, just like fdisk. :)

> **ubername said:**
> If I have the USB switched on I get the grub menu from /boot/grub of the USB bootable linux partition but selecting linux
Well if you are truly booting from your USB, I think your only problem is Grub will see that USB as the first HDD. 
```
title Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root [COLOR="Blue"](hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.26-4-generic root=UUID=945d356d-ab6b-4f99-8327-3590f57de729 ro quiet splash
initrd /boot/initrd.img-2.6.26-4-generic
quiet
```
You have (hd1,2) right now, which is 2nd disk, 3rd partition. I believe that should instead be (hd0,2) if your Intrepid is truly on your 3rd partition. But according to your fdisk output, your 1st partition is the bootable one; therefore you might need (hd0,0) instead. I would just copy/paste both those into your menu.lst, try them and find which works. Or alternatively, on startup, if you select the Intrepid entry in Grub, hit "e" to edit it, you can edit the line that says "root hd1,2)" to instead use (hd0,2) or (hd0,0) and find which works that way.

If the above works, then the same would be true with your Hardy partition: you would have to use (hd1,1) instead of (hd0,1). Windows will be a different matter though as it will require mapping, but let me know if the above works first.

---

### Post by linux_tech on 2008-08-17
Sounds like the option to boot to usb became unusable after running the intrepid upgrade? 

Clarification- 
USB is functional but you can't boot to it- 
Bios has option to boot to removable media and this option is before 
boot to hd in boot order

usb modules likely changed after intrepid upgrade

Recovering grub would be a good bet.
redetecting all usb would also be good

My suggestion is to reinstall/recover grub- directions here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+repair)

if necessary run a script to auto-detect all USB modules and add them
to the initial ramdisk
[http://www.linuxfromscratch.org/hints/downloads/files/initrd-diskcheck.txt](http://www.linuxfromscratch.org/hints/downloads/files/initrd-diskcheck.txt)

---

### Post by ubername on 2008-08-17
> **caljohnsmith said:**
> Those errors you got trying to do "geometry" and such in grub are because you have to run grub as root, just like fdisk. :)


Well if you are truly booting from your USB, I think your only problem is Grub will see that USB as the first HDD. 
```
title Ubuntu intrepid (development branch), kernel 2.6.26-4-generic
root [COLOR="Blue"](hd1,2)[/COLOR]
kernel /boot/vmlinuz-2.6.26-4-generic root=UUID=945d356d-ab6b-4f99-8327-3590f57de729 ro quiet splash
initrd /boot/initrd.img-2.6.26-4-generic
quiet
```
You have (hd1,2) right now, which is 2nd disk, 3rd partition. I believe that should instead be (hd0,2) if your Intrepid is truly on your 3rd partition. But according to your fdisk output, your 1st partition is the bootable one; therefore you might need (hd0,0) instead. I would just copy/paste both those into your menu.lst, try them and find which works. Or alternatively, on startup, if you select the Intrepid entry in Grub, hit "e" to edit it, you can edit the line that says "root hd1,2)" to instead use (hd0,2) or (hd0,0) and find which works that way.

If the above works, then the same would be true with your Hardy partition: you would have to use (hd1,1) instead of (hd0,1). Windows will be a different matter though as it will require mapping, but let me know if the above works first.

Fab! Brill! Excellent!

I am now running from the Intrepid on USB having used 'e' in grub to edit the root location.

(hd0,2) does the trick. Great thinking, thanks so much. I shall now spend some time making it permanent and figuring out the  hardy and windows bit.

---

### Post by caljohnsmith on 2008-08-17
If it will save you some time, I think you would boot your Windows using:
```
title Windows Vista/Longhorn (loader)
root [COLOR="Blue"](hd1,0)[/COLOR]
makeactive
[COLOR="Blue"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader +1
```
Maybe you've all ready got it figured out though. :)

---

### Post by ubername on 2008-08-17
> **caljohnsmith said:**
> If it will save you some time, I think you would boot your Windows using:
```
title Windows Vista/Longhorn (loader)
root [COLOR="Blue"](hd1,0)[/COLOR]
makeactive
[COLOR="Blue"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader +1
```
Maybe you've all ready got it figured out though. :)

All done without re-mapping. I simply changed the hd1 to hd0 for USB intrepid, and the hd0 for hd1 for Windows and hardy on the HD. (Posting from hardy on hd1 (as it were) having booted from the grub menu.lst on USB as I speak) Tested Vista and it works too! Now to work on the menu.lst on the HD. Thanks again.

---

### Post by ubername on 2008-08-17
Just realised: I won't ever need to boot from my USB drive if it is switched off (i.e. I am seeing the grub menu from my HD)!

---

