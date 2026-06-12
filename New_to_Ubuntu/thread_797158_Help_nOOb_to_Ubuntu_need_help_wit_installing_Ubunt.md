---
title: "Help nOOb to Ubuntu need help wit installing Ubuntu Studio keeps giving me errors"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by eragon256 on 2008-05-17
:(:( Trying to install Ubuntu Studio I boot from CD and get GRUB Loading Stage1.5

GRUB loading, please wait....
Error 17 (or 15 or 22)

---

### Post by overdrank on 2008-05-17
> **eragon256 said:**
> :(:( Trying to install Ubuntu Studio I boot from CD and get GRUB Loading Stage1.5

GRUB loading, please wait....
Error 17 (or 15 or 22)

HI and welcome, you are installing or you have installed? Because you only receive the grub errors from a installation.

---

### Post by eragon256 on 2008-05-17
Installing to a computer without other OS on it didn;t think I would have so much problems

---

### Post by overdrank on 2008-05-17
> **eragon256 said:**
> Installing to a computer without other OS on it didn;t think I would have so much problems

OK is the system set to boot to the cd drive? Have you check the cd for errors?

---

### Post by eragon256 on 2008-05-17
I dont even get that far and I know that boot option 1,2, and 3 are set to boot from CD cause at first it kept trying to boot from HDD

---

### Post by overdrank on 2008-05-17
> **eragon256 said:**
> I dont even get that far and I know that boot option 1,2, and 3 are set to boot from CD cause at first it kept trying to boot from HDD

Ok you may look at these links 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by eragon256 on 2008-05-17
I have had Ubuntu on the comupter before and it went just fine then after a few hours of working on my older computer the WinBook I put it in my Dell and booted from CD it came up just fineis it the computer or the Disc and if it is computer what should I do?

---

### Post by eragon256 on 2008-05-17
Oh and i have reformatted HDD like an unknown amount of times with Gparted to get that to work but I either get Error 15 or 17 with all and then I read something on making a smaller partition and then a bigger and formatted to what it said and got error 22

---

### Post by h4mx0r on 2008-05-17
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

That explains all the grub error messages possible and gives good tips.

"22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel." That is your current problem.

---

### Post by h4mx0r on 2008-05-17
Solution To Problem:

1) your system used to have windows and has junked up the master boot record of the hard drive so use dd to wipe the first few sectors of your hard drive from a live cd system.

2) your /boot/grub/menu.lst might be incorrect

Any other possibilities I missed?

---

### Post by eragon256 on 2008-05-17
Still a nOOb what do I do right now it is giving me ERROR 15

---

