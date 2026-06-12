---
title: "GTK problems"
date: 2006-10-13
forum: Programming Talk
---

### Post by xerio on 2006-10-13
Ok. I have gtk2 installed and everything. But when I try to compile a simple program to display a simple window, it won't compile. I get the following error:

```

base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:6: error: (Each undeclared identifier is reported only once
base.c:6: error: for each function it appears in.)
base.c:6: error: ‘window’ undeclared (first use in this function)
base.c:8: error: ‘argv’ undeclared (first use in this function)
base.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

```

Can someone please help me fix this problem? I have gtk installed so I don't understand how I don't have the .h files for it.

---

### Post by po0f on 2006-10-13
xerio,

Most distributions don't install headers with library packages, so you'll need to install libgtk2.0-dev to develop GTK2 apps.

---

