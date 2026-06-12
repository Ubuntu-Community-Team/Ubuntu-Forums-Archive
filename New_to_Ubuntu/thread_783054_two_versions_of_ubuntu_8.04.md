---
title: "two versions of ubuntu 8.04"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-05-05
I recently installed Ubuntu version 8.04. When I boot-up my computer and it pauses on the initial set-up screen, I notice that there are two versions of Ubuntu listed.

8.04, kernel 2.6.24-16 generic   and 
8.04, kernel 2.6.22-14 generic

How do I get rid of one of these versions?

I don't need both of them, do I?

JBA237

---

### Post by perlluver on 2008-05-05
> **JBA2337 said:**
> I recently installed Ubuntu version 8.04. When I boot-up my computer and it pauses on the initial set-up screen, I notice that there are two versions of Ubuntu listed.

8.04, kernel 2.6.24-16 generic   and 
8.04, kernel 2.6.22-14 generic

How do I get rid of one of these versions?

I don't need both of them, do I?

JBA237

Those are just the Kernels, the old one is .22-14 the newer one is 24-16.

Edit:  To get rid of one, follow this [http://ubuntuforums.org/showthread.php?t=22812](http://ubuntuforums.org/showthread.php?t=22812)

---

### Post by phr0ze on 2008-05-05
I'd leave the older one there incase you have problems. I think you can get rid of them by editing menu.lst if you really want to.

---

### Post by stchman on 2008-05-05
> **phr0ze said:**
> I'd leave the older one there incase you have problems. I think you can get rid of them by editing menu.lst if you really want to.

No, you uninstall the kernel via Synaptic.  Once the kernel is uninstalled completely it will be removed from the menu.lst file.

---

### Post by bumanie on 2008-05-05
Two kernel versions don't do any harm. It is good to have at least one old version around in case a future update does not agree with your system, you can then revert to one of the older ones. I think in /boot /grub/menu.lst you can edit one them from appearing by putting # in front of the relevant lines - this doesn't remove it, just stops it showing at boot.

---

