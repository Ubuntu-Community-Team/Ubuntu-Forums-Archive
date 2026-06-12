---
title: "Can a live 12.04 CD be copied onto a flash drive ?"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Innernet on 2013-03-04
I have the 12.04 live CD 700MB; I run 12.04; I have a blank 1GB thumbdrive, flashdrive, pendrive whatever is called.

Will a drag and drop copy make the flashdrive work on a USB boot-enabled machine ?

---

### Post by fantab on 2013-03-04
My guess is NO, it won't work. Why not try and see if it works?

---

### Post by grahammechanical on 2013-03-04
You may find that 1GB is too small for some reason. And it is not enough to copy and paste. We have "burn" the ISO image to the USB drive in a manner similar to "burning" it to the CD/DVD disk.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Regards.

---

### Post by verymadpip on 2013-03-04
My guess is also NO.
Try startup disk creator or UNetbootin.

---

### Post by sudodus on 2013-03-04
> **Innernet said:**
> I have the 12.04 live CD 700MB; I run 12.04; I have a blank 1GB thumbdrive, flashdrive, pendrive whatever is called.

Will a drag and drop copy make the flashdrive work on a USB boot-enabled machine ?

I doubt drag and drop works, but it's worth trying. And please post your result :-D

But you can 'burn' it, actually clone it, using dd and perform low level copying of the block device.

Warning: dd is nick-named 'disk destroyer' because it does what you tell it to do without questions, even if it is stupid, for example to wipe your internal drive or a drive with all your pictures. You must be ***sure*** which is the device letter of your USB pendrive, and you must double-check for typing errrors ;-)

It is straight-forward from an iso file:

```
sudo dd if=live-image.iso of=/dev/sdx bs=4096
``` where x is the device letter of your USB pendrive.
and out of curiosity I tried directly from a CD/DVD like this (in Ubuntu 12.04)
```
sudo dd if=/dev/sr0 of=/dev/sdx bs=4096
``` where x is the device letter of your USB pendrive.
It works :KS (It booted, and I'm checking the drive for errors right now)
*Edit 1*: Check finished: no errors found

*Edit 2*: Not all boot CDs (or their iso files) are bootable from USB drives when cloned, but Ubuntu 10.04 LTS and newer versions and some other distros are. But ***Unetbootin*** can make bootable USB drives from almost all iso files for boot CD/DVD disks.

---

### Post by sanderj on 2013-03-04
> **Innernet said:**
> I have the 12.04 live CD 700MB; I run 12.04; I have a blank 1GB thumbdrive, flashdrive, pendrive whatever is called.

Will a drag and drop copy make the flashdrive work on a USB boot-enabled machine ?

No drag-and-drop, but use usb-creator-gtk instead.

---

### Post by oldfred on 2013-03-04
The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. Or you can use dd.
[URL="http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid"]http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid

[/URL]But I cannot recommend that an average user ever use dd as it can be very dangerous. You copy ISO to wrong place and you have overwritten data in a way that is not recoverable.

If you have dd, then you have Linux and you can directly boot an ISO with grub2's loopmount. I now only install from one hard drive to another hard drive. Or you can use a flash drive.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by Innernet on 2013-03-04
> **fantab said:**
> ...Why not try and see if it works?

Did not copy some files; did not work.  At the end, (about 8 minutes) the folder "Ubuntu" with the link arrow did not copy.  The folder "dists" copied with a larger number of files ¿?  All other folders copied well, show same contents.  Will attempt by other means, but any guidance from you guys, has to be for beguinners, step by step, idiotproof.

---

### Post by audiomick on 2013-03-04
you need to download an .iso.

Then have a look at this
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
to get it on the USB stick.

You may find that it tells you that it wont fit on a 1GB stick. I got an 11.10 to work (or maybe it was 12.04) on a 1GB stick  by disabling the persistance (which it wants  to turn on by default if you use the Ubuntu USB creator) and telling it to ignore all problems. I don't remember exactly, but by "forcing" it, I got it to work.

---

### Post by sudodus on 2013-03-04
> **Innernet said:**
> Did not copy some files; did not work.  At the end, (about 8 minutes) the folder "Ubuntu" with the link arrow did not copy.  The folder "dists" copied with a larger number of files ¿?  All other folders copied well, show same contents.  Will attempt by other means, but any guidance from you guys, has to be for beguinners, step by step, idiotproof.

Be warned about the risks with dd! At 129 beans I dared use it, but it is your choice.

If you want to go the regular and safe way,

- download an iso file and

- make a FAT 32 partition on your USB drive.

- Then use either the ***Ubuntu USB creator*** or ***Unetbootin*** to make your USB drive into an Ubuntu boot drive.

1 GB is enough for a CD iso file, but it is probably not enough for a DVD iso file.

---

