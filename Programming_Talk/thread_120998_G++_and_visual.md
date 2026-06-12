---
title: "G++ and visual"
date: 2006-01-24
forum: Programming Talk
---

### Post by GAW-Snow on 2006-01-24
I've been using microsoft visual .net for a while now.  What I'm wondering is does g++ support visual c++, like creating a window or button popup?  If not, which compiler that is available for ubuntu should I use?

Thanks.

---

### Post by superm1 on 2006-01-24
For tasks like that you might want to look more into scripting languages like python or perl with a gtk2 module add on.  It would really be a lot more simplistic then having to write a Gtk or QT gui or anything of the sort for a small app.

---

### Post by Viro on 2006-01-24
Firstly, you need to understand that Visual-C++ is a compiler. It takes C++ source code, and produces C++ programs. All those GUI creation tasks you talk about are to do with the Win32/MFC API and are separate from the compiler.

When you move to Linux, you'll find that Linux has all the tools of Visual C++. the only difference is, they aren't as well integrated as Visual C++ is. So, for compiling, you'll use GCC. For writing your code, you could use something like Gedit, or you can download Anjuta which is an IDE, similar to Visual C++. For designing your user interface, you could always use Glade, which IMHO provides a superior method of designing GUIs compared to Visual C++ ;).

---

### Post by Viro on 2006-01-24
[QUOTE=superm1]For tasks like that you might want to look more into scripting languages like python or perl with a gtk2 module add on.  It would really be a lot more simplistic then having to write a Gtk or QT gui or anything of the sort for a small app.[/QUOTE]

I honestly do not understand this fixation with Python or Perl :). If you use python/Perl with GTK modules, you are still writing a GTK app, no? How can using these languages be "more simplistic then having to write a Gtk or QT gui"? If I am confused by this, and what do you think the original poster is going to be? ;)

---

### Post by thumper on 2006-01-24
[QUOTE=Viro]I honestly do not understand this fixation with Python or Perl :). If you use python/Perl with GTK modules, you are still writing a GTK app, no? How can using these languages be "more simplistic then having to write a Gtk or QT gui"? If I am confused by this, and what do you think the original poster is going to be? ;)[/QUOTE]
My guess is that there is much less scaffolding for a scripting language :)

---

### Post by GAW-Snow on 2006-01-24
I need to do this in c++ because I'm working on an experiment and the driver for the device I'm using is written in c++.  I am currently using visual .net for it but I was just wondering if I could do the same tasks in linux.  

With that said, could someone give me more details on what is available for this task in ubuntu?  Remember that you are talking to a physicist, not a programmer.  Please don't assume I'm going to understand all the programming jargon that I often see you people use :)

---

### Post by superm1 on 2006-01-24
So.... let me get this straight - you are looking to port a *device driver *to your linux box and have no programming experience?  Lets start out with what this device is, what it does and what you need your driver to do and such.

---

### Post by GAW-Snow on 2006-01-24
That's not the part I want to know.  Getting the driver to work and have my computer collect the data is no problem.  As a matter of fact, I have no problem doing what I wanted to do using microsoft.  What I'm asking is what kind of program I would use for the visual affects and if there's any difference in the code at all.

Yes, I have lots of experience in programming, but it's mostly computational and numerical simulations.  I haven't done much visual, especially linux.

---

### Post by toojays on 2006-01-24
I would recommend that you look at what you want to do as a two step process:

1) Remove your program's dependency on MFC. You would do this by using a cross platform library instead of MFC. Qt and wxWidgets are the most popular cross-platform toolkits. Both of these toolkits work with Visual C++ as well as gcc, so you could do this part of the development with Visual C++ to minimize your headaches. See [Migrating from MFC to Qt](http://www.trolltech.com/products/qt/migrate/mfc.html) and [Introduction to wxWidgets](http://www.wxwidgets.org/intro.htm).

2) Once your app no longer depends on MFC, then port it from Windows to GNU/Linux. This will involve replacing Windows API calls with calls to wxWidgets/Qt or POSIX system calls. If you follow some guidelines for portable programming, you can end up with a program which can be built for Windows or for GNU/Linux just by changing a flag in your Makefile.

---

