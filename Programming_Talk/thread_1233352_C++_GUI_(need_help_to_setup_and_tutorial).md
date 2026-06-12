---
title: "C++ GUI (need help to setup and tutorial)"
date: 2009-08-06
forum: Programming Talk
---

### Post by xoron on 2009-08-06
hi

how do i make windowed application in c++ on Ubuntu. things like forms, combo boxes, buttons, etc.

which libraries do i need?
how i do install them?
and what is a good tutorial for this?

i use netbeans for c++. i know c++ as i learnt it from the [www.cpluscplus.com](www.cpluscplus.com) site in the last few days. but it didn't explain anything about forms.

thanks in advanced.

---

### Post by OutOfReach on 2009-08-06
Well there are many libraries available for GUIs, the two major toolkits are:
Qt (written in C++)
GTK (written in C, but has a C++ port called GTKmm)

I suggest you research both, plus there are a handful of topics around this forum about these two toolkits, but here's a basic run down:
- Qt is cross-platform and look native on all platforms (some may argue about GNOME, but it does indeed look native), and besides the fact that it's a GUI toolkit it also has many more libraries, such as a networking library and a translation library.

- GTK is also cross-platform and it can look somewhat-native on those platform (but looks horrid on Windows IMO). The original GTK is in C and isn't object oriented but GTKmm (C++ port) is, I believe. GTK is only a GUI toolkit, so it doesn't have extra libraries like Qt. And it is very lightweight.

Also note that there ARE other toolkits besides these out there, these are just the two major ones.

---

### Post by Habbit on 2009-08-06
Take into account that Qt does not use standard C++, but a specific pre-processing step called the Meta Object Compiler (moc). This can create a somewhat steep learning curve and some strange incompatibilities. For example, do not try to name a method "emit" on a Qt project.

---

### Post by rockballad on 2009-08-06
[Eclipse CDT]("www.eclipse.org/cdt/") is also a good tool for develop C++ app and GUI. It used to have VisualEditor helping us to design GUI visually, but I don't know the recently version of Eclipse supports which VE version. It's worth to take a look.

---

### Post by Mickeysofine1972 on 2009-08-08
Here's a qt tutorial I did last year :

[http://ubuntu-gamedev.wikispaces.com/Simple+GUI+Using+QT4](http://ubuntu-gamedev.wikispaces.com/Simple+GUI+Using+QT4)

Mike

---

