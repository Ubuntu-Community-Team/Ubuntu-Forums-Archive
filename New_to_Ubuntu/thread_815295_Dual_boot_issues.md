---
title: "Dual boot issues"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by dave_didlydodo on 2008-06-01
Hi everyone - this is my first post - real newbie. I've just installed 8.04 to experiment with. It's a dual boot with XP. When I boot up I get a list of about 10 different options of Ubuntu (half are recovery mode or something) and XP is at the bottom under "Other operating systems".

Is there any way of editing this list, to get rid of the unwanted entries and to put XP at the top, so it's the default?

---

### Post by shifty_powers on 2008-06-01
either go into

```
gksudo gedit /boot/grub/menu.lst
```

and edit there, though be careful and create a backup!

or go system>administrration>synaptic and search for startup manager, which when installed will be in system>administration.

---

