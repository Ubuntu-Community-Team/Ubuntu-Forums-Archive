---
title: "GRUB problems..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Crafty Kisses on 2008-06-03
Well last night I installed Sabayon, because I've used it before and I liked it. So I installed Sabayon, but the thing is, that it deleted the option to boot back into Ubuntu on my GRUB loader. So now I only have Sabayon. I successfully got back into Ubuntu by using "SuperGRUB" and now I'm trying to fix up my GRUB list, and add Sabayon, but anytime I try to edit the "menu.lst" I get this error:
```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```
Any ideas? Thanks!

---

### Post by wolfen69 on 2008-06-03
```
gksudo gedit /boot/grub/menu.lst
```
you will now have permission to save changes.

---

### Post by Crafty Kisses on 2008-06-03
> **Codename said:**
> Well last night I installed Sabayon, because I've used it before and I liked it. So I installed Sabayon, but the thing is, that it deleted the option to boot back into Ubuntu on my GRUB loader. So now I only have Sabayon. I successfully got back into Ubuntu by using "SuperGRUB" and now I'm trying to fix up my GRUB list, and add Sabayon, but anytime I try to edit the "menu.lst" I get this error:
```
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
```
Any ideas? Thanks!

I've also tried gksu, still nada.

---

### Post by unutbu on 2008-06-03
Please post
```
sudo fdisk -l
ls -l /boot/grub/menu.lst
cat /boot/grub/menu.lst

```

Please tell us which partition is Sabayon, which is Ubuntu.

---

