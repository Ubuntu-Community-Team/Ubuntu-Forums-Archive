---
title: "Trying to find a SATA card that works in ubuntu 12.04.3"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by yakinikku on 2013-09-03
Hello all!  does anyone know of a sata card, like this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16816124064](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124064), that will work for sure in Ubuntu?  

The card I linked says it will work in linux but it didn't work in Ubuntu.  I am using 12.04.3

TIA!

---

### Post by blackbird34 on 2013-09-04
If it says it works with "Linux 2.6.x and Above (AHCI devices driver is a built-in feature)", it refers to the fact that the card works with the Linux kernel, which tends to include device drivers for as much stuff as possible, including what this card needs (as per brackets). Current Ubuntu versions should be supported, as they use newer Linux kernels than 2.6 (my Ubuntu 12.04 uses the 3.2 kernel with all Ubuntu's updates applied). 
tl;dr if Linux 2.6+ is supported, Ubuntu 12.04 is.

---

### Post by yakinikku on 2013-09-04
> **blackbird34 said:**
> If it says it works with "Linux 2.6.x and Above (AHCI devices driver is a built-in feature)", it refers to the fact that the card works with the Linux kernel, which tends to include device drivers for as much stuff as possible, including what this card needs (as per brackets). Current Ubuntu versions should be supported, as they use newer Linux kernels than 2.6 (my Ubuntu 12.04 uses the 3.2 kernel with all Ubuntu's updates applied). 
tl;dr if Linux 2.6+ is supported, Ubuntu 12.04 is.

Except it didn't work.  I installed it in the system and it did not pick up the drive.  LSPCI shows that there is something there (using a marvell controller), however it did not do anything.  Thoughts?

---

### Post by yakinikku on 2013-09-06
Bumping.  Hoping I can find one that works.

---

