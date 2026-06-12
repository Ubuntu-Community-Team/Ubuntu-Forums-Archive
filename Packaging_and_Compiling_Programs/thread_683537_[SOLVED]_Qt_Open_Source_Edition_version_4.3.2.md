---
title: "[SOLVED] Qt Open Source Edition version 4.3.2"
date: 2008-01-31
forum: Packaging and Compiling Programs
---

### Post by frankos44 on 2008-01-31
I am an experienced LAMP programmer with good OOP skills but limited C, C++ skills.

I have just installed "Qt Open Source Edition version 4.3.2" and it looks very good. I assume the code I write should reside outside of QT4 but not sure where or how.

The challenge for me is to create a GNOME desktop application using QT4.

What would be nice is a simple "Hello world"  example running on a form created by QT4.

Does anyone have something like this?

---

### Post by luisromangz on 2008-01-31
Gnome apps are written using GTK+, you can't have Gnome integration using Qt, or at least it would be so difficult. KDE apps are written using Qt, and you can write Qt apps that doesn't deppend on any desktop environment.

Besides I'm sure you can find tutorials on QT4 on the web, or you could buy the book "Programming with Qt4" which is quite good.

---

### Post by frankos44 on 2008-01-31
Thanks for the reply.

I just found a pile of examples on the QT website, not sure how I missed that first time around.

The example apps I downloaded and compiled seem to run OK on GNOME all the same? then again they are fairly simple apps.

Is there a GUI form designer for GNOME available?

---

### Post by dsplabs on 2008-01-31
You could use [Trolltech's Qt Designer]("http://trolltech.com/products/qt/features/designer"). A simple walk-through for compiling Qt Designer .ui files into executable binaries is shown here: [Qt GUI example using Qt4 Designer .ui file]("http://linux.dsplabs.com.au/forums/qt-programming/qt-gui-example-using-qt4-designer-ui-file-t26.html").

---

