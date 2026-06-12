---
title: "Qt Warnings on Compile"
date: 2012-05-23
forum: Programming Talk
---

### Post by baruch60610 on 2012-05-23
I've been working through some tutorials on the Qt-SDK.  These tutorials are the ones that came with the package.  When I ran them on Oneiric, I had no problems.  Now that I've upgraded to Precise, I am getting numerous warnings when I do a compile.  The warnings complain of a missing file "menu_proxy_module_load."  On Oneiric I never encountered this error.

Despite the warnings, the programs appear to compile correctly.  At least they run.  They don't seem to be affected by this missing file.  Even so, I'd rather track this problem down and fix it.  Any help would be appreciated.

The warning messages follow:

```
[COLOR=#0a0ab4][FONT=Monospace]Starting /home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books...[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]`menu_proxy_module_load': /home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books: undefined symbol: menu_proxy_module_load[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace](books:2281): Gtk-WARNING **: Failed to load type module: (null)[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]`menu_proxy_module_load': /home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books: undefined symbol: menu_proxy_module_load[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace](books:2281): Gtk-WARNING **: Failed to load type module: (null)[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]`menu_proxy_module_load': /home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books: undefined symbol: menu_proxy_module_load[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace](books:2281): Gtk-WARNING **: Failed to load type module: (null)[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]`menu_proxy_module_load': /home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books: undefined symbol: menu_proxy_module_load[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace](books:2281): Gtk-WARNING **: Failed to load type module: (null)[/FONT][/COLOR]
 [COLOR=#b40a0a][FONT=Monospace]
[/FONT][/COLOR]
 [COLOR=#0a0ab4][FONT=Monospace]/home/baruch/Documents/Projects/Qt/books-build-desktop-Qt_4_8_1_in_PATH__System__Release/books exited with code 0[/FONT][/COLOR]

```

---

### Post by Bachstelze on 2012-05-23
Probably a GTK bug of some sort, you often get those when running a GTK app from the terminal. If your code works fine, I would ignore them. There's probably nothing you can do to fix the.

---

### Post by baruch60610 on 2012-05-23
Thanks for your reply, Bachstelze.  I guess I don't really have a choice but to ignore it, if it's a bug in GTK itself.   I appreciate this info.

---

### Post by pbrane on 2012-05-24
I found this while searching for that warning, apparently this will fix the warnings.
```

sudo apt-get install appmenu-gtk3

```
Although according to this it may not...
[https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/791735]("https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/791735")

---

### Post by baruch60610 on 2012-05-25
Thanks, pbrane, for that idea.  I had already tried it (not sure why the idea occurred to me), but it didn't solve the problem.

OTOH, I guess as long as the programs compile and run, I won't worry too much about it.

---

