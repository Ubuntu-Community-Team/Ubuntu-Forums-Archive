---
title: "GNOME Development"
date: 2007-10-15
forum: Programming Talk
---

### Post by chris062689 on 2007-10-15
I want to start developing applications for the GNOME Desktop.
What's the most common programing language?

---

### Post by aaaantoine on 2007-10-15
This belongs in Programming Talk, but I'll bite.

The three most common languages for GNOME applications are likely to be C, C++, and Python.  The toolkit used to build applications for GNOME is called GTK, which has libraries for all three of these languages (and others).  Though designed primarily for GNOME, GTK applications can work in other X environments, and can even be ported to other operating systems.

For C, you want [GTK+](http://www.gtk.org).  For C++, you want [GTKmm](http://www.gtkmm.org).  For Python, you want [PyGTK](http://www.pygtk.org).  Each of the linked websites include tutorials.

Good luck!

---

### Post by Mickeysofine1972 on 2007-10-15
Its worth adding that if you are thinking of contributing to Ubuntu's gnome then the Ubuntu dev's prefer if you use Python

Mike

---

### Post by Sinister006 on 2007-10-15
I have just recently began writing applications in gnome as well. I have been using python with wxpython for the gui. So far its been pretty straight forward. wxpython is also cross platform from what I understand, although I haven't tested any of my apps in any other operating systems.

---

### Post by chris062689 on 2007-10-15
Would using wxpython a good idea?
I assume I wouldn't be getting the FULL support of the GNOME desktop, but would it be enough for doing most programs?

What can wxpython NOT do that pyGTK can do in GNOME?

[EDIT: Sorry I'm asking so many questions!  I think staying with pyGTK is the best option for me, I'll google around, thanks!]

---

