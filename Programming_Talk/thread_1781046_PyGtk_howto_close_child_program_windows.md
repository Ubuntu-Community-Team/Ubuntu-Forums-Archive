---
title: "PyGtk howto close child program windows"
date: 2011-06-12
forum: Programming Talk
---

### Post by bcz on 2011-06-12
HI all.  Just a Python newbie trying to setup a GUI menu system on Python.

I fork and open a copy of my original program as a basic test and it works fine.  However if I terminate the original program, the window remains open until the child ends processing.  For various reasons, if I quit a program I want its window to close, rather than wait for any child programs to finish.

The code that follows is hopefully a minimal test demonstrating the problem

File TestMenu.py

```
# Table test 0


class TestMenu:

  def __init__(self):
    self.entries = [
    ('Prog 1', './p1'),
    ('Prog 2', './p2'),
    ('Prog 3', './p3'),
    ('Test Fork','./p0')
    ]
```

File p0

```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk
import os
import time
from  TestMenu import *

m = []

class Test:

  def doFork(self,prog):
    print 'Calling program', prog
    newPid=os.fork()
    if newPid==0:
      res=os.system(prog)
      if res != 0: print 'Unable to spawn program', prog
      os._exit(0)
    else:
      print 'Program', prog, 'process', newPid, 'forked'

  def cb(self,widget,data):
    print "Hi Bill - %s was pressed" % data
    self.doFork(data)

  def deleteEvent(self, widget, data=None):
    print 'Delete Event occurred'
    return True

  def destroy(self, widget, data=None):
    gtk.widget_destroy(self.window)
    gtk.main_quit()

  def setMenu(self):
    global m
    m= TestMenu()
#    return len(m.entries)

  def __init__(self):
    global m
    window= gtk.Window(gtk.WINDOW_TOPLEVEL)
    window.set_title("System Menu")
    window.connect("destroy",self.destroy)
    window.connect("delete_event",self.deleteEvent)
    window.set_border_width(10)
    self.setMenu()
    tbl = gtk.Table(len(m.entries)+2,5,False)
    window.add(tbl)
    lbl= gtk.Label("Click to select program")
    tbl.attach(lbl,0,3,0,1)
    line=2
    for a in m.entries:
      button= gtk.Button(a[0])
      button.connect("clicked", self.cb, a[1])
      tbl.attach(button, 1, 4, line, line+1)
      line= line+1
    button= gtk.Button("Quit")
    button.connect("clicked", lambda w: gtk.main_quit())
    tbl.attach(button, 4, 5, 0, 1)
    button= gtk.Button('Special')
    button.connect("clicked", self.cb, 'Special')
    tbl.attach(button, 4, 5, line, line+1)
    window.show_all()

  def main(self): gtk.main()


if __name__=="__main__":
  h=Test()
  h.main()
```

I assume that the spawning program is monitoring the spawned program and the former wont close until the later exits.  How do I stop or avoid this behavior?

Any thoughts appreciated

Thanks Bill

---

### Post by simeon87 on 2011-06-13
Do they have to be forked? You could also create them as child windows of the main window and then use [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-destroy-with-parent](http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-destroy-with-parent).

---

### Post by StephenF on 2011-06-13
You want os.closerange(0, 100) before the call to os.system. This closes the pipe to the X server (console too) in the child process.

This is a vital step for GUI apps to avoid instability. Also, subprocess.popen is the non deprecated approach and will fork, close the pipes, and launch the sub-program in a single function call.

Edit: make that, subprocess.Popen

---

### Post by bcz on 2011-06-13
Thanks for your thoughts Simeon87.

I prefer to link about 200 small programs together with menu programs loading programs which are either submenus or modular application programs.  Are you recommending implementing the whole system as a single monolithic application program which does everything?

I accept this could be done.  It would be using GTK as an operating system.

However simple modular programs minimise both development and maintenance costs.

All the menu programs do is start whatever programs the user selects.  They have no interest on what happens once the program is started and do not need to interact with it in any way.

Essentially the user might be running any number of applications, each application having one or more windows open.

In C I use gdk_spawn_command_line_on_screen, which does exactly what I want.  I am hoping to get Windows and Mac capability by using Python

So basically I want to fork so that I can start a separate program independently in its own window.

I presume this approach means that each application runs a separate copy of the Python interpreter.  Dont see a problem here.

---

### Post by bcz on 2011-06-13
Thanks StephenF

Thanks for comment about subprocess, and also closerange.  It's 2AM here so I will get some sleep before trying it.

Could not get a handle on how to use subprocess from the details I found on the web, but good  to know what is now depreciated.

Rgds Bill

---

### Post by simeon87 on 2011-06-13
Yes, it's quite common for a program to have lots of code and one GUI to access it all. I don't understand how 200 processes with a window benefits the user without, of course, knowing what the programs do. Modularity and low maintaince costs can still be achieved in one program.

---

### Post by bcz on 2011-06-13
Hi Simeon

Going off topic a bit, and interpreters have less of a problem here than compilers.

With my own C based programmers workbench, a compile and link takes about a second developing GTK programs.

My experience using Google Web Toolkit on the same hardware is a ~40 seconds cycle.  I adapted my workbench for use with Java and got the time down to 1-2 seconds.  I assume that GWT pulls in monolithic libraries which causes what to me are unacceptable development and maintenance costs.

However with interpreters like Python and powerful CPUs,  I guess this is not perceived to be a problem.

Thanks for your thoughts

---

### Post by bcz on 2011-06-13
Thanks StephenF, closerange is exactly what I want.  Thought (0,20) would be sufficient) Works a treat.  I will try using Popen etc.  Maybe I just have to master it.  Is the whole "os" module depreciated? 

Thanks Bill

---

### Post by cgroza on 2011-06-13
> **bcz said:**
> Thanks StephenF, closerange is exactly what I want.  Thought (0,20) would be sufficient) Works a treat.  I will try using Popen etc.  Maybe I just have to master it.  Is the whole "os" module depreciated? 

Thanks Bill

The os module is not deprecated, many useful thins such as path handling are contained in it.

---

### Post by bcz on 2011-06-14
Thanks all

Popen is easy to use and makes forking transparent.  Default setting do exactly what I want.  ASssume it works on Mac and the other one as well as Linux....  Nice

---

