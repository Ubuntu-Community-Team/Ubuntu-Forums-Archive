---
title: "Vala crashes when compiling gtk app"
date: 2010-06-20
forum: Programming Talk
---

### Post by Glenn nl on 2010-06-20
Hello, I am experimenting with vala but when compiling a gtk app I get a nice big error. >_<
I have used some vala gtk examples on youtube and on the vala website.
But when compiling I get this:

```
glenn@glenn-laptop:~$ valac --pkg gtk+-2.0 gtktest.vala
/home/glenn/gtktest.vala.c:7:21: error: gtk/gtk.h: file or folder doesn´t exist
/home/glenn/gtktest.vala.c:15: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c:16: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c:17: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c:22: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c:27: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c:33: error: expected ‘)’ before ‘*’ token
/home/glenn/gtktest.vala.c: In function ‘_vala_main’:
/home/glenn/gtktest.vala.c:40: error: ‘GtkWindow’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:40: error: (Each undeclared identifier is reported only once
/home/glenn/gtktest.vala.c:40: error: for each function it appears in.)
/home/glenn/gtktest.vala.c:40: error: ‘window’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:41: error: ‘GtkButton’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:41: error: ‘button’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:43: error: expected expression before ‘)’ token
/home/glenn/gtktest.vala.c:46: error: ‘GTK_WIN_POS_CENTER’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:47: error: ‘GtkObject’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:47: error: expected expression before ‘)’ token
/home/glenn/gtktest.vala.c:47: error: ‘_gtk_main_quit_gtk_object_destroy’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:48: error: expected expression before ‘)’ token
/home/glenn/gtktest.vala.c:49: error: ‘__lambda0__gtk_button_clicked’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:50: error: ‘GtkContainer’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:50: error: expected expression before ‘)’ token
/home/glenn/gtktest.vala.c:51: error: ‘GtkWidget’ undeclared (first use in this function)
/home/glenn/gtktest.vala.c:51: error: expected expression before ‘)’ token
error: cc exited with status 256
Compilation failed: 1 error(s), 0 warning(s)

```

(note: this even happens with a direct copy and paste)

can somebody help me out 0_0

---

### Post by splicerr on 2010-06-20
You need to install the gtk dev package: **libgtk2.0-dev**

---

### Post by Glenn nl on 2010-06-21
> **splicerr said:**
> You need to install the gtk dev package: **libgtk2.0-dev**

[IMG]http://www.thefoodsection.com/photos/uncategorized/2008/12/09/cookie.jpg[/IMG]

:)

---

