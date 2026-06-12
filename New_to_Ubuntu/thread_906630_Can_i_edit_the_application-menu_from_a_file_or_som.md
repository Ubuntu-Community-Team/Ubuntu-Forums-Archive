---
title: "Can i edit the application-menu from a file or something?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Line on 2008-08-31
Hi! I know how to left-click on the application menu and edit the program shortcuts, but is there a file or something that contain this shortcuts?
Thanks

---

### Post by halitech on 2008-08-31
not sure which file it is but alacarte (it's in the repos) will allow you to edit the application menu

---

### Post by drs305 on 2008-08-31
There are several files that contain main menu information.

~/.config/menus/applications.menu contains a list of the standard menu items.

The alacarte-generated menu items referenced in the above file are contained in the folder:
~/.local/share/applications

The numbered objects are referenced in gconf-editor /apps/panel/objects

As you can probably tell, none of these would make it easier to work with ...

---

