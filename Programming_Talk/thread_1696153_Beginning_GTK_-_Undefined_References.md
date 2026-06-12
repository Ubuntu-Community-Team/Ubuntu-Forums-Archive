---
title: "Beginning GTK - Undefined References"
date: 2011-02-27
forum: Programming Talk
---

### Post by Skidbladnir on 2011-02-27
I'm trying to learn how to use the C++ GTK library.  I've tried with GTKMM, but it's not working.  I've also used gtk.h.  I'm developing in C++ eclipse.  Now, with an EXTREMELY basic script (11 lines) it will include gtk.h, but it says undefined reference to gtk_init.  Please.  Help.  HELP.  HHHEEELLLPPP.  :(

---

### Post by mali2297 on 2011-02-27
Make sure that you have the packages [build-essential]("http://packages.ubuntu.com/maverick/build-essential") and [libgtk2.0-dev]("http://packages.ubuntu.com/maverick/libgtk2.0-dev") installed.

You also need to link GTK+ and its companion libraries when compiling. In a terminal, you should be able to compile your program with the command
```

g++ -o yourprog yourprog.cpp `pkg-config gtk+-2.0 --cflags --libs`

```
There is probably an easy way to link the necessary libraries in Eclipse as well, but I have never used that application.

---

### Post by Skidbladnir on 2011-02-27
*Headdesk*  How come none of the other g++ commands for compiling this didn't work?  >_>  Anyway, thank you.  :)

---

