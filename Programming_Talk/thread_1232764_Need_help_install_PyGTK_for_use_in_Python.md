---
title: "Need help install PyGTK for use in Python"
date: 2009-08-05
forum: Programming Talk
---

### Post by Jimleko211 on 2009-08-05
I can't seem to use pyGTK in any of the things I'm trying to program (I'm trying to set it up so I can use it for later), and I can't understand why.  I've downloaded and installed all the dependencies here: [http://www.pygtk.org/downloads.html](http://www.pygtk.org/downloads.html)  and I've copied and pasted the code sample of
[php]
import gtk
 
def createWindow():
    window = gtk.Window()
    window.set_default_size(200, 200)
    window.connect('destroy', gtk.main_quit)
 
    label = gtk.Label('Hello World')
    window.add(label)
 
    label.show()
    window.show()
 
createWindow()
gtk.main()
[/php] from the PyGTK page of Wikipedia.  But whenever I try to run it, I get this error:
```
Traceback (most recent call last):
  File "gtk.py", line 2, in <module>
    import gtk
  File "/home/colin/gtk.py", line 15, in <module>
    createWindow()
  File "/home/colin/gtk.py", line 5, in createWindow
    window = gtk.Window()
AttributeError: 'module' object has no attribute 'Window'

```

What do I have to do to get it run?

---

### Post by Can+~ on 2009-08-05
Your script file is named gtk.py, rename it to something else.

---

### Post by Jimleko211 on 2009-08-05
> **Can+~ said:**
> Your script file is named gtk.py, rename it to something else.
Did that, and it still didn't work.  I changed import gtk to import pygtk, and that got rid of that error.  The example demo provided with the pygtk package worked fine, so I'm starting to think that Wikipedia's example is out dated.

---

### Post by Tony Flury on 2009-08-06
don't you need to import pygtk and gtk to get gtk to work ?

[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

and specifically - for instance : 

[http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld](http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld)

---

