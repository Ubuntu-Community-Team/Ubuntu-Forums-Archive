---
title: "Creating menus"
date: 2007-09-26
forum: Packaging and Compiling Programs
---

### Post by panayk on 2007-09-26
Hi! Sorry if this turns out to be a stupid question, but why doesn't my .deb package create menu entries in Gnome?

I have the following debian/menu file:

```
?package(dreamchess): needs="X11" section="Games" title="DreamChess" command="/usr/bin/dreamchess"
```

as described here: [http://www.debian.org/doc/maint-guide/ch-dother.en.html#s-menu](http://www.debian.org/doc/maint-guide/ch-dother.en.html#s-menu)

I have also tried: Applications/Games and Apps/Games

As you can tell the application I am trying to package is dreamchess. :)

---

### Post by neurostu on 2008-07-07
Did you ever figure this out? I'm trying to do essentially the same thing...

---

### Post by panayk on 2008-07-19
Hmm, I think you have to create a .desktop file under /usr/share/applications/, (take a look in the files already there) whereas package.menu places a shortcut in the debian submenu (which is disabled by default in ubuntu)

---

### Post by neurostu on 2008-07-19
So I actually figured it out:
you need to create a .desktop file for the individual program and you need to create a .directory folder for any directories you want created in the menu.

you can then install them using xdg:
```

sudo xdg-desktop-menu install <directoryFile>.directory <desktopFile>.desktop

```
This takes care of placing all the files in the right place and you can then uninstall them with xdg.

---

