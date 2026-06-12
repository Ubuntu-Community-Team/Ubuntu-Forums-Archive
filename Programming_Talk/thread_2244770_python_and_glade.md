---
title: "python and glade"
date: 2014-09-18
forum: Programming Talk
---

### Post by macstar on 2014-09-18
i am facing a problem with a glade file i have designed on glade  and connecting the right signals with python:

```
from gi.repository import Gtk, GObject
import webbrowser
import subprocess
import tempfile
import os
import threading
import sys
import time
import signal
import readline




class CheckButtonWindow(Gtk.Window):
    

    
    def __init__(self):
        self.window = builder.get_object("window1")
        self.window.show_all()



        grid1 = Gtk.Grid()
        self.add(grid1)
        
        

        self.checkbutton1 = Gtk.CheckButton(label="Clipgrab")
        self.checkbutton1.connect("toggled", self.on_checkbutton1_toggled)
        
      
        
        
       
        button1 = Gtk.Button("Apply")
        button1.connect("clicked", self.on_button1_clicked)
    
        
    

 

    
    def onDeleteWindow(self, *args):
        Gtk.main_quit(*args)

    def on_window1_delete_event(self, *args):
        Gtk.main_quit(*args)
        
    def on_windows1_destroy_event(self, *args):
        Gtk.main_quit(*args)

    def onButtonPressed(self, button):
        print("Hello World!")
        
    def on_window1_destroy(self, object, data=None):
        Gtk.main_quit()
        
    def on_imagemenuitem5_activate(self, menuitem, data=None):
        Gtk.main_quit()
        
        
    def on_checkbutton1_toggled(self, checkbutton1):
        if checkbutton1.get_active():
            label1= "1"
            state1 = "checked"
        else:
            label1= "1"
            state1 = "unchecked"
        print(label1, "was" , state1)
        
        
    def on_button1_clicked(self, button1):
        print ("test")
        if self.checkbutton1.get_active():
            print ("hallo")

           
        
        
        
builder = Gtk.Builder()
builder.add_from_file("interface.glade")
builder.connect_signals(CheckButtonWindow())


Gtk.main()


```

no matter how i try, i can't get the if self.checkbutton1.get_active(): attribute to be done while i click on button1.
and i am out of ideas.
because, when i am running exactly the same code, but without any glade file and the connected signals (they are set up right in glade), it works.

so now i either have a working code with a horrible interface (doing it in python alone with grids is guesswork) or a nice interface (easy with glade) but then the code is not working.

i have googled a lot and found nothing about it.
[http://python-gtk-3-tutorial.readthedocs.org/en/latest/layout.html](http://python-gtk-3-tutorial.readthedocs.org/en/latest/layout.html)  <-- this only explains a very little bit with python/glade combo.

could anyone help me out please?;)

---

