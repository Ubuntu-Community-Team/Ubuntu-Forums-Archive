---
title: "installing gtk2+, poppler, glib, etc."
date: 2013-02-08
forum: Programming Talk
---

### Post by lkdsajf on 2013-02-08
Hi,

just tried to install some libraries, GTK and poppler to be precise.

First of all, is it normal that I need to set the search paths manually in the IDE? I think I can recall not having to do this (way back), used to be automated, but correct me if I'm wrong. Well, now I searched the files I wanted to include and set the paths myself.

Now I'm trying to link the libs to the program, though the linker doesn't seem to find the lib gtk2.0+... This is just annoying, did I do something wrong? I thought Ubuntu was all about usability. Installing things and just start working. Now I've been ******* around for 3 hours just to compile this program: [http://www.gtkforums.com/viewtopic.php?t=3421](http://www.gtkforums.com/viewtopic.php?t=3421) and haven't gotten anywhere ... [FONT=Courier New]cannot find -lgtk2.0+[/FONT]
But I DID install gtk2.0-dev so what's the issue? I'm quite new to developing on linux, and it's already a pain... The reason BTW for not using GTK3 is, that cairo apparently can't handle that, the devs destroyed backwards-compability somehow.
After having installed libpoppler-dev I noticed there is no poppler.h anywhere in /usr/ (as I've said, I had to search for every header) ... compiled poppler myself, but have uninstalled it again. I must have done something wrong here (please enlighten me :p), it can't be that a dev-package doesn't contain the headers needed to use the library, can it?

If this is not too much to ask, can anyone just tell me what packages from the repository I need to install and which additional commands might be necessary to set up the libraries?

Any kind of help is MUCH appreciated.

Regards,
Paul

EDIT: Also, Why do I need to use aptitude to find these dev-packages. Isn't the software center supposed to do that? Can't find any useful software, and it looks like it's just there to promote commercial stuff.

---

### Post by steeldriver on 2013-02-08
Hello and welcome

Which IDE? iirc when I played with gtk in geany it was sufficient to use 

```
`pkg-config --libs gtk+-2.0`
```in the 'Build Commands' section. 

Also, remember that link order is significant.

---

### Post by lkdsajf on 2013-02-08
A thousand kisses to You, Sir! I am speechless. 

As I've said, I used linux way back and never came across this pkg-config witchcraft. Is this the answer to all questions? pkg-config? Can I use the same magic to tell my IDE (CodeBlocks it is, btw) where to look for header files?

Please don't be angry at me for saying Ubuntu is not user-friendly. 

I need to go home and rethink my life.

---

### Post by steeldriver on 2013-02-08
Well, there's a comment at the top of the source code file you linked saying to use

 ```
gcc `pkg-config --cflags --libs gtk+-2.0 poppler-glib` -o pdfviewer pdfviewer.c
```However this doesn't work on some (recent?) versions of the build environments because it places the pkg-config expanded libs ahead of the source file: 

```
$ gcc `pkg-config --cflags --libs gtk+-2.0 poppler-glib` -o pdfviewer pdfviewer.c
/tmp/ccJ0vEOb.o: In function `on_destroy':
pdfviewer.c:(.text+0x7): undefined reference to `gtk_main_quit'
/tmp/ccJ0vEOb.o: In function `on_expose':
pdfviewer.c:(.text+0x1d): undefined reference to `gdk_cairo_create'
pdfviewer.c:(.text+0x34): undefined reference to `poppler_page_render'
pdfviewer.c:(.text+0x3f): undefined reference to `cairo_destroy'
/tmp/ccJ0vEOb.o: In function `main':
pdfviewer.c:(.text+0x88): undefined reference to `gtk_init'
pdfviewer.c:(.text+0xa8): undefined reference to `poppler_document_new_from_file'
pdfviewer.c:(.text+0xd1): undefined reference to `g_object_unref'
pdfviewer.c:(.text+0xf0): undefined reference to `poppler_document_get_page'
pdfviewer.c:(.text+0x117): undefined reference to `g_object_unref'
pdfviewer.c:(.text+0x12e): undefined reference to `poppler_document_get_n_pages'
pdfviewer.c:(.text+0x153): undefined reference to `gtk_window_new'
pdfviewer.c:(.text+0x170): undefined reference to `g_type_check_instance_cast'
pdfviewer.c:(.text+0x19c): undefined reference to `g_signal_connect_data'
pdfviewer.c:(.text+0x1b5): undefined reference to `g_type_check_instance_cast'
pdfviewer.c:(.text+0x1e1): undefined reference to `g_signal_connect_data'
pdfviewer.c:(.text+0x1f5): undefined reference to `gtk_widget_set_app_paintable'
pdfviewer.c:(.text+0x201): undefined reference to `gtk_widget_show_all'
pdfviewer.c:(.text+0x206): undefined reference to `gtk_main'
pdfviewer.c:(.text+0x213): undefined reference to `g_object_unref'
pdfviewer.c:(.text+0x220): undefined reference to `g_object_unref'
collect2: ld returned 1 exit status
$

```You should find that it works if you split the --cflags part and the --libs part and put the --libs after your .c file(s):

```
$ gcc **`pkg-config --cflags gtk+-2.0 poppler-glib`** -o pdfviewer pdfviewer.c **`pkg-config --libs gtk+-2.0 poppler-glib`**
$ ./pdfviewer
Useage: pdfviewer <uri>
$
```Hope this helps

---

### Post by lkdsajf on 2013-02-08
Works like a charm. Thank you so, so much.

---

### Post by steeldriver on 2013-02-08
You're welcome

FYI if your IDE doesn't support shell expansions directly, you can just run pkg-config in a terminal and then copy + paste the output e.g.

```
$ pkg-config --libs gtk+-2.0 poppler-glib
-lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lpango-1.0 -lfreetype -lfontconfig -lpoppler-glib -lgobject-2.0 -lcairo -lglib-2.0

```

---

