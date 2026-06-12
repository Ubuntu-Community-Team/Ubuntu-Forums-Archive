---
title: "pygtk issues"
date: 2012-04-03
forum: Programming Talk
---

### Post by Hiuhu on 2012-04-03
Am new to pygtk amd everytime I try to write code using vim,
jemoh@Hiuhu:~$ vim window.py
#!/usr/bin/env/ python
 
import pygtk
pygtk.require('2.0')
import gtk
 
class Base:
    def destrpy(self,widget,data=none):
        gtk.main_quit()
 
    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.show()
        self.window.connect("destroy", self.destroy)
 
    def main(self):
        gtk.main()
 
if __name__ == "__main__"
     base = Base()
     base.main()
"window.py" 21L, 409C                                         1,1           All
jemoh@Hiuhu:~$ chmod +x window.py
this is what i get  when trying to execute it:
jemoh@Hiuhu:~$ ./window.py
bash: ./window.py: /usr/bin/env/: bad interpreter: Not a directory

---

### Post by r-senior on 2012-04-03
Could you indent in code tags when you post code? It preserves the indentation (and Python is impossible without correct indentation):

```
#!/usr/bin/[COLOR="Red"]env[/COLOR] python

import pygtk
pygtk.require('2.0')
import gtk

class Base:
    def destr[COLOR="Red"]o[/COLOR]y(self,widget,data=[COLOR="Red"]N[/COLOR]one):
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.show()
        self.window.connect("destroy", self.destroy)

    def main(self):
        gtk.main()

if __name__ == "__main__"[COLOR="Red"]:[/COLOR]
    base = Base()
    base.main()

```

I've highlighted the problems in red:

1. No trailing slash on /usr/bin/env
2. Spelling of destroy
3. None is case-sensitive
4. If statement needs a trailing colon in Python

---

### Post by Hiuhu on 2012-04-03
thanx alot it has worked

---

