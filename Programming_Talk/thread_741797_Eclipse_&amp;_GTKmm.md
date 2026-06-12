---
title: "Eclipse &amp; GTKmm"
date: 2008-04-01
forum: Programming Talk
---

### Post by dmendizabal on 2008-04-01
I've installed Eclipse-CDT, but I don't know how to integrate with GTK libs to build GTK+ and GTKmm applications.

Was any one succesfull with this?

---

### Post by kknd on 2008-04-01
> **dmendizabal said:**
> I've installed Eclipse-CDT, but I don't know how to integrate with GTK libs to build GTK+ and GTKmm applications.

Was any one succesfull with this?

Just adapt the standard way:

If in the terminal you compile with:

g++ *.cpp `pkg-config --cflags --libs gtkmm-2.4` -o out  

then

put

pkg-config --cflags gtkmm-2.4 in the flags section and
pkg-config --libs gtkmm-2.4 in the libs section.

It should work.

---

