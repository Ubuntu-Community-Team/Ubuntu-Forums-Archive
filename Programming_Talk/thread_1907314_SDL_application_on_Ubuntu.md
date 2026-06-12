---
title: "SDL application on Ubuntu"
date: 2012-01-11
forum: Programming Talk
---

### Post by dosh on 2012-01-11
I like using SDL and ubuntu. I have not written any programs for a while and have just gotten back to it. I am not very keen on GTK+ and notice that most programs use the Global Application Menu (?) rather than have menus in the application Window. Is  there a way to be able to write the menus to the Global Application Menu using just SDL not GTK? Any hacks? Or code examples?

---

### Post by Simian Man on 2012-01-11
The global application menu is itself a hack.  Unity looks for the GTK+ menus and moves them up itself.  If you were to run those same GTK+ applications on regular Gnome, KDE or something else, the menus would be in the main window like normal.

Anyway, as far as I know, there is no way for SDL to render anything outside of its window.

---

