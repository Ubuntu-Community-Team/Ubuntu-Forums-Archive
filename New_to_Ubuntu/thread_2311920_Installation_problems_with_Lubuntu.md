---
title: "Installation problems with Lubuntu"
date: 2016-01-31
forum: New to Ubuntu
---

### Post by dh72rNedel on 2016-01-31
SO a little background:
Wiped hard drive clean, repartitioned as Fat32/exFat MBR, Tried to install Lubuntu 64 multiple times, reinstalled, used different flash drives (anywhere between 1-16GB they were newly formatted as FAT32/exFat as well), settled for Lubuntu 32 which worked on the first try (On my 2GB flash drive); messing around with it for a little bit and I just now want to fix this Lubuntu 64 issue I have no idea why it keeps getting stuck and I have deep googled and tried/read many things; anyway so here I am....

TL;DR:
Trying to install Lubuntu64 onto an old Gateway T1628 (runs AMD64x2) and I boot all the way to:
Media test failure, check cable
Exiting PXE
Then it boots Lubuntu32

The only other thing I have tried other than what I posted already, is to reinstall and update the grub to no avail. I'm not well versed into what else I should post, but if you should need more information I will try and get it posted ASAP, thanks!

---

### Post by Vladlenin5000 on 2016-01-31
Hi and welcome.

First things first: FAT32 is what you need; exFAT is what you should avoid at all times. And most tools available to create the USB installation media will reformat it anyway (to FAT32) but when they don't weird things may happen.
That said, a 64-bit OS can run on your system but it won't work better than 32-bit unless you have more than 2GB of RAM. How much RAM do you have?

---

### Post by dh72rNedel on 2016-01-31
3 GB.. the 2GB flash drive I had my Lubuntu 64 iso is formatted FAT32; I can't remember but I think I did make at least one of the flash drives exFAT formatted.

---

### Post by Vladlenin5000 on 2016-01-31
1. 64-bit, nothing else.
2. Yes, format to FAT32 -and- use a proper tool; if using Windows then Rufus.

---

### Post by dh72rNedel on 2016-01-31
Okay, downloaded rufus and I'll reformat and try to install again and let you know what happens. Thanks for the quick replies!



Amazing. I'd been scouring the internet for hours trying to fix this before making and account and it took all of 5 minutes to fix the issue... Currently installing; I'll update if I run into any issues thanks!

Not familiar with the forums here, am I still too new to give kudos? I'm sure there is already a sticky on this so I'll check.

---

