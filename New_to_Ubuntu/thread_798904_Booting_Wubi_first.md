---
title: "Booting Wubi first"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by drifter2502 on 2008-05-18
I am running Wubi 8.04 on a Vista based MSI  M670 Laptop. It was a direct download (no iso  disc involved) . Works very well and much faster than the Vista base it sits in!! (I digress). I would like to have Wubi boot up first but the instructions in Wubi FAQ only give instructions for XP based machines. Is the procedure the same for Vista? If not , is it possible to help me and others to get Wubi to boot first in Vista based computers? Thanks.

---

### Post by jimmy the saint on 2008-05-18
According to the faq, Ubuntu gets added to the windows bootloader, which means that at startup, you should have the choice

---

### Post by eriqjaffe on 2008-05-18
I haven't tried it, as I have no plans on running Vista, but [this]("http://neosmart.net/dl.php?id=1") is **supposed** to let you edit the Vista boot loader.

---

### Post by drifter2502 on 2008-05-19
> **eriqjaffe said:**
> I haven't tried it, as I have no plans on running Vista, but [this]("http://neosmart.net/dl.php?id=1") is **supposed** to let you edit the Vista boot loader.
Thanks. What I mean is,When the boot choice screen is up I have to decide within 8 seconds otherwise Vista gets loaded. I would prefer Ubuntu to load first. If I am distracted in those seconds I have to completely re boot and start over to get Ubuntu up and running.Is there a fix without having to resort to an outside facility as kindly suggested in #3.

---

### Post by jimmy the saint on 2008-05-20
if the vista bootloader is controlling the boot process then you need to edit it in order to change its behavior.  Check out the tool he showed you, or install grub, but you will have to edit that in the end as well if you want to change its default behavior.

---

### Post by drifter2502 on 2008-05-20
Solved. Thanks very much. That little programme works very well.

---

