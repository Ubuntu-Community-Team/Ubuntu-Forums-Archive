---
title: "Slow Graphics"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-06-08
I just upgraded my nvidia gts 64 mb graphics card to an ati radeon 9600 128 mb card and when I tried to run any games the graphics were incredibly choppy. I'm not sure what caused it but when I switched back to my nvidia it was still choppy. Also, my trash icon on the panel dissappeared and when I try to add it back it won't. Everything worked fine before. Help!

---

### Post by scott_g on 2008-06-12
I don't know the answer, but it may be helpful to others if you post your xorg.conf file (/etc/X11/xorg.conf), as well as which graphics you are using that are choppy, and whether you are using compiz or not.  Just a few ideas...

Scott

---

### Post by alienexplorers on 2008-06-12
As for the trash can check that:
> /home/userdirname/.gnome/gnome-vfs/.trash_entry_cache
is there.  I had a problem simular to you with loosing the trash can and found that my .gnome directory was missing.  Rebuilt it and restarted the computer and the trash can came back.

---

### Post by skymera on 2008-06-12
What games are you trying to play?

It could be down to the drivers, ATi don't function well in Linux.

Scott.

---

