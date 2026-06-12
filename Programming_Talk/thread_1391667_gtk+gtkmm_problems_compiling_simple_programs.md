---
title: "gtk+/gtkmm problems compiling simple programs"
date: 2010-01-27
forum: Programming Talk
---

### Post by boxnapper on 2010-01-27
Hey, I'm new here, so I'll say hello first.

I know  basic c++. I want to start learning OpenGL, but I need to learn a GUI. I've chosen GTK+/GTKmm. Mostly, I want to learn GTKmm, because I'm a c++ programmer.

Moreover, I keep trying to compile a file(rhymes--lol), but it doesn't want to find the directories & compile. This is really hindering the pace I want to keep with learning.

Here is some code & quotes from my terminal.

Beforehand, if any more info is needed, just ask.


What I type into my terminal.

> g++ -Wall -o simple simplegtk.cpp `pkg-config --libs --cflags libgtk2.0-dev`


This is what the output is.

> Package libgtk2.0-dev was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgtk2.0-dev.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgtk2.0-dev' found
simplegtk.cpp:1:19: error: gtkmm.h: No such file or directory
simplegtk.cpp:3: error: ‘Gtk’ has not been declared
simplegtk.cpp:3: error: expected constructor, destructor, or type conversion before ‘kit’
simplegtk.cpp:5: error: ‘Gtk’ has not been declared
simplegtk.cpp:5: error: expected constructor, destructor, or type conversion before ‘window’
simplegtk.cpp:7: error: ‘Gtk’ has not been declared
simplegtk.cpp:7: error: expected constructor, destructor, or type conversion before ‘(’ token



This is the code I'm trying to compile.

```
#include <gtkmm.h>

Gtk::Main kit(argc, argv);

Gtk::Window window;

Gtk::Main::run(window);



```

If I'm using the code right, I'm not sure. I got it from the GTKmm [documentation]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en").

---

### Post by Some Penguin on 2010-01-27
Just to get this out of the way:  you *have* installed the dev package (libgtk2.0-dev) and not just libgtk, right?  Where "foo" and "foo-dev" are both available, it usually means that the header files are only in the dev (because you don't need the header files at runtime, normally -- just the libraries and any configuration files and the like).

---

### Post by dwhitney67 on 2010-01-27
> **boxnapper said:**
> 
This is the code I'm trying to compile.

```
#include <gtkmm.h>

Gtk::Main kit(argc, argv);

Gtk::Window window;

Gtk::Main::run(window);

```

If I'm using the code right, I'm not sure. I got it from the GTKmm [documentation]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-basics-simple-example.html.en").
EDIT:

I just realized that you indicated that you wanted to do C++ development.  Regular GTK should be avoided, and in lieu of it, GTK+ should be used.  I think you are aware of this, but the reference material you are using is not appropriate.

Here's a link to a tutorial for GTK+ (2.0):
[http://library.gnome.org/devel/gtk-tutorial/2.17/](http://library.gnome.org/devel/gtk-tutorial/2.17/)

As for the pkg-config, you want to specify "gtk+-2.0" as the package name, not "libgtk2.0-dev".

---

### Post by SledgeHammer_999 on 2010-01-27
install libgtkmm-2.4-dev and compile with:
```
g++ -Wall -o simple simplegtk.cpp `pkg-config --libs --cflags gtkmm-2.4`
```

Yuo should read the cocs more carefully. Your link mentions how to compile with Gtkmm at the end of the page.

---

### Post by boxnapper on 2010-01-27
Ok thanks.

---

### Post by boxnapper on 2010-01-27
Thanks a lot guys. It worked, and now I can learn this stuff(gtk).

---

