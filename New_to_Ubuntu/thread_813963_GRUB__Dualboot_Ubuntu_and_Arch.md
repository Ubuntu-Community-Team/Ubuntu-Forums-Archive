---
title: "GRUB  Dualboot Ubuntu and Arch"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by backupdevice on 2008-05-31
Hi there,

I need big help. 

I use ubuntu as primary os, and installed ARH on a third HDD .
I tried to edit menu.lst and add Arch linux, but somehowe i dont get it. 

So, ARCH is installed on the 3th HDD, witch is SDC. ARCH boot on SDC1, etc etc etc.

So my entry for ARCH in grup is like this

title arch
root (hd2,0) because grup starts from 0
kernel /boot/vmklinuz26 root=/dev/sdc ro
initrd /kernel26.img

But when i boot and choose arch, it doesnt work....

Help[ me please

---

### Post by Biggy on 2008-05-31
from Aplication > Add/Remove > install StartUp-Manager

---

### Post by InfinityCircuit on 2008-05-31
It should be /boot/vmlinuz26 not /boot/vmklinux26

---

### Post by backupdevice on 2008-05-31
> **Biggy said:**
> from Aplication > Add/Remove > install StartUp-Manager

Thx for the quick reply , but dont know for sure what this would do? 

I installed it, and only after i editted grub, it shows in the pulldown menu.

---

### Post by backupdevice on 2008-05-31
> **InfinityCircuit said:**
> It should be /boot/vmlinuz26 not /boot/vmklinux26

Thx, changed it, no luck

---

### Post by Biggy on 2008-05-31
after install Startup-manager you can view in System > Administration > StartUp-Manager . for more info how to use, go to [Home]("http://web.telia.com/~u88005282/sum/index.html")

---

### Post by backupdevice on 2008-05-31
> **Biggy said:**
> after install Startup-manager you can view in System > Administration > StartUp-Manager . for more info how to use, go to [Home]("http://web.telia.com/~u88005282/sum/index.html")

Fixed it, logged into ubuntu, went to the partition where arch was installed, copied the menu.lst there, copied the entry, past it the real one, edit one line and vavoem

---

### Post by backupdevice on 2008-05-31
> **Biggy said:**
> after install Startup-manager you can view in System > Administration > StartUp-Manager . for more info how to use, go to [Home]("http://web.telia.com/~u88005282/sum/index.html")

Fixed it, logged into ubuntu, went to the partition where arch was installed, copied the menu.lst there, copied the entry, past it the real one, edit one line and vavoem

---

