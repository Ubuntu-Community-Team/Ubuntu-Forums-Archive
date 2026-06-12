---
title: "Creating GUI without an IDE"
date: 2007-04-04
forum: Programming Talk
---

### Post by M$LOL on 2007-04-04
I've created several command line programs that will work regardless of what platform they are on, using a text editor and gcc as opposed to an IDE.

Now I'm interested in creating a GUI, not anything too complicated, just maybe a window with a button to start with. I know that this is simple to do using an IDE such as Borland C++ Builder, but I'd like to learn how to do it myself, so that it doesn't use any APIs and therefore will give the same window whether it is executed on Windows or Linux.

I don't have any idea of how to do this, so I'm wondering if anyone could help me get started.

Thanks

---

### Post by xtacocorex on 2007-04-04
You could try WxWindows since it is cross platform.  I'm sure there are many tutorials for WxWindows online that don't require an IDE to create.  GTK and QT can also work on Windows.

The only GUI stuff I've done was with Python and GTK+ and that was to interface to a C++ program I had already written.

---

### Post by lnostdal on 2007-04-04
try [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) .. you'll need:

```

sudo aptitude install gnome-core-devel build-essential

```

edit:
under windows you've got [http://gladewin32.sourceforge.net/modules/news/](http://gladewin32.sourceforge.net/modules/news/) which contains the development libraries for gtk+ .. you can also use cygwin

---

### Post by trucutu31 on 2007-04-04
To start, you can adapt your command line programs adding a GUI. The buttons can launch some functions of the program for instance.

Concerning the API to choose, it depends on the language :
C : GTK, ...
C++ : Gtkmm, wxWidgets
Python : pyGtk, wxPython ...

You have to install the libraries (some are already on your system, such as tKinter/Python) , then use them in your program, and finally, compile with the good link options...

---

### Post by M$LOL on 2007-04-04
Thanks guys, I'll try that stuff and see what I can come up with :)

---

### Post by gpolo on 2007-04-04
First, C++ Builder generates a lot of extra code. 

If you expect to develop a nice GUI I would recommend using at max something that layouts the widgets (or windows if you use wxWidgets terminology) and generate a clean code. But, you can also do all the layout yourself, it isn't hard. 

You may use QT, wxWidgets, GTK+ ... like others said.

---

### Post by M$LOL on 2007-04-05
OK, I've started with GTK+ using the tutorial lnostdal provided, but that's for C, and most of my programming is C++. Do I need to change anything for GTKmm, or are the libraries etc I have on my system now OK and can I just start using the tutorial on gtkmm.org?

Also, what are the pros and cons of gtkmm and wxWidgets?

Thanks

---

### Post by lawentzel on 2007-04-06
What about using Glade Interface Designer?  That seems to do a lot of the work for you as well.  It is available through the Add/Remove option as well.

---

### Post by samjh on 2007-04-06
> **M$LOL said:**
> OK, I've started with GTK+ using the tutorial lnostdal provided, but that's for C, and most of my programming is C++. Do I need to change anything for GTKmm, or are the libraries etc I have on my system now OK and can I just start using the tutorial on gtkmm.org?

Also, what are the pros and cons of gtkmm and wxWidgets?

Thanks

If you want to use GTK+ with C++, then you need to go here:
[http://www.gtkmm.org/](http://www.gtkmm.org/)

---

### Post by M$LOL on 2007-04-06
OK, thanks.

---

### Post by alexandrul on 2007-04-06
[http://www.lazarus.freepascal.org/](http://www.lazarus.freepascal.org/)

"Write once compile everywhere!"

based on free pascal, the same source can be compiled on many platforms, including linux and windows

---

