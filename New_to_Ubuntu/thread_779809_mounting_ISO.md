---
title: "mounting ISO"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by saketh321 on 2008-05-03
Hi,
I just installed Ubuntu yesterday and managed to learn a few things.  I am trying to install a game that is in .iso format.  I installed Wine since it is needed to run windows programs and i installed gisomount as well.  But now i don't know where to go from here. I tried to looks in all the folders in applications to find gisomount but cannot find it anywhere.  

Any help would be greatly appreciated 

Thx

---

### Post by Monicker on 2008-05-03
It should be in your Applications menu.

You can also do ALT + F2, then type gisomount in the dialog box.

---

### Post by fenian on 2008-05-03
You can mount the ISO from the command line;open a terminal (Applications>Accessories>Terminal) and enter...

> sudo mkdir /media/iso
sudo mount -t iso9660 ~/Desktop/your.iso /media/iso -o loop
ls -la /media/iso

This assumes the ISO is on your desktop if not use the correct path also be sure to replace your.iso with the name of the ISO to be mounted.

---

### Post by ChameleonDave on 2008-05-03
You can also just mount stuff from the command line.

Put the .iso file on your desktop.

Open up any terminal program.

Type the following:
```

cd ~/Desktop
mkdir ISO
sudo mount -o loop *.iso ISO
```

You can replace "*.iso" with the path to your .iso file if you like.

It will then be mounted.  You can open it in a file-manager window by typing:
```
nautilus ISO
```

---

### Post by saketh321 on 2008-05-03
> **Monicker said:**
> It should be in your Applications menu.

You can also do ALT + F2, then type gisomount in the dialog box.

This is telling me that "You need to be root to run this program"

---

### Post by saketh321 on 2008-05-03
> **fenian said:**
> You can mount the ISO from the command line;open a terminal (Applications>Accessories>Terminal) and enter...



This assumes the ISO is on your desktop if not use the correct path also be sure to replace your.iso with the name of the ISO to be mounted.

Aha that worked like a charm.  Thx

---

### Post by Monicker on 2008-05-03
> **saketh321 said:**
> This is telling me that "You need to be root to run this program"

gksu gisomount works fine, in that case.

---

