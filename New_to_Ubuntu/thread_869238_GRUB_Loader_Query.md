---
title: "GRUB Loader Query"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by CosmicFlux on 2008-07-24
Hey,

OK, I have a dual-boot, dual-hard drive system. The main drive is SATA and the other is configured as master on the primary IDE channel. On the SATA drive I have Vista and Ubuntu and on the IDE drive I have MS-DOS 7.10. I've added MS-DOS to the loader using:

title        MS-DOS 7.10
root        (hd1,0)
savedefault
makeactive
chainloader  +1

The thing is, it wont boot into DOS. I get the message 'Starting Up..." and then the system hangs. 

What am I doing wrong?


CosmicFlux

---

### Post by coffeecat on 2008-07-24
I think I've [found the explanation for you]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows").

> GRUB cannot boot DOS or Windows directly, so you must chain-load them (see [Chain-loading]("http://www.gnu.org/software/grub/manual/grub.html#Chain_002dloading")). However, their boot loaders have some critical deficiencies, so it may not work to just chain-load them. To overcome the problems, GRUB provides you with two helper functions.     If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command map (see [map]("http://www.gnu.org/software/grub/manual/grub.html#map")), like this:  
     grub> map (hd0) (hd1)
     grub> map (hd1) (hd0)
   This performs a virtual swap between your first and second hard drive.
The map commands in the quote are as typed into a grub prompt. To put them into menu.lst, I think you'll have to do:


```
title        MS-DOS 7.10
map        (hd0) (hd1)
map        (hd1) (hd0)
root        (hd0,0)
savedefault
makeactive
chainloader  +1
```
With the root changed to (hd0,0) because grub has to be fooled into thinking the slave drive is the master drive. At least I think that's correct. I've never done this for myself. Let us know how you get on. :)

---

### Post by CosmicFlux on 2008-07-25
Hey,

Thanks for the information. It didn't work, nor did chain-loading. It did, however, give me an idea. I tried hiding the primary drive, like this:

title     MS-DOS 7.10
hide      (hd0,0)
unhide    (hd1,0)
map       (hd0) (hd1)
map       (hd1) (hd0)
root      (hd1,0)
makeactive
chainloader +1


And it worked! I now have a GRUB menu containing Ubuntu, Vista and DOS and I can boot directly into all three.


Thanks!


Cosmic

---

