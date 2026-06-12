---
title: "Gtk and python usage in Ubuntu"
date: 2007-12-28
forum: Programming Talk
---

### Post by pettersolberg on 2007-12-28
Hi,
I've read that Ubuntu makes high usage of python. I'm a hobbyist programmer, I've spent some time sticking to python already and I would like to learn developing some GUI applications.
 
Currently I'm fighting the wxWidgets and boa constructor in order to get some kind of a python GUI application.

I would like kindly to ask the developers of Ubuntu and other programmers, if that's a good choice or maybe there are some better ways to do start it?

In the past I've been programming under Windows  using Borland's / CodeGear's C++ Builder / Turbo C++ (wow, so many names) and MS C# WindowsForms.

---

### Post by MicahCarrick on 2007-12-28
For RAD (Rapid Application Development), Python and GTK or PyGTK is an excellent choice. Using Glade to design the interface and Python to implement said interface can make desktop application development quick and easy.

Being that you have some C++ experience, you could use C++ for GTK development as well.

I have just finished the first part of a tutorial on GTK+ application development which covers using Glade 3. I'm currenly working on the next portions which will implement the design (a basic text editor) using Python and C (code is written and will be posted today, tutorial portion explaining the code will come later).

[GTK+ and Glade3 GUI Programming Tutorial - Part 1]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

To see a very, very simple implementation of a GTK+ application in C which uses an interface designed in Glade, check out this post: [Very, very simple example using libglade]("http://www.gtkforums.com/about187.html")

A very thorough PyGTK tutorial can be found here: [PyGTK 2.0 Tutorial]("http://www.moeraki.com/pygtktutorial/pygtk2tutorial/index.html")

---

### Post by Majorix on 2007-12-28
I am a C&Python programmer currently trying to shift to Java. Java is very similar to C++ in syntax. Netbeans has nice code completion and GUI builder tools integrated, so you shouldn't have much hard time.

If you choose to go the Python way anyways, I would suggest that you stick with wxPython. It's portable and has native looks. And there are not much difference in different GUI toolkits, so level of difficulty shouldn't be an issue at this time. Yet another *and*, wxGlade is an excellent tool at creating GUIs with wxPython.

I don't have much experience with PyGTK and therefore don't want to mislead you, so I won't comment on it. But yeah, you should use wxPython and not PyGTK.

---

### Post by engla on 2007-12-28
I think using Python is the primary thing to produce (smallish) applications for GNU/Linux. If wxWidgets works fine and you know it, perhaps you should continue to use it. I've only used pygtk (for [kupfer]("http://users.student.lth.se/f04us/wiki/kupfer/") and [dragbox]("http://users.student.lth.se/f04us/wiki/dragbox/"), two very small utilities), and it works nicely. I've also begun to use the underlying gobject stuff with signals and so which is handy for your application. (I did a very nice of refactoring of dragbox to use gobject signals all across the application, it made the whole design much more modular and the data and view separation better. The proof was that I could easily afterwards implement most of my todo list on top of the refactoring (still in git))

Also gobject stuff tie in nicely with dbus python bindings etc. All of this could be used at the same time as wxWidgets though.

---

