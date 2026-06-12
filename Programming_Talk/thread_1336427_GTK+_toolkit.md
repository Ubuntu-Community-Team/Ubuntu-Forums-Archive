---
title: "GTK+ toolkit"
date: 2009-11-24
forum: Programming Talk
---

### Post by Engromada on 2009-11-24
I can't work this out for myself... is the GTK+ toolkit (for creating 	  graphical user interfaces) pre installed in the latest Ubuntu distro? if not is there a proper Ubuntu package for it?

Thanks.

Engro.

---

### Post by diesch on 2009-11-24
Gnome is based on GTK so GTK is installed by default.

---

### Post by Engromada on 2009-11-24
*ponders* 

so the programming package for GTK+ development is installed because gnome was made with it? i mean i have GIMP installed on my windows machine but that doesn't mean i have the GTK+ development installed, or anything related to it.

or does Ubuntu include all the development tools that were used to create Ubuntu and it's default packages?

---

### Post by mali2297 on 2009-11-24
If you want to use it in your code, then you also need the development files: [http://packages.ubuntu.com/karmic/libgtk2.0-dev](http://packages.ubuntu.com/karmic/libgtk2.0-dev).

---

### Post by Engromada on 2009-11-24
thanks mali2297 =)

---

### Post by SledgeHammer_999 on 2009-11-24
As far as I know Ubuntu doesn't ship with development files by default(of any library). But it has them available as packages on the online repos.

For gtk+ open Synaptic and search for "libgtk2.0-dev" and install it. Notice the "*-dev". That's marks development files.

---

