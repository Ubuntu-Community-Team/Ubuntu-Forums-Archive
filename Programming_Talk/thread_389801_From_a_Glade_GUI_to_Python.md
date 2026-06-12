---
title: "From a Glade GUI to Python"
date: 2007-03-21
forum: Programming Talk
---

### Post by TheForkOfJustice on 2007-03-21
Long story short, I need to know how to get values entered in text fields and comboboxes in a Glade GUI to be read by a python script and saved in a simple XML file.

I've begun reading tutorials on the internet but to be honest, I have no desire to learn the basics.  I'm not learning a degree here, I just need to know how to do a few simple tasks and not every thing python can do.

Can you help me out?

I'm also learning how to do 'Signals' in Glade.  If someone could point me to the references they used to learn this it would be most welcome.

Thanks in advance.

---

### Post by _tms on 2007-03-21
Here's a sample script that might get you started:
```

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade

wTree = gtk.glade.XML("file.glade")
window = wTree.get_widget("window1")
window.connect("destroy", lambda w: gtk.main_quit())
window.show_all()

gtk.mainloop()

```

But surely you will have to learn the basics to be able to create anything useful.

---

### Post by TheForkOfJustice on 2007-03-22
> **_tms said:**
> Here's a sample script that might get you started:
```

import pygtk
pygtk.require("2.0")
import gtk
import gtk.glade

wTree = gtk.glade.XML("file.glade")
window = wTree.get_widget("window1")
window.connect("destroy", lambda w: gtk.main_quit())
window.show_all()

gtk.mainloop()

```But surely you will have to learn the basics to be able to create anything useful.

The glade file I'm working on basically reports data entered into it and little else so technically that's all I need.  I'll rarely if ever need to know other commands but I intend to learn them down the road.  As of now - they can wait.

What I need now is a reference to understand signal handlers in Glade, how to save the values entered into widgets, and export the values to an XML file.  You provided the basic 'startup' script for a glade GUI which I already have.

I'll be seeing many variations of ' window = wTree.get_widget("window1") '  in the future.  The last 3 lines of code in your sample are currently a mystery to me.

---

### Post by _tms on 2007-03-22
```
window.connect("destoy", lambda w: gtk.main_quit())
```
For clarification, this could look like this:
```

def do_exit(self, window):
    print "Exiting"
    gtk.main_quit()

window.connect(destroy, do_exit)

```

Widgets fire signals on action. The "destroy" signal is emitted wen you try to close the window. Here we are connecting do_exit to the destroy signal, so when that signal is emitted, do_exit is run, which in this example prints Exiting and ends the GTK+ loop.
the show_all() is used for showing the window and it's child widgets because, at least the window is hidden when created.

gtk.mainloop() enters the GTK+ loop.

If you had an entry widget you could connect the "activate" signal to a new method like this:
```

def do_say(self, widget):
    print widget.get_text()

my_entrywidget.connect("activate", do_say)

```

---

### Post by TheForkOfJustice on 2007-03-22
> **_tms said:**
> ```
window.connect("destoy", lambda w: gtk.main_quit())
```For clarification, this could look like this:
```

def do_exit(self, window):
    print "Exiting"
    gtk.main_quit()

window.connect(destroy, do_exit)

```Widgets fire signals on action. The "destroy" signal is emitted wen you try to close the window. Here we are connecting do_exit to the destroy signal, so when that signal is emitted, do_exit is run, which in this example prints Exiting and ends the GTK+ loop.
the show_all() is used for showing the window and it's child widgets because, at least the window is hidden when created.

Understood, though, it may take some time for this to become second nature to me :)

Also, can you explain the 'lambda w: gtk.main_quit()' part to me (especially the 'lambda' bit)?

> gtk.mainloop() enters the GTK+ loop.

You'll have to forgive this newbie programmer but I have no idea what a GTK+ loop is :P

I think it is telling the machine to 'loop' back to the beginning of the code and listen for new events defined in the code from the start on down.  If it didn't 'loop' back it would only be capable of doing one task defined by the code.

Is this correct?

> 
If you had an entry widget you could connect the "activate" signal to a new method like this:
```

def do_say(self, widget):
    print widget.get_text()

my_entrywidget.connect("activate", do_say)

```

I can see how "activate" refers to the signal that the widget sends out but I'm not too certain what the 'self' entries are supposed to be/mean in the 'def' line. Please explain.

---

### Post by aamukahvi on 2007-03-22
Hi,

This is kinda related so I'll post here. Concerning Glade, how can I make a slider with labeled stops like "yes", "no", "maybe" instead of a num-range?

---

### Post by _tms on 2007-03-22
> **TheForkOfJustice said:**
> Understood, though, it may take some time for this to become second nature to me :)

Also, can you explain the 'lambda w: gtk.main_quit()' part to me (especially the 'lambda' bit)?



You'll have to forgive this newbie programmer but I have no idea what a GTK+ loop is :P

I think it is telling the machine to 'loop' back to the beginning of the code and listen for new events defined in the code from the start on down.  If it didn't 'loop' back it would only be capable of doing one task defined by the code.

Is this correct?



I can see how "activate" refers to the signal that the widget sends out but I'm not too certain what the 'self' entries are supposed to be/mean in the 'def' line. Please explain.

lambda's in python are small anonymous functions. The reason I used it is because the destroy signal calls the connected function with the correct widget (the window in this case) as the first argument. However, gtk.main_quit() does not take an argument and would not be happy about receiving one.
Lambda by example:
```

square = lambda x: x*x
print square(4)

```
would print out 16.
[More on lambdas](http://docs.python.org/tut/node6.html#SECTION006750000000000000000)

I don't know the secrets of the GTK+ loop but as far as I know it draws the widgets, waits for events to happens, calls the connected function on events, and such stuff. So when you call gtk.mainloop(), it will stay in that call until gtk.main_quit() is called. 
If you need to make other blocking stuff such as file/network IO, the easiest way would be threading. I'm currently writing an FTP client with pygtk and one thread per FTP connection wich is working great.

Oh yeah, the "self" part should'nt be there. I'm so used to it from writing class methods :)

---

### Post by TheForkOfJustice on 2007-03-22
Heh, it's going to take me a while to digest all of that but this has really helped.

Thanks.

PS - if the 'self' shouldn't be there, then what should take its place?

---

### Post by _tms on 2007-03-22
Nothing, it should just say do_say(widget):
Oh and by the way, since you've already started on learning the basics, [why not continue?](http://docs.python.org/tut/tut.html):)

---

### Post by TheForkOfJustice on 2007-03-22
> **_tms said:**
> Nothing, it should just say do_say(widget):
Oh and by the way, since you've already started on learning the basics, [why not continue?]("http://docs.python.org/tut/tut.html"):)

I plan to!  And you've been handy.

Again, thanks!

---

