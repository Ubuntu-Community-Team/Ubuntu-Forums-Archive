---
title: "[Python] GUI Framework written in Python?"
date: 2008-08-23
forum: Programming Talk
---

### Post by xelapond on 2008-08-23
Are there any GUI frameworks, like GTK or wxWidgets(could be much, much simpler, nothing fancy) written in Python?  Not wrapped or binded from C/C++ or anything?  The only real requirement is that it takes mouse input.

Thanks, 

Alex

---

### Post by -grubby on 2008-08-23
check out these : 

[list]
[*][Easygui](http://easygui.sourceforge.net/)
[*][WxPython](http://www.wxpython.org/)
[/list]

---

### Post by compnut41 on 2008-08-23
Python has a module called tkinter which I guess has Gui, but I haven't gotten to gry it yet here is the link
[URL="http://docs.python.org/lib/tkinter.html"]
http://docs.python.org/lib/tkinter.html[/URL]

---

### Post by pmasiar on 2008-08-23
EasyGUI cannot be beaten, simplicity-wise -- if you can ignore the fact it lacks events and has just couple of types of dialogs, not a real GUI designer. But surely is simple, works and looks good enough.

---

### Post by babyhuey on 2008-08-23
Python really needs a pythonic gui framework that is cross-platform and has nice looking widgets. 

The only thing I've seen thats close is, if they ever integrate Tkinter 8.5's themed widgets in the standard library.

---

### Post by pmasiar on 2008-08-23
> **babyhuey said:**
> Python really needs a pythonic gui framework that is cross-platform and has nice looking widgets. 

The only thing I've seen thats close is, if they ever integrate Tkinter 8.5's themed widgets in the standard library.

Like wxPython? 

If you don't know about it it does not mean it does not exist :-)

---

### Post by xelapond on 2008-08-23
I am not looking to actually use the framework, I already know PyGtk, Clutter and PyQt for all my GUI needs.  I am looking to write my own simple GUI framework, for practice, but I can't seem to find any examples of how to map where the cursor is on the screen to what widget is below it.  I know I can just iterate through all the widgets and check for a collision, but thats not elegant enough for me(and its pretty slow).  I was looking at Quad Tree(recommended by wybiral).  I can figure out how to see which points are in a rectangle, but not which rectangles a point is in.

Easygui was written in Tk, so there was no mouse handling there
wxPython is written in C++, and I was looking for a Python Mouse Handling section
TkInter was a binding type thing to Tk?  Anyway, I could not find where it made any references to detection mouse.

Thanks for all the help, 

Alex

---

### Post by stevescripts on 2008-08-23
> **babyhuey said:**
> 
The only thing I've seen thats close is, if they ever integrate Tkinter 8.5's themed widgets in the standard library.

I assure you all that work continues on bringing Tk's themed (Tile) widgets to python (Tkinter).

It *appears* that some of the folks here seem to think that Tk (and Tkinter)
don't handle mouse events ... Tk and Tkinter handle mouse events just fine.

Steve

---

### Post by xelapond on 2008-08-23
My question is, do they handle mouse events in Python, and if so, where is it?

Thanks, 

Alex

---

### Post by stevescripts on 2008-08-23
What exactly do you wish to do with the mouse?  Warp the pointer?  Get the 
mouse co-ords?  Bind to mouse clicks? ... ?

Steve

---

### Post by babyhuey on 2008-08-23
> **pmasiar said:**
> Like wxPython? 

If you don't know about it it does not mean it does not exist :-)

I'm definitely not a wxPython expert but I would hardly consider it pythonic.

I'm not faulting wxPython. Being built on wxWidgets, I wouldn't expect it to be pythonic.
There was/is an effort to make wxPython more pythonic but I can't remember its name.

---

### Post by days_of_ruin on 2008-08-23
I think the OP is looking for a gui framework CODED in python.
Not a python BINDING.I don't think there are any.It would be too slow.

---

### Post by days_of_ruin on 2008-08-23
I think you might be able to get the mouse cursor x,y using [Xlib]("http://python-xlib.sourceforge.net/?page=home")

---

### Post by xelapond on 2008-08-24
Thanks you all for your replies.

Stevescripts:  I am trying to figure out how to map cursor events to widgets.  Iterating through and checking for collision is too slow, so I got tipped off to Quad Tree.  Unfortunately I can't figure out how to code this, so I was looking for an example that would be easy to apply.  I am sure there are others, but most involve finding which points are in a box.  I need to know which boxes a point is in.  Ill play around with it tomorrow and see if I can hack the former into the latter.

days_of_ruin:  You speak my words exactly!  I have no problem getting mouse events, I just don't know how to map them quickly.

Thanks for all your replies!

Alex

---

