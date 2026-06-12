---
title: "Gtkmm"
date: 2006-08-19
forum: Programming Talk
---

### Post by yatt on 2006-08-19
What do I need to compile C++ code that includes gtkmm.h? As of now g++ returns:
```
error: gtkmm.h: No such file or directory
```
I have installed libgtkmm-2.4-dev, libgtkmm-2.4-1c2a, libgtkmm-2.0-dev, libgtkmm-2.4.1c2a. What have I missed?

EDIT:Nevermind, figured it out myself. Needed to add more to the g++ command. Guess I should have read a little further down the tutorial's page.

---

### Post by GreenVoid on 2007-10-29
Well, if you have figured it out, would you please be so kind as to post it here?

---

### Post by amio_098 on 2009-04-02
may be what you need is linking the gtk library. like:
g++ x.cpp -o x -lgtk

---

### Post by SledgeHammer_999 on 2009-04-02
From the FAQ [link](http://gtkmm.org/docs/gtkmm-2.4/docs/FAQ/html/index.html#id2523031) you need to use ```
g++ source.cpp `pkg-config gtkmm-2.4 --libs --cflags` -o program_name
```

---

