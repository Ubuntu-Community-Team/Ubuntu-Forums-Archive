---
title: "GTK tutorial: &quot;No such file&quot;"
date: 2007-12-11
forum: Programming Talk
---

### Post by tunelabguy on 2007-12-11
I have installed libgtk2.0-dev using synaptic (ubuntu 7.10) with no errors.  Now I am trying to compile the simple test program in the GTK Tutorial from [http://www.gtk.org/tutorial:](http://www.gtk.org/tutorial:)

  #include <gtk/gtk.h>
  int main( int   argc, char *argv[] )
  {
      GtkWidget *window;
      gtk_init (&argc, &argv);
      window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
      gtk_widget_show  (window);
      gtk_main ();
      return 0;
  }

using the command:

  gcc base.c -o base `pkg-config --cflags --libs gtk+-2.0`

where base.c is the program shown,  But I get the error:

gcc: pkg-config --cflags --libs gtk+-2.0: No such file or directory
base.c:1:21: error: gtk/gtk.h: No such file or directory
base.c: In function ‘main’:
base.c:6: error: ‘GtkWidget’ undeclared (first use in this function)
base.c:6: error: (Each undeclared identifier is reported only once
base.c:6: error: for each function it appears in.)
base.c:6: error: ‘window’ undeclared (first use in this function)
base.c:10: error: ‘GTK_WINDOW_TOPLEVEL’ undeclared (first use in this function)

This is all right out of the Tutorial, How am I supposed to set up the environment to compile this program, and why did the Tutorial lead me astray?

Robert Scott
Ypsilanti, Michigan

---

### Post by geirha on 2007-12-11
You've probably got the backticks wrong. there's a difference between '' and ``. Instead of `` however, you can use $() so try:
```
gcc $(pkg-config --cflags --libs gtk+-2.0) -o base base.c
```

What it actually does is run the command:```
pkg-config --cflags --libs gtk+-2.0
``` and uses the output of that command as arguments to gcc

---

### Post by tunelabguy on 2007-12-11
> **geirha said:**
> ...so try:
```
gcc $(pkg-config --cflags --libs gtk+-2.0) -o base base.c
```


Thanks, that was it!  I finally have a GUI program that I can run.

Robert Scott
Ypsilanti, Michigan

---

### Post by ario on 2010-06-29
I used this command in my geany compiler to build the file:
```
gcc -Wall -o "%e" "%f" `pkg-config --cflags --libs gtk+-2.0`
```
And it solved the problem. Remember that ` is back quote and it's usual position is on the left of the '1' key and on top of TAB key on keyboard and it's not the single quote ' sign.
Also gtk+-2.0 must be written not gtk+2.0 or gtk-2.0. Which I've seen in some forums.
Hope this helps.

---

### Post by geirha on 2010-06-29
> **ario said:**
> Remember that ` is back quote and it's usual position is on the left of the '1' key and on top of TAB key on keyboard and it's not the single quote ' sign.

That's one of the reasons the $(...) syntax for command substitution is preferred over `...` [http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

---

### Post by nasrulaz on 2012-11-03
Thanks, it works for me

---

