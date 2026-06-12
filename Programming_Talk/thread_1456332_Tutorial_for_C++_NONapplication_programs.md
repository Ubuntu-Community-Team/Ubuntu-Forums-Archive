---
title: "Tutorial for C++ NONapplication programs???"
date: 2010-04-17
forum: Programming Talk
---

### Post by hakermania on 2010-04-17
I have found thousands of tutorials for C++ console applications, but what I want is a tutorial which tells you how to make a window program
I have a preference on QtCreator and its Designer
Thank you

---

### Post by cdekter on 2010-04-17
[http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html)

Took 10 seconds to find that on Google using "QT C++ tutorial"

---

### Post by nvteighen on 2010-04-17
"Non-application program"? I'd interpret that to mean a library, which is a program that can't be executed on its own... The term is "GUI application".

Ok, the basic idea is the following: you use libraries that already have all the X-Window interfacing done and provide you with basic graphical elements ("widgets") and facilities like a ready-to-use event and signalling system, etc. These libraries usually work in an OOP design: everything is usually a class.

So, Qt is one of these libraries and it's natively written in C++. GTK+ is another, natively written in C, but there's a binding for C++ called gtkmm. wxWidgets is another one for C++, but it's kinda special, as it's just a layer that calls the native underlying library... this is really handy if you plan to develop a cross-platform (including Windows) application.

The GUI designer IDEs make you not to write the boring GUI layout code in your text editor, but they won't (unlike Visual Basic does) allow you to introduce functionality code in them. These designers usually create an XML-based file you then have to load into your C++ code using a library (IIRC, Qt does this too, unlike GTK+).

---

### Post by Drone022 on 2010-04-17
There's a book available online for free, just google "C++ GUI programming with QT4". You should be able to download the first edition.

---

### Post by hakermania on 2010-04-17
Thank you for your answers guys!
The truth is that i never search for "Qt GUI" I searched about C++ non-application programs and I found nothing!
Thank you for your answers!

---

