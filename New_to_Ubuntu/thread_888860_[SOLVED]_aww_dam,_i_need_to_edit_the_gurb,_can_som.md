---
title: "[SOLVED] aww dam, i need to edit the gurb, can some1 help?"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-08-13
ok i need some help with editing my grub, i swiched my hdd's and it still boots from hd(1,1) but mi need it to boot from hd(0,1) any help is much appreciated! 

:guitar:

---

### Post by dca on 2008-08-13
At CLI, either:
 
*sudo nano /boot/grub/menu.lst*
 
(or)
 
*sudo vi /boot/grub/menu.lst*
 
...the only difference is the text editor used...

---

### Post by SchindlerShadow on 2008-08-13
> **dca said:**
> At CLI, either:
 
*sudo nano /boot/grub/menu.lst*
 
(or)
 
*sudo vi /boot/grub/menu.lst*
 
...the only difference is the text editor used...


ok.... so how do i save the changes?

---

### Post by Kevbert on 2008-08-13
With nano hit Ctrl+X
It will ask if you want to keep the changes, press Y
Then it will ask where, press return to keep the default location and that's it.

---

