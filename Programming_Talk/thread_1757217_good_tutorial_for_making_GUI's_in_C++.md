---
title: "good tutorial for making GUI's in C++?"
date: 2011-05-13
forum: Programming Talk
---

### Post by u-noob-tu on 2011-05-13
ive been teaching myself C++ for about 4 months now, but ive hit a wall. the problem is that i have no money due to the lack of a job, so i can neither buy books on C++ nor go to a class. until now i have relied on free tutorials online, converting web pages into PDF's so i can take them on the road. i havent been able to find a good tutorial on creating an actual interface for a program, like a GUI, something i could interact with. i use Anjuta IDE to write my programs (fantastic IDE), which has a glade interface plugin, but i dont know how to use it. any tips and suggestions will be much appreciated.

---

### Post by TeoBigusGeekus on 2011-05-13
See [this]("http://developer.gnome.org/gtkmm-tutorial/2.99/").

---

### Post by nvteighen on 2011-05-13
In essence, what you use is a library that gives you the required tools to create a GUI if some graphical display is available. This is valid for all major OSes.

In GNU/Linux, as usual, we've got several options (freedom!). The two "Big ones" are GTK+ and Qt. GTK+ is natively a C library, but it has official bindings for several languages; the C++ one is called Gtkmm. Qt is natively a C++ library, also with official bindings for several languages (except C, for obvious reasons).

There's no important advantage of one with respect to the other, actually. They both follow their own respective philosophy, but none is "better" than the other when doing GUIs. The only huge difference between GTK+ and Qt is that Qt also includes a lot of features not related to GUI programming, but for general C++ programming because this library was created before the C++ STL. Most of those features are now unnecessary, as people just go with the STL.

GNOME's official toolkit is GTK+; KDE's is Qt. But this is irrelevant for you unless you want your program to be part of any of the DEs' official application suite. Both GTK+ and Qt are designed to work with the X Window System, so as long as the DE is running on it, your program will work regardless what toolkit you've chosen (obviously, the toolkit has to be installed).

So, I suggest you to refer to GTK+'s and Qt's websites for tutorials. TeoBigusGeekus has already pointed you to the Gtkmm one; here you'll find the official Qt one: [http://doc.trolltech.com/4.7/tutorials.html](http://doc.trolltech.com/4.7/tutorials.html)

---

### Post by bouncingwilf on 2011-05-13
The gtkmm tutorial is "sparse and incomplete" to say the least, the GTK+ tutorial is far better but for C. Qt seems better documented but as a C user myself,I don't know it well.


Bouncingwilf

---

### Post by stchman on 2011-05-13
> **u-noob-tu said:**
> ive been teaching myself C++ for about 4 months now, but ive hit a wall. the problem is that i have no money due to the lack of a job, so i can neither buy books on C++ nor go to a class. until now i have relied on free tutorials online, converting web pages into PDF's so i can take them on the road. i havent been able to find a good tutorial on creating an actual interface for a program, like a GUI, something i could interact with. i use Anjuta IDE to write my programs (fantastic IDE), which has a glade interface plugin, but i dont know how to use it. any tips and suggestions will be much appreciated.

If you are going to be making GUIs using C or C++ you need to decide which environment you are going to make the GUI for.

Windows - win32
OS X - Cocoa
Gnome - GTK+
KDE - Qt

Each environment has their own API.  If you are wanting to make GUIs in Linux using Gnome then GTK+ is the way to go.  If you install the GTK+ environment in Windows then you can run GTK+ apps.

There are GTK+ GUI makers out there most notably Glade.  

This is where Java has the edge as long as the computer has a valid JRE then the GUI commands are the same across the board.

---

### Post by cgroza on 2011-05-13
Take a look at wxWidgets, I have some experience in it and I recommend it.

---

### Post by krazyd on 2011-05-14
> **stchman said:**
> If you are going to be making GUIs using C or C++ you need to decide which environment you are going to make the GUI for.

Windows - win32
OS X - Cocoa
Gnome - GTK+
KDE - Qt

Each environment has their own API.  If you are wanting to make GUIs in Linux using Gnome then GTK+ is the way to go.

This is incorrect. Qt can use the native toolkit to render the GUI on OS X, Gnome, KDE and Windows. All you have to do is recompile for the target OS - and on linux it can use the native GTK+ style automatically.

Cross platform information is here:
[http://doc.qt.nokia.com/latest/developing-with-qt.html](http://doc.qt.nokia.com/latest/developing-with-qt.html)
And the widget gallery:
[http://doc.qt.nokia.com/latest/gallery.html](http://doc.qt.nokia.com/latest/gallery.html)

> **stchman said:**
> This is where Java has the edge as long as the computer has a valid JRE then the GUI commands are the same across the board.
There is no real advantage over Qt here. You still need a natively compiled JRE, whereas you could just natively compile your app.

Really, for C++ GUI programming, nothing comes close to Qt.

---

