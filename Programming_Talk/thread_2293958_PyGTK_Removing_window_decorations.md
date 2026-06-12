---
title: "PyGTK: Removing window decorations"
date: 2015-09-08
forum: Programming Talk
---

### Post by tdogmonster1337 on 2015-09-08
Hi. I have written a simple program in PyGTK that simply creates a windows and display an image inside of it. Here is the code.
```
#!/usr/bin/python

import pygtk
import gtk
import commands

class Base:
    def delete_event(self, widget, event, data=None):
        print "Delete event occured.\n"
        return False

    def destroy(self, widget, data=None):
        gtk.main.quit()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.image = gtk.Image()
        self.image.set_from_file("oldlady_cup.jpg")
        self.window.add(self.image)
        self.image.show()
        self.window.show()

        
    def main(self):
        gtk.main()

if __name__ == "__main__":
    base = Base()
    base.main()
```

However, I want PyGTK to create the window without any window decorations. I tried putting this line of code in the program:

```
self.set_decorated(False)
```

I tried putting this line in the list of lines in the "def __init__(self):" section, but instead of creating a  window without decorations with a picture in it, it threw an error:

```
Traceback (most recent call last):
  File "image.py", line 29, in <module>
    base = Base()
  File "image.py", line 19, in __init__
    self.set_decorated(False)
AttributeError: Base instance has no attribute 'set_decorated'
```

What Am I doing wrong? How do I make this work? I require assistance! ;)

Thanks!

---

