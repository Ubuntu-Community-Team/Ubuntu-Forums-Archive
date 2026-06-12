---
title: "Getting started with pygtk and Glade"
date: 2008-07-07
forum: Programming Talk
---

### Post by mssever on 2008-07-07
I'm having trouble using pygtk and Glade. I'm trying to write a GUI configuration app for Net Responsibility (see my sig), and I thought that it would be a simple process: design the interface in Glade, then write event handlers to connect the events to the (already-existing) backend. But I'm stuck.

I've searched Google for help, but what help I've found hasn't been very helpful. [This article]("http://www.linuxjournal.com/article/6586") looked promising, but alas, it's outdated (I get DeprecationWarnings) and appears to be missing important information. Plus, it includes a lot of code without explanation (learning by reading code is only possible if you already have at least a basic familiarity with the tools involved). I've found API documentation both on the Gnome website and via the Python shell's help() function, but that's a ton of information to read, and I don't know enough about GTK or GUI programming in general to know what to look for.

So, here are several questions:

[LIST=1]
[*]Would someone provide me a link to a good explanation of Python + GTK + Glade targetted toward someone with little or no GUI experience?
[*]My most pressing problem right now is how to display a window so I can check how it looks outside the distortion of Glade. I expected it to be a matter of simply loading the glade file and showing the window, but I can't find how to do that. Any help on this?
[*]I think I remember playing with Glade quite a while ago and noticing a feature to generate Python code. I can't see that in the current version. Is there such a code generator? That seems like the ideal solution to my problem.
[*]One part of the GUI is a list of multiple e-mail addresses. I looked for a list-type widget similar to HTML's <select multiple="multiple">, but I didn't find anything similar in Glade. Will a treeview work?
[/LIST]

---

### Post by af20001 on 2008-07-07
A couple of tutorials that should cover your points 1 & 2:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")
[http://www.learningpython.com]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/")

One tip that has caught me out a few times - remember to set the visible property of the window to True in the Glade designer.

3. There's no feature like that in Glade 3 that I know of. Are you thinking of Gladex? (a separate project).

4. Not sure on this one I'm afraid.

---

### Post by Flimm on 2008-07-07
Here, I made a small demo of the things you were trying to explore. Download the archive to get the working demo with its glade file.
[php]#!/usr/bin/env python
# released in the Public Domain ;)

import pygtk
pygtk.require("2.0")
import gtk, gtk.glade
import sys

# read the main function first, then examine this class

class MyApplication():
    
    def __init__(self):
        # here's where the glade file is loaded
        self.wTree = gtk.glade.XML("glade1.glade")
        
        # referencing the widgets to python objects
        self.win = self.wTree.get_widget("window1")
        self.treeView = self.wTree.get_widget("treeview1")
        
        # allowing the TreeView to select multiple items
        self.treeView.get_selection().set_mode(gtk.SELECTION_MULTIPLE)
        
        # making a simple ListStore with one column for text
        self.ll = gtk.ListStore(str)
        self.treeView.set_model(self.ll)
        crt = gtk.CellRendererText()
        column = gtk.TreeViewColumn("header")
        self.treeView.append_column(column)
        column.pack_start(crt, True)
        column.add_attribute(crt, "text", 0)
        
        # appending some data
        self.ll.append(["Number one"])
        self.ll.append(["Number two"])
        self.ll.append(["Number three"])
        
        # when window exists, quit the application
        self.win.connect("destroy", self.win_destroy_event)
        
        # show the window
        self.win.show_all()
        
        
    def win_destroy_event(self, widget, data=None):
        """When the main widow is closed, this function quits the application"""
        print "Window closed, exiting"
        gtk.main_quit()
        sys.exit()
        return False


def main():
    # this is required if you're going to be using threads
    gtk.gdk.threads_init()
    # initialize an instance of MyApplication
    app = MyApplication()
    # start the gtk main loop
    gtk.gdk.threads_enter()
    gtk.main()
    gtk.threads_leave()
    
if __name__ == "__main__":
    main()[/php]
Don't forget the [PyGTK documentation](http://pygtk.org/docs/pygtk/index.html).
The [PyGTK sources](http://ftp.gnome.org/pub/GNOME/sources/pygtk/) also have lots of examples of PyGTK and Glade.

---

### Post by master_kernel on 2008-07-07
You can also refer to KernelCheck for examples (in my signature). I built it from the ground up using Glade and Python, learning as I went along. Too bad there isn't great documentation for both of them together. I'll start working on a simple howto and post the link back here.

---

### Post by mssever on 2008-07-07
> **af20001 said:**
> A couple of tutorials that should cover your points 1 & 2:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)
[http://www.learningpython.com]("http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/")Thanks for the links. I'm reading them now.

> One tip that has caught me out a few times - remember to set the visible property of the window to True in the Glade designer.That was my problem! Thanks for the tip.

> 3. There's no feature like that in Glade 3 that I know of. Are you thinking of Gladex? (a separate project).
Yes, I found Gladex after posting this thread.

---

### Post by mssever on 2008-07-07
> **master_kernel said:**
> You can also refer to KernelCheck for examples (in my signature). I built it from the ground up using Glade and Python, learning as I went along. Too bad there isn't great documentation for both of them together. I'll start working on a simple howto and post the link back here.
Thanks. I'll take a look at it.

---

