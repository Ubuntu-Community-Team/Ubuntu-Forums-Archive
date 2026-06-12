---
title: "gtkmm question"
date: 2005-11-13
forum: Programming Talk
---

### Post by nuggien on 2005-11-13
Hello all,

I have a quick question about development with gtkmm.  I installed all the necessary gtkmm libs and downloaded calender.cc from the gtkmm examples in order to test if my setup was working.  I'm pretty sure it's finding the headers etc., and that the "as" error has something to do with the assembler?  

```

duc@nuggien:~/tmp/gtkmm-examples/calendar$ g++ calendar.cc `pkg-config gtkmm-2.4 --cflags --libs`
as: unrecognized option `-Qy'
duc@nuggien:~/tmp/gtkmm-examples/calendar$

```

the "pkg-config gtkmm-2.4 --cflags --libs" shows the following: 
```

duc@nuggien:~/tmp/gtkmm-examples/calendar$ pkg-config gtkmm-2.4 --cflags --libs
-I/usr/include/gtkmm-2.4 -I/usr/lib/gtkmm-2.4/include -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/gdkmm-2.4 -I/usr/lib/gdkmm-2.4/include -I/usr/include/pangomm-1.4 -I/usr/include/atkmm-1.6 -I/usr/include/gtk-2.0 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/lib/gtk-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/atk-1.0  -lgtkmm-2.4 -lgdkmm-2.4 -latkmm-1.6 -lgtk-x11-2.0 -lpangomm-1.4 -lglibmm-2.4 -lsigc-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lXrender -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
duc@nuggien:~/tmp/gtkmm-examples/calendar$

```

I can't really find where -Qy is anywhere in the options. 

Thanks in advance for any help!

---

### Post by nuggien on 2005-11-13
nevermind...the wrong assembler was in my path :(

I got it working now.

---

