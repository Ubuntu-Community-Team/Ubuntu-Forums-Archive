---
title: "Python 3 Graphics how to."
date: 2011-02-02
forum: Programming Talk
---

### Post by VietCanada on 2011-02-02
I used to program in Amigabasic. I'm interested in learning Python. I've installed what I believe to be the latest Python. I use Ubuntu 10.10 64bit.

My question.

I want to build a database and the GUI to access it. In Amaigabasic I did this by hand I guess. That is I used polygons, circles and lines to draw my GUI and other commands to make some areas sensitive to mouse clicks. Can I do this with Python?
 
I've been searching for tutorials with no luck so far.

Any advice?

I really don't like Visual basic or related software that lets users point and click their way to a program. I want to write the program from scratch.

Thanks.

---

### Post by fct on 2011-02-02
Sure you can do that with Python, using a library like pyglet:

[http://www.pyglet.org/doc/programming_guide/graphics.html](http://www.pyglet.org/doc/programming_guide/graphics.html)

If you change your mind there are nice graphical toolkits like Qt and GTK with Python interfaces that are not as easy as Visual Basic but will save lots of graphics development.

---

### Post by juancarlospaco on 2011-02-02
Tk

---

### Post by VietCanada on 2011-02-03
Thanks fct. I'll look at it and see if I can do it.  At first glance it looks pretty logical. I guess I need to install pyglet  from the Software centre since typing <python3.1> in a Terminal and pasting in 

pyglet.graphics.draw(2, pyglet.gl.GL_POINTS,
    ('v2i', (10, 15, 30, 35)),
    ('c3B', (0, 0, 255, 0, 255, 0))
)resulted in an error and a message that it did not recognise pyglet.

juancarlospaco- Thanks for the recommendation. First I'll try it 'by hand'. Or do you mean that tk allows for this as well? I thought it was a GUI creating package that utilises existing windows and buttons. I want to make my own.

---

### Post by raydeen on 2011-02-03
Not to sway you from Python (it's my weapon of choice lately) but since you've worked in a dialect of BASIC before you might want to give Gambas a spin. It's similar to MS Visual Basic (not an exact copy though) but it has a built in interface creator that might speed up your dev time. There's also Lazarus/Free Pascal which is the spiritual successor to Borland's Delphi. I like to lean towards Lazarus as it's cross platform whereas Gambas is Linux only.

---

### Post by oldfred on 2011-02-03
I used MS Access a lot with sql queries hand coded (or copied from qry tool) into the code, so I learned sql and vba coding.

But I do not have Access at home and wanted to learn how to do similar programs in Linux. I tried Gambas and it seemed pretty good but I wanted to learn python. 

I started with python, and gtk and did get a simple db in sqlite to work - create, edit & update. I am now tried the same thing in qt.

It seems you can in qt create an updatable tableview very easily, where in gtk I had to had code a lot of things. But it looks like if I want the same control as I had in gpt I will have to hand code similar to what I did in gtk. Still learning the qt version.

[http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)
Recipes, sample code
[https://help.ubuntu.com/community/PythonRecipes](https://help.ubuntu.com/community/PythonRecipes)
[http://code.activestate.com/recipes/langs/python/](http://code.activestate.com/recipes/langs/python/)
Byte of Python
[http://www.cesarkallas.net/arquivos/apostilas/python/doc/byteofpython_120.pdf](http://www.cesarkallas.net/arquivos/apostilas/python/doc/byteofpython_120.pdf)
Dive into python
[http://diveintopython.org/](http://diveintopython.org/)
Python - Think like a computer scientist
[http://openbookproject.net//thinkCSpy/](http://openbookproject.net//thinkCSpy/)
Richard G Baldwin Programming Tutorials
[http://www.dickbaldwin.com/tocpyth.htm](http://www.dickbaldwin.com/tocpyth.htm)

Editors - I like Geany:
Too many choices but many are free so you can try them
[http://wiki.python.org/moin/PythonEditors](http://wiki.python.org/moin/PythonEditors)

builder - I used Glade to create view for GTK app
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
builder definitions
[http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html](http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html)
py faqs builder
[http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp](http://faq.pygtk.org/index.py?req=show&file=faq13.039.htp)

I used qtdesigner for view in qt
[http://zetcode.com/tutorials/pyqt4/](http://zetcode.com/tutorials/pyqt4/)
[http://doc.trolltech.com/4.6/qabstracttablemodel.html](http://doc.trolltech.com/4.6/qabstracttablemodel.html)
qtdesigner image viewer code
[http://www.harshj.com/2010/04/page/2/](http://www.harshj.com/2010/04/page/2/)

[http://www.wellho.net/mouth/2746_Model-View-Controller-demo-Sqlite-Python-3-Qt4.html](http://www.wellho.net/mouth/2746_Model-View-Controller-demo-Sqlite-Python-3-Qt4.html)
copied into geany & chgd to pyqt and it runs:
[http://blog.rburchell.com/2010/02/pyside-tutorial-model-view-programming_22.html](http://blog.rburchell.com/2010/02/pyside-tutorial-model-view-programming_22.html)

---

### Post by VietCanada on 2011-03-16
Just posting to thank people for their advice and suggestions. It's much appreciated.

I was derailed somewhat using the latest version of Python as opposed the version that Ubuntu uses.

I should also say that I am trying python first so I can take advantage of the open source nature of this beast. Maybe I can add something one day and give back to this project.

I like to build my own computers and seemed to be an MS slave because of it. Now I am not thanks to Ubuntu. I dual boot with MS 7 but haven't had to go there for months. I use Ubuntu at work as well have no issues connecting to their XP network.

Thanks again for the support.

---

### Post by cgroza on 2011-03-16
> **VietCanada said:**
> I used to program in Amigabasic. I'm interested in learning Python. I've installed what I believe to be the latest Python. I use Ubuntu 10.10 64bit.

My question.

I want to build a database and the GUI to access it. In Amaigabasic I did this by hand I guess. That is I used polygons, circles and lines to draw my GUI and other commands to make some areas sensitive to mouse clicks. Can I do this with Python?
 
I've been searching for tutorials with no luck so far.

Any advice?

I really don't like Visual basic or related software that lets users point and click their way to a program. I want to write the program from scratch.

Thanks.

You said that you want to build GUIs? Why don't try a GUI toolkit? Like wxPython!

---

### Post by DarkMunk on 2011-03-17
I've always used the Tktinter module to build Python GUI's.

---

