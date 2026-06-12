---
title: "[SOLVED] Python GTK problems in Intrepid"
date: 2008-11-18
forum: Programming Talk
---

### Post by flyguy97 on 2008-11-18
I have the following simple program to test pygtk functionality:
```
import pygtk
import gtk
  
class TestGTK:
 
     def delete_event(self, widget, event, data=None):
        return False
 
     def destroy(self, widget, data=None):
        gtk.main_quit()
        
     def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(200)
        self.window.set_title("GTK Test")
  
        self.button = gtk.Button("This is just a test")
        self.button.connect_object("clicked", gtk.Widget.destroy, self.window)
   
        self.window.add(self.button)
        self.button.show()
        self.window.show()

     def main(self):
        gtk.main()

if __name__ == "__main__":
	test = TestGTK()
	test.main()
```

but it generates the following error:
```
me@laptop:~/Desktop$ python Test.py 
Traceback (most recent call last):
  File "Test.py", line 30, in <module>
    test = TestGTK()
  File "Test.py", line 13, in __init__
    self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
AttributeError: 'module' object has no attribute 'Window'
```

I have all the python-gtk2 packages installed (even re-installed them). Is this a problem with a broken package perhaps?

---

### Post by mike_g on 2008-11-18
Well, your code works fine my end.

---

### Post by nvteighen on 2008-11-18
It works here too... This is strange; I can't see any error, unless your system has a problem.

---

### Post by unutbu on 2008-11-18
Perhaps check that you do not have a rogue file named gtk.py somewhere in your sys.path.

You can do that by running
[PHP]#!/usr/bin/env python
import pygtk
import gtk
print gtk
print pygtk[/PHP]
and making sure it returns something like
```

<module 'gtk' from '/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.pyc'>
<module 'pygtk' from '/var/lib/python-support/python2.5/pygtk.pyc'>

```

---

### Post by flyguy97 on 2008-11-19
Thank you so much, I had a file named gtk.py in my path. All works now.

> **unutbu said:**
> Perhaps check that you do not have a rogue file named gtk.py somewhere in your sys.path.

You can do that by running
[PHP]#!/usr/bin/env python
import pygtk
import gtk
print gtk
print pygtk[/PHP]
and making sure it returns something like
```

<module 'gtk' from '/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.pyc'>
<module 'pygtk' from '/var/lib/python-support/python2.5/pygtk.pyc'>

```

---

