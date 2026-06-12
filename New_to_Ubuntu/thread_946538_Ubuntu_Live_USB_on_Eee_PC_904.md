---
title: "Ubuntu Live USB on Eee PC 904"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by SuperNapalm on 2008-10-13
Okay so before I nabbed myself an Eee for work (and occasional play since i know the eees can run one or two) I decided to go with Ubuntu.

I bought a USB memory stick (an Integral 4gb to be precise) and used the unetbootin utility on Windows to write the 8.04.1 disk image (which checks out fine btw). When I attempt to load it on my main desktop it loads fine with no problem but when I try to load it on my Eee it hangs during loading.

Anything I can do to solve this? It's also worth mentioning that the USB had 2 drives/partitions or whatever, one had 3.77gb, the other like around 5mb. That's probably where my problem lies but i don't want to screw around with it until i get some outside help.

Cheers for any info :)

EDIT: Also, the USB is FAT32 formatted

---

### Post by C.S.Cameron on 2008-10-13
I had to adjust BIOS on my EEE to boot from Flash Drive.
In bios go to boot, hard disk drives and select the memory stick as the first HDD.

---

