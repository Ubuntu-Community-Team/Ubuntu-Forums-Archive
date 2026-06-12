---
title: "[Python]"
date: 2009-06-15
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-15
ok i want to create a little alarm clock program with python so i need something like boa constructor... but boa constructor creates kinda ugly gui... i need a more stylish gui that i can design better like the visual studio ... unfortuantely thats not for python or linux... any suggestions?

---

### Post by simeon87 on 2009-06-15
You could use PyGTK; then you can design the gui in GLADE.

---

### Post by xZachtmx on 2009-06-15
ok looks good! so i downloaded Glade from add/remove and i downloaded pygtk-2.14.1.tar.gz            but i dont know how to install it so it works with glade?

---

### Post by monraaf on 2009-06-15
Pygtk is in the repositories, and is probably already installed on your system since a lot of standard programs depend on it, so no need to use tarballs...

Basically what you do is you design the UI with Glade and add signal handlers to the widgets, Glade will save the description of your UI to an XML file.

Then in your code, you load the XML file, connect to the signal handlers and add more functionality to it.

---

### Post by xZachtmx on 2009-06-15
ok ill look for some tutorials... looking preety cool thanks guys:D

---

### Post by HydroModeler on 2009-06-15
I found these tutorials very helpful:

[http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/](http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/)

---

