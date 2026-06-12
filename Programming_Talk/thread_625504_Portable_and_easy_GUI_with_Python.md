---
title: "Portable and easy GUI with Python"
date: 2007-11-28
forum: Programming Talk
---

### Post by lowpis on 2007-11-28
I need to write a simple GUI with Python that needs to be portable (most Linux flavors and Mac OS X). I also need it to be simple to use, that means that the end user should install nothing extra.

Ubuntu has pyGTK and Tk support (anything else?) right out-of box.
OS X has wxPython and no GTK or TK.

Is there any way to write a python application that runs on most Linux distros (Ubuntu, Fedora, Mandriva, Suse) and Mac OS X without requiring the user to install extra python modules?

Thanks

---

### Post by smartbei on 2007-11-28
Any platform that has Python installed has Tk - it is included. For Python programming it is therefore the most portable gui toolkit. Whether it makes sense to use Tk depends on the your project. If you are making a simple application then it should be very simple to put together a Tkinter Gui that would satisfy the requirements.

Note that there are also ways to package a python application so that users don't need to install anything else. For example, there is py2exe (which is for windows).

---

### Post by xtacocorex on 2007-11-28
You are incorrect about OS X not having Tkinter.  That is the main reason why I moved my GTK+ UI over to TKinter for my Airfoil Generator.  I wanted a UI that was cross platform without having my userbase install extra libraries.

Tkinter may not be the sexiest UI toolkit available, but it definitely gets the job done.

There is also a python script (py2app) that will create a .app bundle for OS X, just forgot where I got it.

---

### Post by adelgado on 2007-11-28
As som already said, every Python install comes with Tkinter, including Mac OS X.

As for .app bundles for Mac OS X, this link might be of help:

[http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html](http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html)

---

### Post by samjh on 2007-11-28
Actually, Python on Ubuntu doesn't come installed with Tkinter or Tk.  It needs to be manually installed or installed as a dependency for another program, from the repositories.

---

### Post by lowpis on 2007-11-28
My mistake: I just saw that Mac has Tkinter.

Tkinter looks ok on Mac but is very ugly on Ubuntu. But it seems to be the right solution for me.

---

### Post by smartbei on 2007-11-28
Yes, it is indeed very ugly on Ubuntu, and it looks good (decent anyway) on Windows as well. Who knows...

---

