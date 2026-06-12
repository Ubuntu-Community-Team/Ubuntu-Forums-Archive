---
title: "hd0"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by gsmax4 on 2008-08-08
Does anyone know how to find out what x is in (hd0, x)??

---

### Post by sharks on 2008-08-08
it is mostly 2 or 5

---

### Post by Mister.Vash on 2008-08-08
What are you trying to do?  Are you using grub and trying to dual boot, or are tying to do something else?   Just looking for information or is the part of some configuration, and if so, what application?

---

### Post by gsmax4 on 2008-08-08
> **Mister.Vash said:**
> What are you trying to do?  Are you using grub and trying to dual boot, or are tying to do something else?   Just looking for information or is the part of some configuration, and if so, what application?

Yes I'm trying to use grub to dual boot, the partition is sda1.

---

### Post by agapito on 2008-08-08
I guess you are talking about grub. In that case the 'x' is the partition number.
Get more info in the grub documentation.

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

---

### Post by sharks on 2008-08-08
then it should (hd0, 0)

---

### Post by logos34 on 2008-08-08
if it's sda1 you're trying to boot, then you want (hd0,**0**)

*grub starts counting from 0

---

### Post by kajillin on 2008-08-08
grub should be installed in the first section of your first hard drive, your MBR. I dont think it has to be, but it will ensure a nice dual boot if ur running windows aswell.

but your labels should be as follows

sda=hd0
sda1=hd0,0
sda2=hd0,1
etc..

---

