---
title: "[SOLVED] Python gui for bash script"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by gmxgeek on 2008-08-31
Hello all. I have never written anything in python, but have been told it would be the best language to write a gui for a bash script. Basically, i need a window that has 4 textboxes with labels, and one button, that when pressed will pass the textbox values to my bash script.

any takers?

---

### Post by ad_267 on 2008-08-31
Yeah python and pygtk would probably be the best idea. You can use glade3 to create a simple gui. There's a good tutorial here that covers glade and gtk in python and in C: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

For python you probably want to check out Dive Into Python: [file:///usr/share/doc/diveintopython/html/toc/index.html](file:///usr/share/doc/diveintopython/html/toc/index.html)

It should be pretty easy to get all the input and then just use something like:
```
os.system("./your_script "+options)
```
to call your script.

---

### Post by gmxgeek on 2008-08-31
Thanks. One more quick question. Say i have a textbox called txtServer. How can i store the value of the textbox to a variable in python?

---

### Post by gmxgeek on 2008-08-31
> **ad_267 said:**
> Yeah python and pygtk would probably be the best idea. You can use glade3 to create a simple gui. There's a good tutorial here that covers glade and gtk in python and in C: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

For python you probably want to check out Dive Into Python: [file:///usr/share/doc/diveintopython/html/toc/index.html](file:///usr/share/doc/diveintopython/html/toc/index.html)

It should be pretty easy to get all the input and then just use something like:
```
os.system("./your_script "+options)
```
to call your script.

```

NameError: global name 'os' is not defined

```

EDIT: Forgot to import os -.-

---

### Post by ad_267 on 2008-08-31
The pygtk documentation should contain everything you need to know. From the page on text entries:

> The contents of the Entry can be retrieved by using a call to the following method. This is useful in the callback methods described below.
```
text = entry.get_text()
```


[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

---

### Post by gmxgeek on 2008-08-31
> **ad_267 said:**
> The pygtk documentation should contain everything you need to know. From the page on text entries:



[http://www.pygtk.org/pygtk2tutorial/index.html](http://www.pygtk.org/pygtk2tutorial/index.html)

right, but if i have a button click method, and a textbox named txtServer, how would I access the entry?

```

text = txtServer.get_text()

```

comes up with 'NameError: global name 'txtServer' is not defined'
So, i guess what i am asking is how to refer to the textbox object from inside a button event


here is what i am working with
```

#!/usr/bin/env python

import sys
import os
try:
        import pygtk
        pygtk.require("2.0")
except:
        pass
try:
        import gtk
        import gtk.glade
except:
        sys.exit(1)

class NetworkMnt:
        def __init__(self):
                self.gladefile = "networkmnt.glade"
                self.wTree = gtk.glade.XML(self.gladefile)
                dic = { "on_cmdMount_clicked" : self.cmdMount_clicked,
                        "on_cmdExit_clicked" : gtk.main_quit,
                        "on_Prompt_destroy" : gtk.main_quit }
                self.wTree.signal_autoconnect(dic)

        def cmdMount_clicked(self, widget):
                print txtServer.get_text();

if __name__ == "__main__":
        mnt = NetworkMnt()
        gtk.main()

```

---

### Post by ad_267 on 2008-08-31
I'm pretty new to python and gtk myself and I'm a bit more familiar with using gtk.Builder rather than gtk.glade, but I think you need to use:

```

server = self.wTree.get_widget("txtServer");
print server.get_text();

# or
print self.wTree.get_widget("txtServer").get_text();

```

---

### Post by gmxgeek on 2008-08-31
Perfect! Gold star for you!

---

