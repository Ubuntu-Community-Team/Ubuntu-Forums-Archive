---
title: "Need Help Compiling Gnome/C Program in Hardy Heron"
date: 2008-06-29
forum: Programming Talk
---

### Post by Strike Team on 2008-06-29
I'm attempting to compile this program, taken from a book:

[i]#include <gnome.h>

int main(int argc, char* argv[])
{
GtkWidget *app;
gnome_init ("example", "0,1", argc, argv);
app=gnome_app_new(("example", "Hello!");
gtk_widget_show(app);
return(0);
}[/i]

I use the following command, taken from the book:

* gcc gnome1.c -o gnome1 'gnome-config --cflags --libs guomeui'*

I get the following error messages:

[i]gcc: gnome-config --cflags --libs guomeui: No such file or directory
gnome1.c:1:19: error: gnome.h: No such file or directory
gnome1.c: In function ‘main’:
gnome1.c:5: error: ‘GtkWidget’ undeclared (first use in this function)
gnome1.c:5: error: (Each undeclared identifier is reported only once
gnome1.c:5: error: for each function it appears in.)
gnome1.c:5: error: ‘app’ undeclared (first use in this function)
gnome1.c:7: error: expected ‘)’ before ‘;’ token
gnome1.c:10: error: expected ‘;’ before ‘}’ token[/i]

gnome.h is located in /usr/include/libgnomeui-2.0 on my system.

How do I get gcc to locate gnome.h and use gnome-config? All help appreciated.

---

### Post by geirha on 2008-06-29
gnome-config is installed by the [libgnome-dev](apt:libgnome-dev) package, so make sure you have that one installed.

EDIT:
Also, I see you got the quotes wrong. 
```
gcc gnome1.c -o gnome1 'gnome-config --cflags --libs guomeui'
```
You are using regular quotes while you should be using backquotes
```
gcc gnome1.c -o gnome1 `gnome-config --cflags --libs gnomeui`
```

---

### Post by xlinuks on 2008-06-29
Strike Team looks like you're using an old book, what year is it?

---

### Post by Strike Team on 2008-06-29
Thanks geirha, it works now.

The book is from 1999. I should really get something more up-to-date.

---

### Post by xlinuks on 2008-06-29
Well, that's it. I read a similar post like yours on the ubuntu forums, there also was a guy with such an issue like yours and he has been told to look for a newer book, because "gnome-config" is obsolete, people use "pkg-config", please do a google search on how exactly to compile such issues nowadays. I also hope you're reading about Gtk 2.0 rather than 1.2 (but since the book is from 1999 I'm pretty sure you're learning (very) old stuff).

---

### Post by xlinuks on 2008-06-29
Here's what a guy says (a post from 2003):
> 
...
> Where is gnome-config hiding in Gnome 2?
The separate *-config scripts are obsolete; with GNOME2 one uses
pkg-config ([http://www.freedesktop.org/software/pkgconfig/](http://www.freedesktop.org/software/pkgconfig/)), e.g.
"pkg-config --cflags --libs libgnome-2.0".

Here's the post itself which contains a link to more pkg-config info:
[http://osdir.com/ml/linux.debian.devel.gtk-gnome/2003-07/msg00060.html](http://osdir.com/ml/linux.debian.devel.gtk-gnome/2003-07/msg00060.html)

---

