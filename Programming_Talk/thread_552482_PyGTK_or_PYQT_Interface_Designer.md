---
title: "PyGTK or PYQT Interface Designer"
date: 2007-09-16
forum: Programming Talk
---

### Post by Sayers on 2007-09-16
Is there an interface designer for either to make my job a lot easier?

---

### Post by xtacocorex on 2007-09-16
For GTK+, you can use Glade to generate the XML file that pyGTK can parse to draw widgets.  Don't know about pyQT.

---

### Post by dugh on 2007-09-16
For pyqt (or rubyqt) you can use QT designer.

---

### Post by Sayers on 2007-09-16
but this doesn't allow me to take the design and then use it in my python code :(

---

### Post by xtacocorex on 2007-09-16
How does having pyGTK read an XML file and draw the UI widgets not do what you want to do?

It's very easy to generate the UI in Glade and then use some simple commands to connect signals for the interactive widgets in the Python code.  I've done it on this: [http://aeronerd.wordpress.com/projects/airfoil-generator/](http://aeronerd.wordpress.com/projects/airfoil-generator/) (no code available)

[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
This article helped me out a lot.

---

