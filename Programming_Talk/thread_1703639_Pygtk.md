---
title: "Pygtk"
date: 2011-03-09
forum: Programming Talk
---

### Post by Hippytaff on 2011-03-09
I'm doing a tutorial and I've copied the code exactly. I even copy and pasted the code and it doesn't work. Any help would be very welcome

```
#!/usr/bin/env python

#example base.py

import pygtk
pygtk.require('2.0')
import gtk

class Base:
        def _init_(self):
                self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
                self.window.show()

        def main(self):
                gtk.main()

print _name_
if _name_ == "_main_":
        base = Base()
        base.main()

```error
```
File "./base.py", line 17, in <module>
    print _name_
NameError: name '_name_' is not defined

```[link to tut]("http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html")

Thanks

---

### Post by robots.jpg on 2011-03-09
Those single underscore _ characters should all be double __.

Edit: not the one in gtk.WINDOW_TOPLEVEL.

---

### Post by Hippytaff on 2011-03-09
You star - I just thought they looked bigger because it's a different font (I am such a moron sometimes)

Cheers

---

