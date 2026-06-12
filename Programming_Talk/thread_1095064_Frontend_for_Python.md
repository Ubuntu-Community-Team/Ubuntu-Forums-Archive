---
title: "Frontend for Python"
date: 2009-03-13
forum: Programming Talk
---

### Post by KingNeil on 2009-03-13
I've been learning Python, and am doing pretty well.. but I'm very confused as to how you create a GUI frontend for your Python backend. All I have so far is my programs inputting/outputting in a command prompt/terminal environment.

Do you program the front end in Python, or a totally separate program? If the answer is the latter, can I have some examples of programs can be used to create a front end? 

This is a very n00bie question, but I can't find an answer elsewhere, so I thought I'd ask you fine people.

(By the way, I am using Windows for this, if that matters)

---

### Post by unutbu on 2009-03-13
Python comes with Tk, which I believe works the same for both Windows and Linux.
The examples found in Mark Lutz's book "Programming Python" can be downloaded here:
[http://examples.oreilly.com/python3/PP3E-Examples-1.2.tgz](http://examples.oreilly.com/python3/PP3E-Examples-1.2.tgz)
Look in the directory PP3E-Examples-1.2/Examples/PP3E/Gui
for examples of how to build GUIs using Python and Tk.

---

### Post by KingNeil on 2009-03-13
Very nice. I'll have a look at that and come back if I have any questions. Nice to see cross-Operating System support.

---

### Post by ghostdog74 on 2009-03-13
unless you are programming something complicated, why not just program a web interface using HTML(and other web technologies). Simple buttons, radio, checkboxes, submit buttons can be done up pretty easily. Just a suggestion.

---

### Post by KingNeil on 2009-03-13
> **ghostdog74 said:**
> unless you are programming something complicated, why not just program a web interface using HTML(and other web technologies). Simple buttons, radio, checkboxes, submit buttons can be done up pretty easily. Just a suggestion.

How would you link an HTML page to a Python script?

---

### Post by ghostdog74 on 2009-03-13
[Python Web Frameworks ](http://www.google.com.sg/search?hl=en&q=Python+web+framework&btnG=Google+Search&meta=)
[Python CGI](http://www.google.com.sg/search?hl=en&q=Python+CGI&btnG=Search&meta=)

if you are not restricted to Python, then use PHP, one of the simplest way to create web pages.

---

### Post by scottuss on 2009-03-13
I use PyGTK for Gnome programming in Python [http://www.pygtk.org/](http://www.pygtk.org/) and Tkinter for Windows / cross platform

---

### Post by cdsboy on 2009-03-13
You could go the web route with python or you can go desktop apps. Another more complete webframework for python is django. For desktop gui's you should look at the python library for gtk or check out wxPython. They are both good frameworks that can be run on both windows and linux.

---

### Post by KingNeil on 2009-03-13
> **scottuss said:**
> I use PyGTK for Gnome programming in Python [http://www.pygtk.org/](http://www.pygtk.org/) and Tkinter for Windows / cross platform

Thank you. I'll check those out.

And to ghostdog, no, this cannot be PHP. I need to access people's local files, amongst other stuff. And of course, people would have to install PHP just to use my file, so no, that's a complete fail. All I'm looking for is an interface. It'd probably be best if it's not web-based.

---

### Post by cmat on 2009-03-13
wxPython for everything. Uses native OS widgets and runs on many OSes with no modification. I actually develop software for Ubuntu on Vista and it works as well as I expect it to.

---

### Post by mcla0203 on 2009-03-13
You can call any script from the unix terminal from HTML.  

<!-- #exec cmd ="./python_script.py"-->

Just make sure that script has executable permission.
Make sure the html has executable permission.
Also make sure apache is configured to execute scripts in that directory, otherwise apache won't do it.

---

### Post by scottuss on 2009-03-13
> **mcla0203 said:**
> You can call any script from the unix terminal from HTML.  

<!-- #exec cmd ="./python_script.py"-->

Just make sure that script has executable permission.
Make sure the html has executable permission.
Also make sure apache is configured to execute scripts in that directory, otherwise apache won't do it.

I don't think that's what the OP is really looking for. Mixing HTML and Python scripts is complicating what he/she wants to achieve.

---

### Post by KingNeil on 2009-03-13
Yes, indeed. None of this web stuff.

I'll be looking into some of the other suggestions people have made.

---

### Post by Can+~ on 2009-03-13
The thing is that there's no unified python frotnend.

There are various [GUI libraries]("http://wiki.python.org/moin/GuiProgramming") that have python bindings.

One typically found in the ubuntuforums, due to the popularity of gnome, is GTK+ (pygtk) using Glade3 to design the interface and bind it with a python script.

Other typically found are QT3 (and 4), wxwidgets and tk which comes included with python.

---

### Post by stevescripts on 2009-03-13
A quick  "Hello World" GUI, in Python, using Tkinter:

```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Hello World")

root.resizable(0, 0)

b = Button(root, text="Hello World!", width=20, command=exit)

b.grid(row=0, column=1)

root.mainloop()

```

I know a lot of folks dont like the looks of Tk, but, it works for me ;)

Hope this is informative.

Steve

---

### Post by KingNeil on 2009-03-13
TK looks good. I'd ideally be looking for a GUI where I can design it, a bit like Visual Basic. I could code it with TK though.

---

### Post by wmcbrine on 2009-03-13
> **KingNeil said:**
> I'd ideally be looking for a GUI where I can design it, a bit like Visual Basic.Take a look at Glade.

---

### Post by scottuss on 2009-03-13
> **wmcbrine said:**
> Take a look at Glade.

+1. Glade is very good

---

