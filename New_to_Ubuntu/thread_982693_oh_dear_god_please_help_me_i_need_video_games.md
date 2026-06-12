---
title: "oh dear god please help me i need video games"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by paininurhead on 2008-11-15
help me i have installed ubuntu completely from scratch on my new computer and i want dual boot windows now this damn computer cant see any drives while am booting from the windows CD PLEASE HELP ME I need my diablo 2

---

### Post by jimmy the saint on 2008-11-15
xp or vista?

---

### Post by paininurhead on 2008-11-15
XP quick and easy i would think please help

---

### Post by Mardoct909 on 2008-11-15
Umm, it's really a better idea to install Windows then Ubuntu. I really doubt that this has caused your problems, but when they are fixed, keep this in mind.

---

### Post by jimmy the saint on 2008-11-15
not neccessarily.  If it is a new computer, it likely has sata drives.  XP installer doesn't have them.  You need to put them on a floppy (if you have a floppy drive) and load them when it asks if you have any drivers (i think it asks you to hit f6).  or you can slipstream them into the image and reburn it.

Very true about the window THEN Ubuntu

But Your issue is the SATA drivers

---

### Post by Mardoct909 on 2008-11-15
I've done literally 10 or more XP installs with SATA hard drives just fine.

Did they include them with SP2? Is that it?

---

### Post by paininurhead on 2008-11-15
Where might I find these SATA drivers? Cause i am srtarting from scratch

---

### Post by jimmy the saint on 2008-11-15
> **Mardoct909 said:**
> I've done literally 10 or more XP installs with SATA hard drives just fine.

Did they include them with SP2? Is that it?

were you using a genuine windows xp cd?  Last month I put xp on a qozmio laptop and had to slipstream the drivers into the image.  There are all kinds of tutorials for it.

PAININURHEAD:
You will need to find your sata controller.  In the Ubuntu live cd open a terminal and type in 
```
lspci
```
and look for a line that looks similar to 
```
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)

```
the make and model may be different, but look for the SATA controller.
Then employ google to find your drivers and follow this tutorial if you have a floppy drive [http://www.mysuperpc.com/build/pc_sata_install_windows_operating_system.shtml](http://www.mysuperpc.com/build/pc_sata_install_windows_operating_system.shtml)

or this one if you don't (though you will need to use a windows computer) [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml)

---

### Post by Mardoct909 on 2008-11-15
> **jimmy the saint said:**
> were you using a genuine windows xp cd?  Last month I put xp on a qozmio laptop and had to slipstream the drivers into the image.  There are all kinds of tutorials for it.


I don't know if I'd use the word genuine...

---

### Post by jimmy the saint on 2008-11-15
most retooled images would have the drivers slipstreamed in.

---

