---
title: "Promise SX4000 woes v2"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Huzudra on 2008-09-06
[http://ubuntuforums.org/showthread.php?t=253839](http://ubuntuforums.org/showthread.php?t=253839)
as an update to this thread above...

the card actually DOES work, works in my dell box with the plain jane intel board just fine...drive recognizes, ram recognizes, etc.


however i have no bleeding clue how to get anywhere with it in ubuntu, it sort of looks like theres no driver for it?  or has someone made some inroads?  i'd like to use it since it gives me 4 more IDE channels when not in raid mode.


otherwise, i still do have the CMD IDE controller around that gives me 2 more channels.  i'll probably use that, its a CMD 649U, does it get along well with 8.04?  i'd rather not dual boot just to get access to my files.  my main PC doesnt have a free PCI slot (that doesnt block something) and has only one IDE channel.  also, i need to re-learn samba sharing for when i help others with things, what better way to learn than to force yourself?

ok, i put in the other card but i  have no idea what i need to do to recognize the hard drive in linux.  i only have ONE hard drive mounted, in the past in multiple hard drive systems they all mounted automatically.  which makes me think theres a problem with something.

---

### Post by Huzudra on 2008-09-07
ok, that other ide controller is exactly a 

SiI 0649 Ultra ATA/100 PCI to ATA Host Controller


as per lspci (i'm learning).


so uh, it worked back in the day on 6.06 xubuntu i think...but now in 8.04 i got nothing. i've never had a device NOT just work in ubuntu. i plug it in, turn the system on, log in, it says it found something, enter your password, tick this box, and it works now.  

but nothing now, i know that bios sees the card, that at some level linux sees the card, but my drive attached to it is no where to be found!  cant see it in the partition editor.

drive is also NOT listed when i sudo fdisk -l

---

### Post by Huzudra on 2008-09-12
**Bump?**  any ideas guys/gals?

---

### Post by Huzudra on 2008-09-27
nothing?

---

### Post by Huzudra on 2008-10-11
since i was going no where fast with the card, i just pulled it from the system. maybe its not compatible with the dell board?  come to think of it, i dont remember seeing the cards bios come up.

---

### Post by husindo on 2009-11-25
*buuump :-)*


Hello Huzudra,

all solutions i was able to find are [http://majestic.lugh.de/promise/kernel-2.6/](http://majestic.lugh.de/promise/kernel-2.6/) , and im also not able to get this Card working, but i think its because of actually using x86_64.
Regarding 32bit-architecture I would suggest you to follow the manual on [http://www.lugh.de/promise/](http://www.lugh.de/promise/) (beginning with " user@host#> tar xvfz promisesx4000.tar.gz ", and using the files from [http://majestic.lugh.de/promise/kernel-2.6/sx4_partial_src.tar-kernel-2.6.tar.gz](http://majestic.lugh.de/promise/kernel-2.6/sx4_partial_src.tar-kernel-2.6.tar.gz), or  [http://majestic.lugh.de/promise/sx4000_v2.zip](http://majestic.lugh.de/promise/sx4000_v2.zip))


** Now to my problem (which I think is x64 related):**
Trying to setup an my old RaidCard Promise-SX4000 for backup-purposes, i also tried to follow the HowTo on [http://www.lugh.de/promise/](http://www.lugh.de/promise/) (also with [http://majestic.lugh.de/promise/sx4000_v2.zip](http://majestic.lugh.de/promise/sx4000_v2.zip) ), but got problems because of having x86_64 GNU/Linux 2.6.31-14-generic #48-Ubuntu i think.
Even after manually changing both Strings "-march=$(ARCH)" in the Makefile to "-march=i686" i get following errors:
.
root@localhorst:~/sx4000/FastTrak-partial-b24# make
[: 1: -lt: unexpected operator
[: 1: -lt: unexpected operator
kernel version:  
gcc -c -O2 -fomit-frame-pointer -D__KERNEL__ -DMODULE -D__LINUX__ -Wall -Wstrict-prototypes -fno-strict-aliasing -Wno-unused -pipe -DXH_BSL -D_PBM_ -DENABLE_PRIVATE_DEBUGGING -D_SUPPORTENCLOSURE_ -I/lib/modules/2.6.31-14-generic/build/include -I/lib/modules/2.6.31-14-generic/build/drivers/scsi -D__SMP__ -march=i686 -mpreferred-stack-boundary=2  -o wrapper.o wrapper.c
wrapper.c:1: error: CPU you selected does not support x86-64 instruction set
wrapper.c:1: error: -mpreferred-stack-boundary=2 is not between 4 and 12
make: *** [wrapper.o] Error 1
root@localhorst:~/sx4000/FastTrak-partial-b24# 
.


I also managed to install ptisxutils-1.30.0-51.i386.rpm with --force-architecture, but "msgagt start" gives me following error:
.
Starting msgagt services: [ OK ]-ne 
/usr/sbin/msgagt: 283: msgagtd: not found
.
But ls -l /usr/sbin/msgagtd shows: -rwxr-xr-x 1 root root 185798 2004-08-07 00:42 /usr/sbin/msgagtd
I think because of lspci | grep Promise
01:06.0 RAID bus controller: Promise Technology, Inc. PDC20621 (FastTrak S150 SX4/FastTrak SX4000 lite) (rev 01)
shows the wrong (light?) module loaded for the SX4000 ?
[B]
If anybody has sugestions how to get this compiled under x86_64 - architecture, please give me a bit help![/B] 
Since i would like to use this card with a bunch of 500GiB disks (afaik these are the largest which get regonized by the bios) in a Raid5 as backup-space for an existing raid it would make me very happy to be able to use this "old and under windows2k ever stable running baby" in the linux-world :-)


_Edit for Mods:_
Why not merging this Thread to the end of Thread [http://ubuntuforums.org/showthread.php?t=253839](http://ubuntuforums.org/showthread.php?t=253839) and move the result to a better forum like "Hardware & Lapops", or even "[x86 64-bit Users]("http://ubuntuforums.org/forumdisplay.php?f=343")" :D

---

