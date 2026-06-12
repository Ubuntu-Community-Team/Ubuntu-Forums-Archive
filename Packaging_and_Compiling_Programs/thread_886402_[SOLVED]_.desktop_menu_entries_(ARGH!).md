---
title: "[SOLVED] .desktop menu entries (ARGH!)"
date: 2008-08-11
forum: Packaging and Compiling Programs
---

### Post by viciouslime on 2008-08-11
I'm trying to package a project i'm working on and I've managed to get the deb to work just as I want it, except for menu entries... it installs a .desktop file to /usr/share/applications/ but this doesn't appear in the menu until i restart gnome-panel, is there a command I can issue to update the menus after my deb is installed?

I've tried adding "include /usr/share/cdbs/1/class/gnome.mk" to my rules file, but this gives the following error when i run debuild:

chmod: cannot access `/home/dan/Projects/ViciousLex/Build/viciouslex-0.6/./configure': No such file or directory

---

### Post by bobbocanfly on 2008-08-11
> **viciouslime said:**
> I'm trying to package a project i'm working on and I've managed to get the deb to work just as I want it, except for menu entries... it installs a .desktop file to /usr/share/applications/ but this doesn't appear in the menu until i restart gnome-panel, is there a command I can issue to update the menus after my deb is installed?

I've tried adding "include /usr/share/cdbs/1/class/gnome.mk" to my rules file, but this gives the following error when i run debuild:

chmod: cannot access `/home/dan/Projects/ViciousLex/Build/viciouslex-0.6/./configure': No such file or directory

You need to put the line "dh_desktop" somewhere in Debian rules (after you install the .desktop into /usr/share/applications obviously).

---

### Post by viciouslime on 2008-08-12
> **bobbocanfly said:**
> You need to put the line "dh_desktop" somewhere in Debian rules (after you install the .desktop into /usr/share/applications obviously).

I came across something else that told me to do that, but when i looked into it further it said that dh_desktop only works if your applications registers new MIME types, my application does not do this, so dh_desktop is no use :(

I'll try it anyway just in case, now you've recommended it too, and I'll post back with the results, I'm not hopeful though :(

Thanks anyway!!! :)

---

### Post by viciouslime on 2008-08-12
Ok that didn't work :( However, I'm using cdbs, so I think that is why.

It would appear that when using cdbs you should have "include /usr/share/cdbs/1/class/gnome.mk" in the rules file as an equivalent, but this reults in an error for me:

chmod a+x /home/dan/Projects/ViciousLex/Build/viciouslex-0.6/./configure
chmod: cannot access `/home/dan/Projects/ViciousLex/Build/viciouslex-0.6/./configure': No such file or directory
make: *** [config.status] Error 1


I don't know why it now looks for such a directory, or how to stop it doing so...

---

### Post by bobbocanfly on 2008-08-13
Can you post your debian/rules file so we can see what might be calling the file that doesnt exist?

---

### Post by viciouslime on 2008-08-13
```
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/simple-patchsys.mk
include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/class/makefile.mk

DEB_MAKE_BUILD_TARGET = DESTDIR=$(CURDIR)/debian/viciouslex 
DEB_MAKE_INSTALL_TARGET = DESTDIR=$(CURDIR)/debian/viciouslex 
```

That's the debian/rules file :)

If I add "include /usr/share/cdbs/1/class/gnome.mk" under "include /usr/share/cdbs/1/class/makefile.mk" then i get the error above :(

---

### Post by viciouslime on 2008-08-13
Ok, I think this is pretty messy... but it works

I've added the gnome.mk line and created a new file called config in the level above the debian folder that contains a single line: "echo nothing to do here"

Now everything works fine :)

Thanks for the help guys

---

