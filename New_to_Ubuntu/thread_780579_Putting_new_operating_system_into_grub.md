---
title: "Putting new operating system into grub?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by joyser on 2008-05-03
hi
just wondering how i can put a different third party operating system on the grub as another option to boot from
thanks

---

### Post by acelin on 2008-05-03
> **joyser said:**
> hi
just wondering how i can put a different third party operating system on the grub as another option to boot from
thanks

Usually it will pick it up as long as you didnt overwrite using w/e that OS uses as a boot manager...

---

### Post by CloudFX on 2008-05-03
You will need to edit GRUB by entering this input:

```
gksu gedit /boot/grub/menu.lst
```

Scroll down to the bottom, where you will see all of the items that are currently in GRUB.  Enter the information at the bottom of this list.

---

### Post by zvacet on 2008-05-04
First find on which partition is installed with 

```
sudo fdisk -l
```

Then 

```
sudo cp /boot/grub/menu.lst /boot/grub.menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

find line

### END DEBIAN AUTOMAGIC KERNELS LIST

title     OSname
rootnoverify (hd?,?)
chainloader +1

EDIT: If for example in fdisk -l partition was hda2 under rootnoverify you will put (hd0,1)

---

