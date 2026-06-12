---
title: "Best option for making a GUI"
date: 2011-09-21
forum: Programming Talk
---

### Post by lifelike27 on 2011-09-21
Hey guys,

I wanted to know which language/kit I should use to make a UI to make a basic application. Something that I can use later on for more complicated stuff. For now, I just want to make a basic UI for my application.

I'm planning on writing my code in python. I know that you can create a GTK UI with python but would it be the best for future purposes?

---

### Post by Smart Viking on 2011-09-21
> **lifelike27 said:**
> Hey guys,

I wanted to know which language/kit I should use to make a UI to make a basic application. Something that I can use later on for more complicated stuff. For now, I just want to make a basic UI for my application.

I'm planning on writing my code in python. I know that you can create a GTK UI with python but would it be the best for future purposes?

Yea sure, all you need is there.

The only disadvantage is bad documentation, gtk with C has good documentation, but not gtk with python. You will likely look through C documentation to find solutions to your problems. Other than that it's fine.

---

### Post by lifelike27 on 2011-09-21
I've never made a GUI before so it's going to be a new experience. Is there any benefit for sticking with a python based UI as apposed to C?

Would putting C UI and python code be a problem as well?

Sorry for the noobish questions, we all have to learn some how. :p

---

### Post by juancarlospaco on 2011-09-21
search for python-dialog, Tkinter or HTML5.

Choose the one you like more, python dialog is easy, as Tk, HTML5 is very cool.

---

### Post by jwxie on 2011-09-21
There are many different libs that you can use in Python, but I think for most GUIs, Java is usually recommended. If you are comfortable with Python, go with Python. 
A little time investment is all that you need :p
Bad or good? If you are very good you can even contribute by writing features for those libs as well.

---

### Post by JDShu on 2011-09-21
I've found that there is enough documentation to write applications with pygtk. You might want to take a look at glade as well. A bit finicky and there are some gaps you have to fill in with educated guesses, but it's doable.

---

### Post by cgroza on 2011-09-21
I write my GUI applications with wxPython. Never needed something else.

---

### Post by karlson on 2011-09-21
> **lifelike27 said:**
> I've never made a GUI before so it's going to be a new experience. Is there any benefit for sticking with a python based UI as apposed to C?

Would putting C UI and python code be a problem as well?

Sorry for the noobish questions, we all have to learn some how. :p

You can choose your poison as there are many options available including for Python.

I personally prefer QT as a toolkit, but GTK will work just as well.  I do like the QT Designer actually better then Glade(may be there is some other GTK layout designer but I haven't tried them), and as far as I remember PyQT used to be able to do Python Code directly from the UI file that QT designer produces.

In the end choice will ultimately be yours but if you are just starting out I would suggest starting with the designer and try to have something automated generate Python or C or C++ code for you so you can actually see what's being done before you jump head first into doing it all yourself.

P.S. If you are just starting out I would suggest doing some light reading before coding.
QT has some good books that helped me:
[http://developer.qt.nokia.com/books/view/c_gui_programming_with_qt_4_2nd_edition_the_official_c_qt_book](http://developer.qt.nokia.com/books/view/c_gui_programming_with_qt_4_2nd_edition_the_official_c_qt_book)

P.P.S.  I know I sound like a walking advertisement so don't shoot.

---

### Post by lifelike27 on 2011-09-21
Wow, there are a lot of mixed opinions here! I think I'll do a bit of reading on Qt and wxPython/pyGTK to finally choose one. I've heard of a lot of applications that use Qt so I'm a bit more interested in that.

One last question, would packaging my program into a deb file be a problem of sort for the end user? Basically, I want to make it as simple as possible for a person using my application, to install it with the least number of dependencies needed to run the application. 

Python 2.7 is pre-installed on Ubuntu as far as I know, so I'm guessing wxPython or pyGTK wouldn't need extra dependencies, but what about Qt?

---

### Post by karlson on 2011-09-21
> **lifelike27 said:**
> 
One last question, would packaging my program into a deb file be a problem of sort for the end user? Basically, I want to make it as simple as possible for a person using my application, to install it with the least number of dependencies needed to run the application. 


I would suggest get your application written before you start thinking about packaging.

> 
Python 2.7 is pre-installed on Ubuntu as far as I know, so I'm guessing wxPython or pyGTK wouldn't need extra dependencies, but what about Qt?

You might want to check on this.  QT is installed if you are using KUBUNTU, if you are using a server you may not even have a GTK.

---

### Post by lykwydchykyn on 2011-09-21
> **lifelike27 said:**
> 
Python 2.7 is pre-installed on Ubuntu as far as I know, so I'm guessing wxPython or pyGTK wouldn't need extra dependencies, but what about Qt?

Just install python-qt4 to start with.  There's also python-qt4-phonon, python-qt4-gl, and python-qt4-dbus if you need those libraries (for sound, advanced graphics, and desktop integration, respectively).

---

