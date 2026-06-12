---
title: "Change order of boot"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by geoffb1 on 2008-08-28
Hi

Expect this is easy but being completely new to Ubuntu i need some help.

When I start my laptop a window appears listing Ubuntu at the top, some other Ubuntu starts then Windows XP.

Because my wife also uses my laptop is it possible to put Windows XP at the top of the list so that it is the default boot and when I want to boot into Ubuntu I have to press the down arrow to select it.

I know in Windows it can be altered in MSConfig, select Boot.ini

Thank you

Geoff

---

### Post by Vivaldi Gloria on 2008-08-28
The boot options are configured in 

```
/boot/grub/menu.lst
```

First open a terminal and give the following command to back it up:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```

Then press ALT+F2 and start

```
gksudo gedit /boot/grub/menu.lst
```

and now edit it.

There are a couple of ways to make windows default. Try changing the line

```
default		0
```

to 

```
default		n
```

where windows is the nth option in the boot menu. Note that the count starts with 0.

---

### Post by kellemes on 2008-08-28
*Vivaldi Gloria* has it right..
See for more info.. [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by geoffb1 on 2008-08-28
Thank you for your help.

Now booting into Widows as default, Wife is now happy

Thanks again

Geoff

---

