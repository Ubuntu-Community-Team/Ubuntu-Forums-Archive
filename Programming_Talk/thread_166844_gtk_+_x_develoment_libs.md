---
title: "gtk + x develoment libs"
date: 2006-04-27
forum: Programming Talk
---

### Post by M4av0 on 2006-04-27
hi all,
i'm trying to compile gtk 2.8.16 on my machine, but the configure script displays error:
checking for X... no
configure: error: X development libraries not found

now, i don't know what these libraries are and where to get them (i have successfuly compiled other required libs).

please help
thanks!

---

### Post by mostwanted on 2006-04-27
Don't start compiling that stuff yourself. What do you honestly need in the newest version of GTK? It's just extra bug fixes. Ubuntu uses the version of Gnome and GTK it uses and messing with that is not a good idea. If you want the bleeding edge libraries you should use Dapper Drake.

---

### Post by M4av0 on 2006-04-27
well i need gtk+ to be able to build openbox, nmap (frontend) and such and maybe for building my own appz. if this is the wrong way, please tell me how to do it correctly (i'm slightly loosing my nerve with this).
thanks.

ps. i have compiled gtk+ a long time ago on redhat 9 with no prob. (even made some of my own appz), i'm not a total newbie, but i can't get this xlib stuff to work.

---

### Post by mostwanted on 2006-04-27
GTK+ 2.8 is installed along with Ubuntu, all the graphical programs included use it. What you need to is install the GTK+ header files that come with the package *libgtk2.0-dev* to be able to compile programs that use the GTK+ toolkit. See the link in my signature about installing packages in Ubuntu.

---

