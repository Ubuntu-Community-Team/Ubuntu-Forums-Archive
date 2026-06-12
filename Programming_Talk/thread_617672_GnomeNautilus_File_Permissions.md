---
title: "Gnome/Nautilus File Permissions"
date: 2007-11-19
forum: Programming Talk
---

### Post by thethawav on 2007-11-19
a program to set the ownership of a file - name has to be determined (suggestions welcome)
* added functionality to set the group

If you want me to provied ubuntu-packages just ask. descriptions on how to compile one post below

 .... still looking for someone whos experienced in hacking nautilus
Screenshot:
[IMG]http://i216.photobucket.com/albums/cc135/meanbeanmachine/Bildschirmfoto.png[/IMG]

for your convenience i've also made a deb-/ubuntu-package

---

### Post by thethawav on 2007-11-21
I've hacked something together (one evil piece of buggy code).
If you're brave enough to try use the following command to compile(you have to rename it from permissions.txt to permissions.c):

gcc -o perm permissions.c `pkg-config --libs --cflags gtk+-2.0 libgksu2`

have fun and report back anything unusual or feature requests

---

