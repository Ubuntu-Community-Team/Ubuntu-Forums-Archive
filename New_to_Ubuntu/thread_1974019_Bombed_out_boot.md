---
title: "Bombed out boot"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by nuddernuby on 2012-05-05
This is a bit embarrassing.

Dual boot Windows XP and 11.04 - all fine.
Needed to be able to boot from CD, so installed SBM.
Now I can't boot at all - only blank screen.
Supergrub and Supergrub 2 CDs don't help as I can't boot from CD.

Any suggestions will be appreciated. Thank you

---

### Post by strask on 2012-05-05
I assume by SBM you mean Smart Boot Manager from [http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html) yes?

What devices do you have on your computer that could potentially be used as boot devices? You mentioned a CD drive (PATA, SATA, SCSI?) and of course you have a hard drive (or more than one? what kind?) but do you also have a floppy drive? What about USB ports?

Can you get into your BIOS? What is the configured boot order?

---

### Post by nuddernuby on 2012-05-05
Thank you for your response.
Yes, Smart Boot Manager, installed from the Ubuntu Software Centre.
System:
Intel Core 2 Duo
1 SATA HDD 500gb
4 USB ports
CD/DVD drive
No Floppy

Yes, can get to BIOS (American Megatrends). Current boot order:
HDD
CD/DVD
1st Floppy
The above are in square brackets. Comment in BIOS says: "A device enclosed in parentheses has been disabled in the corresponding type menu". I don't know if that has any relevance.

---

### Post by nuddernuby on 2012-05-06
Thank you - problem solved.

---

