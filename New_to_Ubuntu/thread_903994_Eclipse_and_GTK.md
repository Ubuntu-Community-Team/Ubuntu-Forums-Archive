---
title: "Eclipse and GTK"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by bacardiandwatermelon on 2008-08-28
From one noobie programmer to another..

To configure eclipse 3.4 so it can find the <gtk/gtkh.> folder you need to..
click your project in project explorer ->Project->Properties->C/C++ Build->Settings->GCC C Compiler->Directories.
Add /usr/include/gtk-2.0

Then under Miscellaneous->Other flags
Add -L 'pkg-config --cflags --libs gtk-2.0'

update.

Well it did work but it aint anymore... When I figure out what I did wrong I will let ya know...

---

### Post by SpectacularNick on 2009-01-06
I'm trying to get my head around the somewhat the same problem. What does that other flag do?

When I tried to include /usr/include/gtk-2.0 i got tons of syntax errors though. including /usr/include/gtk-2.0/gtk worked. But Im missing a linker search path. At least thats what I think. The errors I get are similar to error I get on compiling onto other libraries when I remove the linker search path to them.

Here's my similar thread:
[http://ubuntuforums.org/showthread.php?t=1032447&highlight=include+GTK+eclipse+project](http://ubuntuforums.org/showthread.php?t=1032447&highlight=include+GTK+eclipse+project)

---

