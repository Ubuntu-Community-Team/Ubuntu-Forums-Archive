---
title: "import and use Glade desing in Python program"
date: 2011-11-23
forum: Programming Talk
---

### Post by puntigamer on 2011-11-23
Hello guys!

I'm trying to make a small graphical program, to be able to work on Ubuntu during my "Digital Image Processing" class. 
I would like to use GTK 3 (GObject) and Python for this.
I've already created some working test windows from source, but it would be too difficult to write the whole GUI without a designer app. I've made a small design in Glade, and I would like to use it in the Python program, but I have no idea, how to import and use the GUI file (.glade) in the program.

If you know any good manual for this, or could write me a small hello-wordl-level GUI app in python, I would really appreciate it!

This was my first try, but it doesn't show any windows :(

```
 #!/usr/bin/python

from gi.repository import Gtk, Gst, GObject
import os, sys

UI_FILE = "/home/daniel/Dokumente/hello.glade"

print("HEllo!!")

class GUI:
        def __init__(self):
                self.builder = Gtk.Builder()
                self.builder.add_from_file(UI_FILE)
                self.builder.connect_signals(self)

                window = self.builder.get_object('window')
                window.show_all()

def main():
        app = GUI()
        Gtk.main() 
```

---

### Post by Russss on 2011-11-23
Why don't you try to use [quickly]("https://wiki.ubuntu.com/Quickly"). It is helpful for building quick GUIs I just made a small app with it and it is pretty easy. It also has a tutorial to show you an example app.

---

### Post by MG&amp;TL on 2011-11-23
....yes, but then if you modify anything, it then crashes.

IMO, you are probably better either learning how to hard-code it, or learn glade. Either way, but I really can't recommend quickly.

A bit wordy, but try this: [http://www.pygtk.org/pygtk2tutorial/]("http://www.pygtk.org/pygtk2tutorial/")

Incidentally, I've never got glade to import correctly. :( Let me know if you get it working.

---

### Post by oldfred on 2011-11-23
I have used glade. Lately I have tried doing my same project with qt4, so I have not tried glade recently.

```
        try:
            self.builder = gtk.Builder()
            self.builder.add_from_file("testimport.glade")
        except:
            self.show_error_dlg("Failed to load UI XML file: testimport.glade")
            sys.exit(1)

```

---

### Post by puntigamer on 2011-11-24
I think I have to learn to hard-code it... I don't want to use pygtk, because I would like to learn the newest things, like GTK 3 and Python 3 ;)
There is a good doc for this, but it would be much simpler to be able to use some GUI designer...

---

### Post by crdlb on 2011-11-24
You can use glade with Gtk3 and the gobject-introspection bindings. Your original code looks fine. Did you name the window 'window' in glade?

---

