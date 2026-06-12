---
title: "Is there any tool to buildup a GUI installer?"
date: 2008-09-09
forum: Packaging and Compiling Programs
---

### Post by uilaek on 2008-09-09
Is there any tool to build up GUI installer? similar to Windows or Mac application, the user select or fill some information, and the click next.

---

### Post by uilaek on 2008-09-09
such as InstallJammer, or Mac's packagemaker.

i'd like the packagemaker, it is more simple. but there is no linux version available.

---

### Post by loell on 2008-09-09
there is none, and such type of installers are despised in the free software world.

its debs,rpms and bins that are widely acceptable.

you could make from scratch though. ie( pygtk , zenity). ;)

---

### Post by ad_267 on 2008-09-09
Why?

If you package it as a .deb then you can just double click to install with gdebi-gtk.

---

### Post by uilaek on 2008-09-09
> **ad_267 said:**
> Why?

If you package it as a .deb then you can just double click to install with gdebi-gtk.
OK. there are serveral .deb package in our project, and we want provide a big installer package.

there are dependence between these packages, and not all package are necessary (depend on user's selection).

we also need to gather some information from user, and take different after that (click next or continue).

Any idea on this? Thanks all for your reply.

---

### Post by uilaek on 2008-09-09
> **loell said:**
> there is none, and such type of installers are despised in the free software world.

its debs,rpms and bins that are widely acceptable.

you could make from scratch though. ie( pygtk , zenity). ;)
from scratch is nightmare, we all lazy man.....  :D

A GUI installer satisfies our purpose best, and makes our users feeling easy.

---

### Post by ad_267 on 2008-09-09
I guess it would be pretty simple to set up something with python and pygtk then and just get the user to select their options. Then when they click install it could use "gksu dpkg -i" to install the selected packages.

---

### Post by loell on 2008-09-09
> **uilaek said:**
> from scratch is nightmare, we all lazy man.....  :D

A GUI installer satisfies our purpose best, and makes our users feeling easy.

its not as difficult as it sounds, its really easy especially with zenity , if you just require user information and some click buttons and dialogs. :)

---

