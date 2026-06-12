---
title: "gtk/gtkmm programming"
date: 2008-05-10
forum: Programming Talk
---

### Post by MDSmith2 on 2008-05-10
Wheres a good tutorial, what packages do i need, etc.

Thanks

---

### Post by Lux Perpetua on 2008-05-10
For GTK: libgtk2.0-dev

For gtkmm: libgtkmm-2.4-dev

There is a passable gtkmm tutorial on the gtkmm website ([www.gtkmm.org](www.gtkmm.org)). I'm sorry to say the documentation for gtkmm is not very good, but the documentation for GTK itself is better (and also applies somewhat to gtkmm), so having both handy, you might be okay.

---

### Post by MDSmith2 on 2008-05-10
when i compile this```
/*
*File name: window.c
 */

#include <gtk/gtk.h>
#include <glib.h>

int main (int argc, char *argv[])
{
  /*-- Declare the GTK Widgets used in the program --*/
  GtkWidget *window;

  /*--  Initialize GTK --*/
  gtk_init (&argc, &argv);

  /*-- Create the new window --*/
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  /*-- Display the window --*/
  gtk_widget_show(window);

  /*-- Start the GTK event loop --*/
  gtk_main();

  /*-- Return 0 if exit is successful --*/
  return 0;
}

```

i get this```
michael@mdsmiths:~/Desktop$ g++ test.cpp
test.cpp:5:21: error: gtk/gtk.h: No such file or directory
test.cpp:6:18: error: glib.h: No such file or directory
test.cpp: In function ‘int main(int, char**)’:
test.cpp:11: error: ‘GtkWidget’ was not declared in this scope
test.cpp:11: error: ‘window’ was not declared in this scope
test.cpp:14: error: ‘gtk_init’ was not declared in this scope
test.cpp:17: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
test.cpp:17: error: ‘gtk_window_new’ was not declared in this scope
test.cpp:20: error: ‘gtk_widget_show’ was not declared in this scope
test.cpp:23: error: ‘gtk_main’ was not declared in this scope


```
any idea?

---

### Post by WW on 2008-05-10
What command did you use to compile your program?

The section "[Compiling Hello World](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)" of the [GTK+ 2.0 Tutorial](http://library.gnome.org/devel/gtk-tutorial/stable/) show a typical command used to compile a simple GTK program.

---

### Post by MDSmith2 on 2008-05-10
thanks but i found the problems.
for future googlers:
1: I used g++ test.cpp `pkg-config gtkmm-2.4 --cflags --libs` instead of g++ test.cpp
2: the header file is gtkmm.h not gtkmm.
thanks for the help.

---

### Post by dmendizabal on 2008-07-07
> **MDSmith2 said:**
> when i compile this```
/*
*File name: window.c
 */

#include <gtk/gtk.h>
#include <glib.h>

int main (int argc, char *argv[])
{
  /*-- Declare the GTK Widgets used in the program --*/
  GtkWidget *window;

  /*--  Initialize GTK --*/
  gtk_init (&argc, &argv);

  /*-- Create the new window --*/
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  /*-- Display the window --*/
  gtk_widget_show(window);

  /*-- Start the GTK event loop --*/
  gtk_main();

  /*-- Return 0 if exit is successful --*/
  return 0;
}

```

i get this```
michael@mdsmiths:~/Desktop$ g++ test.cpp
test.cpp:5:21: error: gtk/gtk.h: No such file or directory
test.cpp:6:18: error: glib.h: No such file or directory
test.cpp: In function ‘int main(int, char**)’:
test.cpp:11: error: ‘GtkWidget’ was not declared in this scope
test.cpp:11: error: ‘window’ was not declared in this scope
test.cpp:14: error: ‘gtk_init’ was not declared in this scope
test.cpp:17: error: ‘GTK_WINDOW_TOPLEVEL’ was not declared in this scope
test.cpp:17: error: ‘gtk_window_new’ was not declared in this scope
test.cpp:20: error: ‘gtk_widget_show’ was not declared in this scope
test.cpp:23: error: ‘gtk_main’ was not declared in this scope


```
any idea?


I haven't worked with Gtk+ but Gtkmm. In any case, it seems to be a problem with missing namespaces.
Try: Gtk::GtkWidget instead of just GtkWidget
Try: Gtk::gtk_init instead of just gtk_init, etc.

Or you can just include the following line on top (before main()):

using namespace Gtk;

---

### Post by haTem on 2008-07-08
> **dmendizabal said:**
> I haven't worked with Gtk+ but Gtkmm. In any case, it seems to be a problem with missing namespaces.
Try: Gtk::GtkWidget instead of just GtkWidget
Try: Gtk::gtk_init instead of just gtk_init, etc.

Or you can just include the following line on top (before main()):

using namespace Gtk;

Unlike gtkmm, gtk+ does not use namespaces. It is written in C which does not have namespaces (gtkmm wraps it in C++ and makes use of namespaces, classes, etc). His problem was simply forgetting to tell the compiler where to look for the gtk header files.

---

