---
title: "kernel source ??"
date: 2005-05-18
forum: Programming Talk
---

### Post by neighborlee on 2005-05-18
where do I get kernel source ?..uname shows 2.6.10-5-386 yet closest match in synatpic is 2.6.10-34 ...????

thx
neighborlee

---

### Post by az on 2005-05-18
Use the linux-headers or linux-tree packages.

---

### Post by fishfork on 2005-05-18
This one confused me as well. After hours of messing around, I managed to compile the kernel using linux-source-2.6.10 and make-kpkg. linux-headers is just headers presumably, not the full source. So does anyone know the difference between linux-source and linux-tree?

---

### Post by jerome bettis on 2005-05-18
i would just go to [www.kernel.org](www.kernel.org) and download from there.

---

### Post by az on 2005-05-18
Linux-source is just the source.  Linux-tree is the configuration and ubuntu patches.  Use linux-tree.

Actually, if you just want to compile a module, use linux-headers and forget about the source.

---

### Post by neighborlee on 2005-05-18
[QUOTE=azz]Linux-source is just the source.  Linux-tree is the configuration and ubuntu patches.  Use linux-tree.

Actually, if you just want to compile a module, use linux-headers and forget about the source.[/QUOTE]
---------------------
well I just wanted to compile the nvidia driver ( not the one in synaptic obviously) but of course its wanting the source...ill try the tree and see if that helps although I was wanting to avoid comiling kernel if I could..takes forever lol...

i'm doing this because well my gnome desktop ( wont use kde) is a bit flakey with nautilus having crashed other day similar to behavior many others are seeing and posts seemed to indicate compiling nvidia driver from source might help?

hope someone knows about this cause i'd rather avoid comiling kernel..

actually..there IS NO tree version for the default kernel that ubuntu comes with and that will NOT work for nvidia as it must MaTCH exactly....so there is no way to compile ubuntu kernel ???? 

thx
neighborlee

---

### Post by LordHunter317 on 2005-05-18
All you need are the kernel-headers for your kernel.  Read the nvidia documentation carefully to figure out how to use them.

Why do you want to recompiled the Nvidia driver?  The Ubuntu provided one is the latest, AFAIK.

---

### Post by neighborlee on 2005-05-18
[QUOTE=LordHunter317]All you need are the kernel-headers for your kernel.  Read the nvidia documentation carefully to figure out how to use them.

Why do you want to recompiled the Nvidia driver?  The Ubuntu provided one is the latest, AFAIK.[/QUOTE]
------------------
because i'm trying to get to bottom of my gnome crashes ( same crashes others are reporting in desktop forum)....It was reccommended somewhere that compiling nvidia source migth fix this but i'm wondering if thats really so as does ubuntu do anything special with the packaged nvidia-glx ?? ..anyway I'll check the docs BUT main problem is there is no kernel package for kernel matching exactly what is default out of box installed kernel with ubuntu..which I find a bit odd dont you?

thx
neighborlee

---

