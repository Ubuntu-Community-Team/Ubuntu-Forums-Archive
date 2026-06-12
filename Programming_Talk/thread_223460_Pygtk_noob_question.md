---
title: "Pygtk noob question"
date: 2006-07-26
forum: Programming Talk
---

### Post by iamah on 2006-07-26
I'm trying to make learn Pygtk + Glade ([http://www.linuxjournal.com/article/6586](http://www.linuxjournal.com/article/6586)) but I'm getting Syntax Error at line
```
pygtk.require(...)
```

What may be causing this? I installed also the devel pygtk libs...](*,) [-( :-k

---

### Post by Athropos on 2006-07-26
Could you paste the error you get and some more code around this line?

---

### Post by iamah on 2006-07-26
This is the error message:
```
$ ./intel.py   
File "./intel.py", line 6
    pygtk.require("2.0")
    ^
SyntaxError: invalid syntax
```

Here is the file:

```
#!/usr/bin/env python
import sys
try:
 import pygtk
  #tell pyGTK, if possible, that we want GTKv2
  **pygtk.require("2.0")**
except:
  #Some distributions come with GTK2, but not pyGTK
  pass
try:
  import gtk
  import gtk.glade
except:
  print "You need to install pyGTK or GTKv2 ",
  print "or set your PYTHONPATH correctly."
  print "try: export PYTHONPATH=",
  print "/usr/local/lib/python2.2/site-packages/"
  sys.exit(1)
#now we have both gtk and gtk.glade imported
#Also, we know we are running GTK v2


class appgui:
  def __init__(self):
    """
    In this init we are going to display the main
    serverinfo window
    """
    gladefile="project1.glade"
    windowname="serverinfo"
    self.wTree=gtk.glade.XML (gladefile,windowname)
    # we only have two callbacks to register, but
    # you could register any number, or use a
    # special class that automatically
    # registers all callbacks. If you wanted to pass
    # an argument, you would use a tuple like this:
    # dic = { "on button1_clicked" : \
             (self.button1_clicked, arg1,arg2) , ...
    
dic = { "on_button1_clicked" : \
            self.button1_clicked,
            "on_serverinfo_destroy" : \
            (gtk.mainquit) }
    self.wTree.signal_autoconnect (dic)
    return
  
#####CALLBACKS
  def button1_clicked(self,widget):
    print "button clicked"
# we start the app like this...
app=appgui()
gtk.mainloop()
```

---

### Post by iamah on 2006-07-26
problem solved!
It was an identation problem... I just became a Python fundamentalist, identation checking is great

---

### Post by Daverz on 2006-07-27
What editor are you using?  If possible, set it up to use spaces for tabs.  This should be the default for python-mode under emacs (for gnu emacs, you may need to download python-mode), and it's a menu setting in gvim.

---

### Post by forrestcupp on 2006-07-29
Before I saw that you already solved it, I was thinking that the pygtk.require line looked like it was one space too far to the right.  It's crazy that Python is that picky, but it is.

---

