---
title: "C++ includes and dependencies issues with glib"
date: 2010-06-08
forum: Programming Talk
---

### Post by FiberOptix on 2010-06-08
Hey all,

First, I caution you that I'm a complete beginner with C++ so please bear with me. In case you're wondering, I'm trying to use the Gwyddion libraries. I suspect that there are very few people viewing this thread that have some experience with them, but I hope I'm wrong.

The gwyddion libraries depend heavily on glib. After installing libglib-2.0, I note that the header files can be found in /usr/include/glib-2.0, which I have to link in the Makefile with -I so that g++ can find all the other header files when I #include <glib-2.0/glib.h>. However, even when I #include <glib-2.0/glib.h> I still find that g++ complains about certain types i.e. "&#8216;guint32&#8217; does not name a type" and "&#8216;GQuark&#8217; has not been declared." Further, it still can't locate some of it's own header files "/usr/include/glib-2.0/glib/gtypes.h:34:24: error: glibconfig.h: No such file or directory" 

None of the posted examples with the libraries I'm trying to use actually work, and it's mostly due to these sorts of errors. Since I'm unfamiliar with standard practices with respect to this sort of thing with C++, I think I must be missing something fairly big.

Any help is much appreciated, thanks!

---

### Post by nvteighen on 2010-06-09
> **FiberOptix said:**
> Hey all,

First, I caution you that I'm a complete beginner with C++ so please bear with me. In case you're wondering, I'm trying to use the Gwyddion libraries. I suspect that there are very few people viewing this thread that have some experience with them, but I hope I'm wrong.

The gwyddion libraries depend heavily on glib. After installing libglib-2.0, I note that the header files can be found in /usr/include/glib-2.0, which I have to link in the Makefile with -I so that g++ can find all the other header files when I #include <glib-2.0/glib.h>. However, even when I #include <glib-2.0/glib.h> I still find that g++ complains about certain types i.e. "‘guint32’ does not name a type" and "‘GQuark’ has not been declared." Further, it still can't locate some of it's own header files "/usr/include/glib-2.0/glib/gtypes.h:34:24: error: glibconfig.h: No such file or directory" 

None of the posted examples with the libraries I'm trying to use actually work, and it's mostly due to these sorts of errors. Since I'm unfamiliar with standard practices with respect to this sort of thing with C++, I think I must be missing something fairly big.

Any help is much appreciated, thanks!

From what I've researched, Gwyddion uses pkg-config, which is a tool designed to help in these situations, by managing all library and header dependencies of a certain library.

So, it seems that this would work:
```

g++ -o output source.cpp $(pkg-config --cflags --libs gwyddion)

```

Don't worry "--cflags", although it oddly refers to C, it just handles the header files.

---

### Post by SledgeHammer_999 on 2010-06-09
I think the correct include is "#include <glib.h>"
You should install the "libglib2.0-dev" package under Ubuntu 10.04. It contains all the necessary headers(hence the -dev suffix).
Almost all projects use the pkg-config utility to pass the correct compiler/linker flags(check google for pkg-config).
See here on how to use glib + pkg-config-->[http://library.gnome.org/devel/glib/stable/glib-compiling.html](http://library.gnome.org/devel/glib/stable/glib-compiling.html)

(Also are you aware of the C++ bindings? They're part of gtkmm and are called glibmm)

---

### Post by tchakabam on 2011-07-06
On a typical system like Ubuntu 10.4 you will have to include these directories :

 - /usr/include/glib-2.0
 - /usr/lib/glib-2.0/include 

It is important to include the second one to have glibconfig.h in your path which is critical for system specific typedefs to work.

For gcc i.e g++ this means using the following compiler flags:

-I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -lglib-2.0  

which is equivalent to inserting `pkg-config --cflags --libs glib-2.0`
in to the compiler call.

When developing, if you know where your header files are located you can use an explicit call, sometimes it is good to know what`s behind pkg-config and certain includes dirs.

---

