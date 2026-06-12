---
title: "Non terminal programs"
date: 2008-12-12
forum: Programming Talk
---

### Post by DrPepper836 on 2008-12-12
Is there a way to write a program that opens up in a window (like firefox) in C++ using the Geany compiler? So far, all it seems to be able to do is run in the terminal for me.

---

### Post by escapee on 2008-12-12
Have you written the program to utilize a library to create windows?  If not, you should read up on libraries such as GTK+, QT, or even just using X11 to draw the windows.

---

### Post by nvteighen on 2008-12-13
You need a GUI toolkit (or just directly interfacing to X11, but that will be more complicated). If you want a GNOME look-and-feel, use GTK+. If you want a KDE look-and-feel, Qt. Search for the development packages at Synaptic and also the documentation, as they're huge APIs (you just learn the basics and then learn by need).

Keep in mind that GTK+ is written in C and Qt in C++... so they're designed to work natively with that languages. But, you have GTK+ bindings for C++ and Python, e.g. and Qt, too (AFAIK, sadly, not for C).

---

