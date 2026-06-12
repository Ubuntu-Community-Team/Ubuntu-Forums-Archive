---
title: "[SOLVED] GTK &amp;amp; C - hiding a widget"
date: 2008-04-30
forum: Programming Talk
---

### Post by anewguy on 2008-04-30
I'm just a beginner here, so be kind! :):)

I have a small GTK application I am writing.  In the main.c file I have declared  GtkWidget *button2 before any functions, so it should be global, right?  Then in another file, do_download.c, I have declared extern GtkWidget *button2, that should reference the widget, right?

Ok, now when I am in do_download.c I want to hide button2 (I got here because button2 was pressed, I don't want it visible again until I finish my processing).  So, I have     gtk_widget_hide( GtkWidget button2);
in do_download.c.  When I try to compile it, I get this error:

dave@dave-desktop:~/cvsdownload$ ./compileme.sh
do_download.c: In function ‘do_download’:
do_download.c:9: error: expected expression before ‘GtkWidget’

From what I saw in a tutorial, I thought I was doing this correct, but obviously I'm being stupid again!! :):)

Any help would be greatly appreciated!! :)

---

### Post by WW on 2008-04-30
Just call **gtk_widget_hide(button2);**

---

### Post by anewguy on 2008-04-30
PERFECT !!  Thank you so much!!  :):)

---

