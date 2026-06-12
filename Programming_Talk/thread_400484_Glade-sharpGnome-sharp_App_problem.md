---
title: "Glade-sharp/Gnome-sharp App problem"
date: 2007-04-03
forum: Programming Talk
---

### Post by rekahsoft on 2007-04-03
Hi all, i am having a problem using the gnome cataloges in glade but when i try and run my program i get an error saying:```
GnomeUI-ERROR **: You must call gnome_program_init() before creating a GnomeApp
```How do i make a Gnome.Program? The part i get hung up on is the ModuleInfo argument...what is it and how do i use it?

---

### Post by rekahsoft on 2007-04-03
ok i found how to do it...i create a Gnome.Program object by doing this:```
Gnome.Program program = new Gnome.Program("name of program", "version number", Gnome.Modules.UI, args);
```Note that args is a string[].

---

