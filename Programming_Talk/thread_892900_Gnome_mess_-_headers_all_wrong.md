---
title: "Gnome mess - headers all wrong"
date: 2008-08-17
forum: Programming Talk
---

### Post by mike_g on 2008-08-17
I have just spent the last hour modifying the gnome headers because they all refer to teh wrong directories. I though it was over but now bonobo wants to poo in my face. This is what I am getting:
```
gcc -Wall treetest.c `pkg-config --cflags --libs gtk+-2.0`
In file included from /usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:44,
                 from treetest.c:4:
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:55:51: error: libbonobo-2.0/bonobo/bonobo-dock-band.h: No such file or directory
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:56:53: error: libbonobo-2.0/bonobo/bonobo-dock-layout.h: No such file or directory
In file included from /usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:44,
                 from treetest.c:4:
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:99: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:107: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:126: error: expected declaration specifiers or ‘...’ before ‘BonoboDockLayout’
In file included from treetest.c:4:
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:90: error: expected specifier-qualifier-list before ‘BonoboDockLayout’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:145: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItemBehavior’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:154: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItemBehavior’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:161: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
treetest.c: In function ‘main’:
treetest.c:80: warning: assignment from incompatible pointer type
treetest.c:88: warning: passing argument 1 of ‘gtk_widget_show_all’ from incompatible pointer type
mike@mike-laptop:~/code/GTKTreeview$ clear

mike@mike-laptop:~/code/GTKTreeview$ gcc -Wall treetest.c `pkg-config --cflags --libs gtk+-2.0`
In file included from /usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:44,
                 from treetest.c:4:
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:55:51: error: libbonobo-2.0/bonobo/bonobo-dock-band.h: No such file or directory
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:56:53: error: libbonobo-2.0/bonobo/bonobo-dock-layout.h: No such file or directory
In file included from /usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:44,
                 from treetest.c:4:
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:99: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:107: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libbonoboui-2.0/bonobo/bonobo-dock.h:126: error: expected declaration specifiers or ‘...’ before ‘BonoboDockLayout’
In file included from treetest.c:4:
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:90: error: expected specifier-qualifier-list before ‘BonoboDockLayout’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:145: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItemBehavior’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:154: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItemBehavior’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:161: error: expected declaration specifiers or ‘...’ before ‘BonoboDockItem’
/usr/include/libgnomeui-2.0/libgnomeui/gnome-app.h:171: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
treetest.c: In function ‘main’:
treetest.c:80: warning: assignment from incompatible pointer type
treetest.c:88: warning: passing argument 1 of ‘gtk_widget_show_all’ from incompatible pointer type
```
Now I really dont want to have to manually edit all these files. Has anyone else had this problem? How best should I deal with it?

Cheers.

---

### Post by mike_g on 2008-08-17
Ok, I went back and undid all the changes I made. It seems I need to link the gnome package somehow. For example if I add:
```
`pkg-config --cflags --libs gtk+-2.0`
``` 
to gcc it links the gtk+2.0 package and  can include gtk by doing:
[include]#include <gtk/gtk.h>[/code]
When the actual directory is something like:
```
/usr/share/include/gtk-2.0/gtk/gtk.h
```
Anyone know how I can set it up to link gnomeui?
As a guess I tried:
```
`pkg-config --cflags --libs gnomeui-2.0` 
```
But it gives this error:
```
Package gnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gnomeui-2.0' found
```

---

