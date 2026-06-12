---
title: "Advice on GUI platform"
date: 2009-04-19
forum: Programming Talk
---

### Post by reizencroft on 2009-04-19
Hi I'm a game programmer. Mostly, I program portable console games and some openGL stuff. I also had experience with Visual Basic 6.0 and a little on Visual Studio 2003(using MFC)(about 3 years ago). Aside from some console applications, I don't have any other programming experience with GUI stuffs.

I am planning to make some game tools which will be run primarily in Ubuntu and can be also run on different ditros and possibly windows, though portability to is optional. Can you give me advice on what platform can I develop my application? I'm considering wxwidgets, but I also want to consider other possible options. Portable is good, but I would prefer one that have good support with 3D rendering. 

Thanks

---

### Post by simeon87 on 2009-04-19
If Ubuntu is your primary platform then GTK+ ([http://www.gtk.org/](http://www.gtk.org/)) could also be an option (it's used for many applications). I don't have experience with OpenGL in Gtk but here's link: [http://gtkglext.sourceforge.net/](http://gtkglext.sourceforge.net/) (it's used in various projects: [http://gtkglext.sourceforge.net/users](http://gtkglext.sourceforge.net/users)).

---

### Post by samjh on 2009-04-19
GTK+, Qt, and wxWidgets all support OpenGL.

Juding by your reference to MFC, I'm guessing your target language is C++.

GTK+ is written in C, although there are C++ bindings available for it (GTKmm).  It is multi-platform, and attempts to emulate the look-and-feel of the native operating system by using various themes.  It is very popular and has widespread support, although its documentation is relatively lacking (but steadily improving).

Qt is written in C++, and is perhaps the most well-documented and supported multi-platform development framework for C++.  It is available on Windows, Mac, and X11-based platforms (Unix, Linux, etc.).  For the GUI component, it emulates the look-and-feel of the native operating system by mixed use of drawing functions native to the operating system or themes.  Aside from the GUI, Qt is also a library for multi-threading, database transactions, networking, security, multimedia, and more.

wxWidgets is also written in C++.  It is more verbose than Qt to achieve the same type of task.  It is well-documented, but popularity is somewhat less than GTK+ and Qt these days.

---

### Post by reizencroft on 2009-04-19
Thanks for the replies.

My target language is C. I can use C++, but im not very comfortable with it. And I think i'll be going with GTK+.

---

### Post by Firestom on 2009-04-19
I suggest you use C++ if you want to program a game. C++ is object-oriented and objects are safer/more-readable/easier to maintain than structures and functions. Also, C includes templates and lots of other concepts that avoid you to rewrite code over and over.

Being familiar with Qt, I would suggest it. However, it is meant to create windows and not games. For games, I suggest SDL a/o SFML in 2D and OpenGL in 3D. OpenGL is a Qt plugin and can be set up without too much hardships. Here is a good tutorial in using OpenGL with Qt: [http://www.digitalfanatics.org/projects/qt_tutorial/chapter14.html]("http://www.digitalfanatics.org/projects/qt_tutorial/chapter14.html")

The main advantage in Qt is that it also includes other plugins for various things to do, from XML to Multimedia (Phonon) and you can even create a web browser (by including WebKit) without much effort.

---

### Post by reizencroft on 2009-04-19
I'm only planning to make game tools, not actual games. And I do program games using C++. 

Thanks for the link. Seeing that page, swayed me to use Qt. 

But which one is faster to learn, Qt or GTK+? Which is much easier to port to Windows?

---

### Post by samjh on 2009-04-19
> **reizencroft said:**
> I'm only planning to make game tools, not actual games. And I do program games using C++. 

Thanks for the link. Seeing that page, swayed me to use Qt. 

But which one is faster to learn, Qt or GTK+? Which is much easier to port to Windows?

In my experience, I found Qt faster to learn, even though my knowledge of C++ is only basic.  Documentation is exceedingly good.  Start with the tutorials.

Documentation for Qt 4.4 (Ubuntu 8.10): [http://doc.trolltech.com/4.4/index.html](http://doc.trolltech.com/4.4/index.html)

Documentation for Qt 4.5 (Ubuntu 9.04): [http://doc.trolltech.com/4.5/index.html](http://doc.trolltech.com/4.5/index.html)

For porting to Windows, again, Qt is easier - far easier - than GTK.  The Qt SDK for Windows provides you with Qt Creator IDE, which takes care of all project management and build processes.  Even if you develop using only command-line tools in Linux, you can literally copy-paste the Qt .pro file and source files into Windows, open the .pro file using Qt Creater, and build.  Package the relevant DLL files with your program's installer or archive, and your program is ready for distribution.  Very simple.

---

### Post by Firestom on 2009-04-19
The Qt framework is the most well-documented I've seen. All functions/signals/slots/static members/etc... are all listed on the class page. 

Also, Qt uses the platform's display functions, it does not try to emulate the look and feel of it.

So Qt is the best choice for GUIs IMHO. Left is to know if you will like it.

---

### Post by NintenDave on 2009-04-20
If C is your target language, I don't think Qt is an option.

The hello world example uses C++ classes: [http://doc.trolltech.com/3.3/tutorial1-01.html](http://doc.trolltech.com/3.3/tutorial1-01.html)

And if you're going to use C++, then I wouldn't go for Qt since it seems only loosely based on C++ without taking full use of the language. GTKmm seems to take a lot of C++'s advantages and is better for it, IMO.

If you're going to use C then I think it should be GTK+ all the time, because it's just so extremely powerful.

---

### Post by scourge on 2009-04-20
> **NintenDave said:**
> And if you're going to use C++, then I wouldn't go for Qt since it seems only loosely based on C++ without taking full use of the language. GTKmm seems to take a lot of C++'s advantages and is better for it, IMO.

Lol. Qt is fully based on C++. It just extends the language a bit, but still generates valid C++ which can be compiled with almost any C++ compiler. Mostly the difference is just the signals and slots system, which is great compared to callbacks.

---

### Post by samjh on 2009-04-20
> **NintenDave said:**
> And if you're going to use C++, then I wouldn't go for Qt since it seems only loosely based on C++ without taking full use of the language. GTKmm seems to take a lot of C++'s advantages and is better for it, IMO.That is a misunderstanding by some C++ purists.

As Scourge said, Qt has some features which extend C++'s capabilities.  This is done for signals and slots, and is almost transparent to the developer, as it merely involves typing Q_OBJECT in the header file of a custom widget class.  If you don't use custom widgets, it's not even necessary.

Also, the link you posted points to Qt 3.3, which was released in the first-quarter of 2004!  The current Qt version is 4.5. :)

The current "hello world" is:
```
#include <QtGui/QApplication>
#include <QtGui/QLabel>
 
int main(int argc, char *argv[])
{
    QApplication app(argc, argv);
    QLabel label("Hello, world!");
    label.show();
    return app.exec();
}
```

Having said all that, let the OP decide. :)

If he wants to use only C, then GTK+ is the logical solution.  If he doesn't mind using C++, then Qt is as good as any alternative, if not better.

---

