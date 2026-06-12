---
title: "GTK Not Found"
date: 2008-06-13
forum: Programming Talk
---

### Post by Black Mage on 2008-06-13
I am writing a program and when I include:

#include <gtk/gtk.h>

it says

testprogram.c:1:21: error: gtk/gtk.h: No such file or directory

and a whereis gtk gives me

gtk: /etc/gtk

And I've done a apt-get install gtkdev2.0. Does anyone have an idea of what is wrong? And I am relatively new to C/C++

---

### Post by LoneWolfJack on 2008-06-13
try

```
gcc -Wall -g yourprogramname.c -o outputfilename `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`
```

---

### Post by JupiterV2 on 2008-06-13
Make sure you do your homework before posting. The answer lies within the gtk docs.

When compiling a gtk program, you need to provide the compiler with path's to its libraries. This is most easily done with pkg-config:

```
gcc my_gtk_source.c `pkg-config --cflags --libs gtk+-2.0`
```

See: [http://library.gnome.org/devel/gtk/stable/gtk-compiling.html]("http://library.gnome.org/devel/gtk/stable/gtk-compiling.html")

---

### Post by Black Mage on 2008-06-13
Ahhh, alright thanks.

---

