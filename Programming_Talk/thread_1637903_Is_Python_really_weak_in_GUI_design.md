---
title: "Is Python really weak in GUI design?"
date: 2010-12-05
forum: Programming Talk
---

### Post by zhaotianwu on 2010-12-05
I'm seeking ideas about Python's GUI design strength. I've heard someone say that using Python to design a WYSIWYG GUI is a painful experience, and Python's GUI is even worse than Visual Basic's. But I've also heard quite opposite opinions that indicate Python's GUI design is much better than Java Swing. Since I really don't know which one is accurate, and I really have a keen interest in Python, I'd like to hear some advice here. Many thanks!   

By the way, I'm a totally newbie to Python, can anybody throw in some advice about good Python tutorials(preferably free) and good forum?

---

### Post by NightwishFan on 2010-12-05
This taught me everything I needed to know to make simple GUI apps.
[http://www.tuxradar.com/content/python-pygtk-webkit-20-minutes](http://www.tuxradar.com/content/python-pygtk-webkit-20-minutes)

---

### Post by Tony Flury on 2010-12-05
> **zhaotianwu said:**
> I'm seeking ideas about Python's GUI design strength. 
The point is that the Python Language does not support GUI Designs per se - what it does is support the use of libraries and toolkits that allow you to create and use GUIS - GTK, QT, TK are some for instance.
> 
I've heard someone say that using Python to design a WYSIWYG GUI is a painful experience, and Python's GUI is even worse than Visual Basic's. 

As above - python does not have a GUI of it's own - but depending on the toolkit library you use, and the supporting tools you use you can make GUI design very easy - for instance the combination of Glade and the GTK library makes GUI design very easy in fact a lot easier than VB - every tried to write a generic window in VB that resizes nicely - including the layout expansion etc.
> 
But I've also heard quite opposite opinions that indicate Python's GUI design is much better than Java Swing. Since I really don't know which one is accurate, and I really have a keen interest in Python, I'd like to hear some advice here. Many thanks!   

By the way, I'm a totally newbie to Python, can anybody throw in some advice about good Python tutorials(preferably free) and good forum?

---

### Post by GregBrannon on 2010-12-05
Opinions are like . . . well, you know the rest.

The tool you learn to use well will always seem better for the job at hand than the tool you don't know how to use.  You like Python?  Great! Learn it inside and out; use it until you find the thing it can't do, then learn something else.

---

### Post by slooksterpsv on 2010-12-05
Personally, I like Python and Qt, cause Qt very... well you can position what you want anywhere, where with wx, and there's one more... I've had issues where it tries to align things for you.

PyQt lets you design how it looks, and even setup signals (like click, double-click, etc.) and assign those to functions that you can delegate to whatever you want it to do later in your code. You do have to use: 
pyuic <ui_file> > <python_output>

To output how the python file, then modify the python file to initialize the window and what not. Not too hard, but better IMO. I should look more into GTK.

---

### Post by Sprut1 on 2010-12-05
> **zhaotianwu said:**
> I'm seeking ideas about Python's GUI design strength. I've heard someone say that using Python to design a WYSIWYG GUI is a painful experience, and Python's GUI is even worse than Visual Basic's. But I've also heard quite opposite opinions that indicate Python's GUI design is much better than Java Swing. Since I really don't know which one is accurate, and I really have a keen interest in Python, I'd like to hear some advice here. Many thanks!   

By the way, I'm a totally newbie to Python, can anybody throw in some advice about good Python tutorials(preferably free) and good forum?

I'm shocked. With python you have several possibilities when it comes to GUI design. wxPython, pyGTK, Tkinter, QT too name the most common. I for one have developed GUIs in both wxPython, using wxFormBuilder, which is a great GUI designer, and pyGTK using Glade3 which is an amazing GUI builder in my opinion.

Also the GUIs looks very native (in my opinion) on both Linux and Windows (can't speak for OSX). If you search around the web you'll read thousands of different opinions, but experiencing it yourself is always the best solution.

I recommend starting learning the basics of Python before even considering GUI designing. If you do a quick search there are a few good python forums around the web, including this one. Buying a few books never hurt either.

And btw, Visual Basics GUI editor is one of the best I've every tried.

---

### Post by lykeion on 2010-12-05
> **zhaotianwu said:**
> But I've also heard quite opposite opinions that indicate Python's GUI design is much better than Java Swing.Personally I think Java Swing is a PITA, and with the plethora of available GUI libraries for Python you should be able to find something much simpler and better.

---

