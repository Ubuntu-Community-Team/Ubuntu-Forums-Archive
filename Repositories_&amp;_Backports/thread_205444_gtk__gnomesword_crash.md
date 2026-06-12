---
title: "gtk / gnomesword crash"
date: 2006-06-28
forum: Repositories &amp; Backports
---

### Post by Coburn on 2006-06-28
While checking out some package installs on 5.10 using Synaptic, I crashed one of my programs, and have not been able to get it to run again, even with several different ways of reinstalling it and the related packages.

The crashed program is gnomesword.

I think I was installing arkrpg when it crashed, but maybe it was gtkhtml and libgtkhtml-data.  The error messages seem to have to do with gtk.  I don't remember why I installed those last two, but if they overwrote some key file or other, it won't come back.

I have removed arkrpg and its (new) dependencies, and tried to reinstall all the affected programs.  Specifically there was another glitch that was fixed by installing libstdc++-gtkhtml.#-#... 

If anybody has thoughts on this, maybe I won't have to wait 2-3 weeks 'till my Dapper CD comes in the mail, and I can just back up my packages and reload the whole thing.

The error message says it's a segmentation fault, and the error codes in term are:

```
oomingmaks@ingram:~$ sudo gnomesword
Password:

** CRITICAL **: file e-splash.c: line 348 (e_splash_new): assertion `splash_image_pixbuf != NULL' failed.

Gtk-CRITICAL **: file gtkwidget.c: line 1427 (gtk_widget_show): assertion `widget != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkObject'

Gtk-CRITICAL **: file gtkobject.c: line 1161 (gtk_object_ref): assertion `object != NULL' failed.
Building GnomeSword interface

Gtk-WARNING **: invalid cast from (NULL) pointer to `ESplash'

** CRITICAL **: file e-splash.c: line 376 (e_splash_add_icon): assertion `splash != NULL' failed.

** CRITICAL **: file gdk-pixbuf.c: line 79 (gdk_pixbuf_unref): assertion `pixbuf != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `ESplash'

** CRITICAL **: file e-splash.c: line 376 (e_splash_add_icon): assertion `splash != NULL' failed.

** CRITICAL **: file gdk-pixbuf.c: line 79 (gdk_pixbuf_unref): assertion `pixbuf != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `ESplash'

** CRITICAL **: file e-splash.c: line 376 (e_splash_add_icon): assertion `splash != NULL' failed.

** CRITICAL **: file gdk-pixbuf.c: line 79 (gdk_pixbuf_unref): assertion `pixbuf != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `ESplash'

** CRITICAL **: file e-splash.c: line 376 (e_splash_add_icon): assertion `splash != NULL' failed.

** CRITICAL **: file gdk-pixbuf.c: line 79 (gdk_pixbuf_unref): assertion `pixbuf != NULL' failed.

Gtk-WARNING **: invalid cast from (NULL) pointer to `ESplash'

** CRITICAL **: file e-splash.c: line 411 (e_splash_set_icon_highlight): assertion `splash != NULL' failed.

GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertion failed, use IA__g_type_init() prior to this function

```

---

