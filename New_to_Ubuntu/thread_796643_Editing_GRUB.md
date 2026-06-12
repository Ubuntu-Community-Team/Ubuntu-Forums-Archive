---
title: "Editing GRUB?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by ylinux on 2008-05-16
I'm currently dual booting Ubuntu and Vista and I'd like to tidy up my GRUB menu a bit. 

Just curious about the entries for:
kernel (recovery mode)
memtest

Can I get rid of these safely from the menu or is there any reason why I would want to keep them there?

---

### Post by shifty_powers on 2008-05-16
```
gksudo gedit /boot/grub/menu.lst
```

just make sure that you save a copy of it.

plus you might want to

```
sudo apt-get install startupmanager
```

it will probably do what you want for you ;) it will appear in system>administration iirc.

---

### Post by UnWarierMage224 on 2008-05-16
A safer option is to use startupmanager (can be gotten from the repositories, search in Synaptic)... It will let you get rid of the memtest/kernel options. 

-'Mage

---

### Post by shifty_powers on 2008-05-16
heh beat you to it ;)

---

### Post by Oldsoldier2003 on 2008-05-16
> **ylinux said:**
> I'm currently dual booting Ubuntu and Vista and I'd like to tidy up my GRUB menu a bit. 

Just curious about the entries for:
kernel (recovery mode)
memtest

Can I get rid of these safely from the menu or is there any reason why I would want to keep them there?

you might want to keep the recovery mode login, its very useful if you run into massive configuration problems and become unable to sudo.
memtest is up to you, it could come in handy someday, but I just run memtest from a bootcd if I need it.

---

### Post by UnWarierMage224 on 2008-05-16
> **shifty_powers said:**
> heh beat you to it ;)

:lolflag:

---

### Post by sailor2001 on 2008-05-16
you can do this:  gksudo gedit /boot/grub/menu.lst  and place a hash before the lines you don't want to show up. (mem test and safe)  That way you can always go back and remove the hash at anytime

---

