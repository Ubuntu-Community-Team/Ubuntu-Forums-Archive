---
title: "Programming language to use for GUI development"
date: 2014-10-20
forum: Programming Talk
---

### Post by bala5 on 2014-10-20
Hello Junta,
   I am in the process of development of a tool which should work in UNIX/Linux OS(later on must be extended to windows)
My need is to develop a GUI where a user draws certain stick diagrams from which I need to extract the details and convert it into a
representation/code native to my tool.

I am pretty new to software programming since I am an hardware engineer but with pretty solid fundamentals in OOP(thanks to Systemverilog that I have been working on).
I have some basic knowledge of C but I am ready to learn any new language provided it solves my need as I need to complete the project in a year's time.

It will be really great if anyone can help me out with your inputs.

Thanks in advance.

Regards
Bala

---

### Post by slickymaster on 2014-10-20
*Moved to the ***Programming Talk*** sub-forum*

---

### Post by llanitedave on 2014-10-21
Easiest to get started with might be Python, as there are some decent GUI tools available:  wxPython for Python 2, PyQt for Python 2 and 3, and tkinter which comes bundled.  The first two are wrappers around C++ tools, while tkinter uses tcl/tk as its backend language.  Any of them work fine on Linux, Mac, and Windows.   If you're comfortable with C++, you might skip the Python part and go directly to wxWidgts or QT, but that might involve more boilerplate code to build anything.

From what I remember, all of them provide canvas tools for drawing objects, and Python can define the objects that it draws and translate it to whatever output you need.

---

