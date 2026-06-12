---
title: "Python GUI"
date: 2008-05-10
forum: Programming Talk
---

### Post by zodiac123 on 2008-05-10
Hi, I'm a student programming in python - mainly console programs and one pygame project. In general my code tends to be ~500 lines.

I'm aware of widget toolkits like Tk which create GUI widgets, but I've tried Tk and don't like it - someone told me it's not particularly good. Does anyone know good alternatives, and what are your experiences in using them?

---

### Post by ssam on 2008-05-10
PyGTK is pretty good. you can either create and arange widgits programtically or you can use glade to make the interface.

---

### Post by Kadrus on 2008-05-10
there is also [wxpython]("http://www.wxpython.org/") which is very good...i suggest trying it out..check out this [tutorial]("http://zetcode.com/wxpython")

---

### Post by Can+~ on 2008-05-10
When working with GUI toolkits you will always have that problem, a truck load of declarations that are used once. Try using a separated file for interfaces. I use Python + Glade3 for that.

Also, try splitting your code in modules.

---

### Post by LaRoza on 2008-05-10
The sticky has a link to GUI programming in Linux (my wiki also has a section for it)

---

### Post by dtmilano on 2008-05-11
[autoglade]("http://autoglade.sourceforge.net/") may be to you, take a look at it.

---

### Post by MicahCarrick on 2008-05-12
I am also a fan of PyGTK. I have a tutorial ([_GTK+ and Glade3 GUI Programming Tutorial - Part 1_]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")) which gives a thorough overview of using Glade 3 to build a GUI without discussing the language yet. Although I haven't yet finished part 3 which will discuss coding the GUI, the complete source of the final application (a text editor) is available in both C and Python.

The python Wiki has a large list of GUI toolkits you can use for Python: [http://wiki.python.org/moin/GuiProgramming]("http://wiki.python.org/moin/GuiProgramming")

---

### Post by xelapond on 2008-05-13
I like PyQt, personally.  If you are working with KDE Qt is definitely the way to go, though it also runs in Gnome.

---

### Post by stevescripts on 2008-05-13
> **zodiac123 said:**
> Hi, I'm a student programming in python - mainly console programs and one pygame project. In general my code tends to be ~500 lines.

I'm aware of widget toolkits like Tk which create GUI widgets, but I've tried Tk and don't like it ...


A serious question, absolutely not meant to be flame-bait. (and I invite responses from all concerned, not just the OP).  If you don't want to respond in this forum, feel free to send e-mail.

What is it that you do not like about Tk?  (in this case Tkinter...)

Is it an appearance issue for you, or a usage issue?

The tcl/tk community continues to strive to improve the appearance of the Tk widget set, particularly on Linux.

Steve

---

### Post by solarwind on 2008-05-13
I have used PyQT and I like it. It's easy to use and works well with python. I'm sure PyGTK is just as good, but I don't know how to use Glade properly.

---

### Post by Senesence on 2008-05-15
Another vote for wxPython.

It's cross-platform, features plenty of widgets, and is relatively easy to learn and use.

It's also very well documented, and there are even video tutorials for it:
[http://showmedo.com/videos/series?name=PythonWxPythonBeginnersSeries](http://showmedo.com/videos/series?name=PythonWxPythonBeginnersSeries)

---

### Post by days_of_ruin on 2008-05-15
pyGTK is good.

---

