---
title: "curses or ncurses"
date: 2009-05-19
forum: Programming Talk
---

### Post by lavinog on 2009-05-19
I am looking into making some python console based utilities using a curses interface.

By importing curses am I importing ncurses?
Is it common to refer to ncurses as just curses?
Is there a difference between the two?

---

### Post by geirha on 2009-05-19
ncurses is curses, one of several implementations of curses. The curses python module is a python implementation of curses which is made to be very similar to ncurses, it does not use ncurses or any other curses library.

EDIT: Oops, looking a bit closer, it **does** use the ncurses library, at least in Ubuntu.

---

### Post by nvteighen on 2009-05-19
curses was a UNIX library that developed into a standard now implemented by ncurses ("NewCurses") plus some little extensions. Python's curses module is just a wrapper to the ncurses library, which is written in C (libncurses.so). It's basically the same you get with PyGtk and GTK+, actually...

---

### Post by lavinog on 2009-05-19
Thanks for clearing that up

---

