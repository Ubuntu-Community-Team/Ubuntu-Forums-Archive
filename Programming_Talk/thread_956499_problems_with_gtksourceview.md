---
title: "problems with gtksourceview"
date: 2008-10-23
forum: Programming Talk
---

### Post by Ulrik04 on 2008-10-23
hi all

I'm currently making a C++/GTK+ application, where I want to use the GtkSourceView. I installed the libgtksourceview2.0-dev installed, and in some examples and in the gedit source code I've seen that you include it with #include <gtksourceview/gtksourceview.h>, but when I do that it tells me that it can't find it.
I looked into usr/include, and noticed that the gtksourceview folder is inside a "gtksourceview-2.0" folder, but when I include #include <gtksourceview-2.0/gtksourceview/gtksourceview.h>, it gives errors from the included file that it can't find a file that's in the gtksourceview folder.
Then I tried to copy the gtksourceview folder to usr/include, and now it can include, but when I tries to call a function, it gived me a "undefined reference to gtk_source_view_new()" error, but I know that it can see the functions, because when I call it with other arguments, it's telling me that the arguments of gtk_source_view_new() is wrong.

What am I doing wrong? And how do I install and use gtksourceview? :confused:

---

### Post by bruce89 on 2008-10-23
[LIST=1]
[*]GTK+ is C, not C++, if you want to use C++, use [gtkmm]("http://www.gtkmm.org/")
[*]You need to use [FONT="Monospace"]pkg-config[/FONT], probably [FONT="Monospace"]gcc -Wall `pkg-config --cflags --libs gtksourceview-2.0` -o out in.c[/FONT]
[/LIST]

---

### Post by mali2297 on 2008-10-23
As mentioned, you need to tell the compiler to link against the library. Try
```

g++ yoursourcefile.cc `pkg-config --cflags --libs gtksourceview-2.0` 

```
Check the man page of pkg-config for more information.

---

### Post by Ulrik04 on 2008-10-23
Thanks a lot, the compile option was everything i needed :D

And BTW I know that GTK+ is for C and GTKMM for C++, but I like the C++ functions and GTK+ setup and it's working fine... :P

Thanks again :D

---

### Post by cabalas on 2008-10-23
A while ago I did a blog post about getting syntax highlighting working with gtksourceviewmm-2.0 and giomm, I know your using the C libraries but the code shouldn't be hard to translate.

[http://mlowen.com/?p=15](http://mlowen.com/?p=15)

I don't know if need/want it, but I thought it might be helpful.

---

