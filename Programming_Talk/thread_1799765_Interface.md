---
title: "Interface"
date: 2011-07-08
forum: Programming Talk
---

### Post by shashanksingh on 2011-07-08
This may sound pretty naive, but I really want to make a small app for ubuntu (not too big or professional, mainly for a learning curve and mostly for personal use), which helps compressing my images by giving me most of the funtionalities of the convert command, using a GUI for lots of image files will be more convenient than a script shell. But I have no idea where to begin with, I only know a liitle shell programming. For the GUI, will I need to do something on the QT interface???

Some guidance would really help.

Thanks

---

### Post by r-senior on 2011-07-08
Python and wxPython, PyGTK or PyQT4 would probably be your quickest route. Good tutorials here:

[http://zetcode.com/](http://zetcode.com/)

---

### Post by Habitual on 2011-07-08
zenity/yad too...

---

### Post by nvteighen on 2011-07-08
> **shashanksingh said:**
> This may sound pretty naive, but I really want to make a small app for ubuntu (not too big or professional, mainly for a learning curve and mostly for personal use), which helps compressing my images by giving me most of the funtionalities of the convert command, using a GUI for lots of image files will be more convenient than a script shell. But I have no idea where to begin with, I only know a liitle shell programming. For the GUI, will I need to do something on the QT interface???


Actually, a well-designed command line program could allow you to process lots of images more easily than a GUI can: via command line arguments, pipes and all the sorts of I/O capabilities there are available for shell scripts/CLI apps, you could ask the program to process a list of files with just a single command.

Also, GUI programming using bash is tough because bash is a shell, i.e. it calls executables. And GUIs are based on libraries, not executables. So you're limited to what zenity or yad can give you, which is basic dialog interaction and not much more. If you're thinking in a full fledged "normal" GUI, you'll have to use a general programming language that supports interfacing with the GTK+ or Qt libraries, either natively or through some binding.

---

### Post by shashanksingh on 2011-07-12
Thank you all.
I guess Ill start with the basics of python and then Qt,

Any amazing e-books/tutorials you could suggest??
for Python and QT??

---

### Post by Bachstelze on 2011-07-12
[http://www.amazon.com/dp/0132354187](http://www.amazon.com/dp/0132354187)

---

### Post by shashanksingh on 2011-07-14
One question..
What is the difference between Qtk and Gtk?
Which one would better suit my needs?

---

### Post by Bachstelze on 2011-07-14
I don't know what Qtk is. If you mean Qt, Qt and Gtk are just different toolkits. From my experience, Qt seems bigger and more powerful, and Gtk smaller and simpler. Ultimately, the choice is yours, both will probably work for you.

---

### Post by PaulM1985 on 2011-07-14
People have suggested python but Java has a few image processing functions available that you could use instead of having to do your own:

[http://download.oracle.com/javase/1,5.0/docs/api/java/awt/image/BufferedImageOp.html](http://download.oracle.com/javase/1,5.0/docs/api/java/awt/image/BufferedImageOp.html)

Paul

---

### Post by cgroza on 2011-07-14
Did you take wxPython in consideration?

---

### Post by juancarlospaco on 2011-07-14
zenity, yad, gtkdialog

---

### Post by cgroza on 2011-07-14
> **juancarlospaco said:**
> zenity, yad, gtkdialog
I don't know about the others, but zenity is quite limiting in terms of flexibility.

---

### Post by shashanksingh on 2011-07-15
No, wXpython? Didnt know about it.

Btw, which UI library does gnome use? Is gnome all made in C++??

---

### Post by cgroza on 2011-07-15
> **shashanksingh said:**
> No, wXpython? Didnt know about it.

Btw, which UI library does gnome use? Is gnome all made in C++??
wxPython is kind of a wrapper around the native toolkit and API. So your applications "fit"
in every environment. Eg. It will integrate seamlessly into KDE, Windows and GNOME.
wxPython is just a binding for wxWidget which is written in C++, just as Qt and pyQT.


All I know is that Gtk is written in C if this is what you asked.

---

### Post by JupiterV2 on 2011-07-15
> **cgroza said:**
> Did you take wxPython in consideration?

I think cgroza gets paid to promote wxWidgets. LOL!

First off, it's about looks. Qt and GTK+ are the two main graphical toolkits for Linux. There are many more but they are the "big two." Qt is the bases for the KDE desktop and GTK+ for Gnome. wxWidgets uses "native" widgets for each platform. Meaning, on Linux it uses GTK+, Windows the Windows API, OSX it's Quartz (or whatever it's called). Qt and wxWidgets are developed in C++ and GTK+ in C. They all have python bindings, meaning you can develop UI's using Python's native syntax. It's not about making a wrong choice, it's about making the right choice for you. Each of them have their own strengths and weaknesses.

---

### Post by cgroza on 2011-07-15
> **JupiterV2 said:**
> I think cgroza gets paid to promote wxWidgets. LOL!



I just want to share my joy with others.:p

---

### Post by nvteighen on 2011-07-16
> **shashanksingh said:**
> 
Btw, which UI library does gnome use? Is gnome all made in C++??

GNOME uses GTK+ as the library for its official applications, but nothing prevents you to use any other library, as long as it's compatible with the X Window System.

GTK+ is written in C and most of GNOME's core applications also are. But there's an official GTK+ C++ binding called Gtkmm, which is used by programs as unknown as OpenOffice.org or Mozilla Firefox ;)

---

### Post by shashanksingh on 2011-07-17
> **nvteighen said:**
> GNOME uses GTK+ as the library for its official applications, but nothing prevents you to use any other library, as long as it's compatible with the X Window System.

GTK+ is written in C and most of GNOME's core applications also are. But there's an official GTK+ C++ binding called Gtkmm, which is used by programs as unknown as OpenOffice.org or Mozilla Firefox ;)

> **JupiterV2 said:**
> I think cgroza gets paid to promote wxWidgets. LOL!

First off, it's about looks. Qt and GTK+ are the two main graphical toolkits for Linux. There are many more but they are the "big two." Qt is the bases for the KDE desktop and GTK+ for Gnome. wxWidgets uses "native" widgets for each platform. Meaning, on Linux it uses GTK+, Windows the Windows API, OSX it's Quartz (or whatever it's called). Qt and wxWidgets are developed in C++ and GTK+ in C. They all have python bindings, meaning you can develop UI's using Python's native syntax. It's not about making a wrong choice, it's about making the right choice for you. Each of them have their own strengths and weaknesses.

Thank you.

---

