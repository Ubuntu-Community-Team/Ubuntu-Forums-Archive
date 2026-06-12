---
title: "Python - Progressbar"
date: 2014-09-12
forum: Programming Talk
---

### Post by macstar on 2014-09-12
i have a bit experience with python and glade, and so far i can  successfully create buttons, boxes, etc. and i can make each button or  checkbox to output a print command.

now the thing i wanna to achieve is that i have - to make it easier - a simple file where i have 1 button and 1 progressbar.
now i wanna make the progressbar either pulsing (should be easier afaik) or progressing till the thread i run is completed.
for start i would be happy if the progressbar just pulses when i do a button click.

however: i have tried the whole day and it just seems to be impossible.
google did not help:

so here is my simple code:

```

from gi.repository import Gtk
import subprocess

class Handler:
  def on_window1_delete_event(self, *args):
  Gtk.main_quit(*args)

  def on_button1_clicked(self, button):
  print("Hello World!")

builder = Gtk.Builder()
builder.add_from_file("progress2.glade")
builder.connect_signals(Handler())

window = builder.get_object("window1")
progressbar = builder.get_object("progressbar1")
window.show_all()

Gtk.main()


```

now i need to somehow get the progressbar.
if i make it like this:

```
from gi.repository import Gtk
import subprocess

class Handler:
    def on_window1_delete_event(self, *args):
        Gtk.main_quit(*args)

    def on_button1_clicked(self, button):
        print("Hello World!")
    self.progressbar.pulse()
builder = Gtk.Builder()
builder.add_from_file("progress2.glade")
builder.connect_signals(Handler())

window = builder.get_object("window1")
progressbar = builder.get_object("progressbar1")
window.show_all()

Gtk.main()
```

i get the error:
    	 		 		[INDENT]File "test1.py", line 10, in on_button1_clicked
  self.progressbar.pulse()
AttributeError: Handler instance has no attribute 'progressbar'
[/INDENT] 	 
making it like this:

```
from gi.repository import Gtk
import subprocess

class Handler:
    def on_window1_delete_event(self, *args):
        Gtk.main_quit(*args)

    def on_button1_clicked(self, button):
        print("Hello World!")
    progressbar.pulse()
builder = Gtk.Builder()
builder.add_from_file("progress2.glade")
builder.connect_signals(Handler())

window = builder.get_object("window1")
progressbar = builder.get_object("progressbar1")
window.show_all()

Gtk.main()
```

makes the progressbar only pulsing a small step each time i  click the button.
i want to have it pulsing endlessly if i click the button only once.
how?

i suspect we would need to end a  kind of loop right?

i spent the last 2 days trying, looking online for solutions, i even got me 3 books today but they all help only partially with things i need to master.

those are:

- a progressbar pulsing while a thread is running and installs stuff
- i managed to create a temp file but it's empty and there is no way to write anything in it.
 for example the code is this:
```

import tempfile
import csv
import sys

tempfile.tempdir = '/home/macstar/Projekte/GLADE/addonpacknew/examples/'
tempfile.NamedTemporaryFile(delete=False, mode='w+t')
with tempfile.NamedTemporaryFile() as temp:
  temp.write('some data')
 

```

all i get ever is an empty temp file. i thought it would be nice to write chosen numbers in the tempfile and then the script reads the content of the temp file and for example if it contains 1, 2, 4 and 5 installes the programs 1, 2, 4 and 5 and so on...


i probably don't know ennough about it yet, but the problem is that there is not a single good tutorial out there. not one! 

i found a few nice examples how to create a progressbar in terminal, which would be also an option for me, but not a single line where to enter the threading command.
i have spent hours of trying blindly with no luck.

ideas? help? you can also inbox me. thanks

---

