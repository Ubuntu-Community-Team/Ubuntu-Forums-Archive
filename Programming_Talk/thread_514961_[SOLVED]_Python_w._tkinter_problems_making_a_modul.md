---
title: "[SOLVED] Python w. tkinter: problems making a modules file?"
date: 2007-08-01
forum: Programming Talk
---

### Post by tjansson on 2007-08-01
I am writing a bunch of small GUI's in Python with Tkinter and I would like to put my classes in a separate file, so I wouldn't have make changes to all the GUI's when i change something in the classes.

I started creating a file to be my module file and called geomodule.py
```

	self.line = Label(frame, bd=1, relief=RAISED, width=maxwidth, text="",fg="white", bg="dark blue")
	self.line.grid(row=Ilineposition, column=0, columnspan=4, sticky=W)

```
In the GUI.py i then write
```

from Tkinter import *
import geomodule

```
and call the function with the following:
```

geomodule.seperator_line(24)

```
but that doesn't work since it apparently it doesn't that Label is a tkinter obejct:
```

Traceback (most recent call last):
  File "./geocol-gui.py", line 288, in <module>
    app = App(root)
  File "./geocol-gui.py", line 231, in __init__
    geomodule.seperator_line(24)
  File "/mnt/nfs/Documents/Firma/Projekter/geocol-gui/geomodule.py", line 2, in seperator_line
    self.line = Label(frame, bd=1, relief=RAISED, width=maxwidth, text="",fg="white", bg="dark blue")
NameError: global name 'Label' is not defined

```

So what is the proper way to do this?

---

### Post by pmasiar on 2007-08-01
```

from Tkinter import *
import geomodule

```

1) *Never* use "from module import *". It is called "star of death", you will never know what names were injected to your main namespace, and if they clash with names you defined, you are asking for problems, and you *will* get them. *Always* use "from module import name1, name2". Remember: **Explicit is better than implicit.** So when facing error like that, you can easily see where the name came from. 

Type in Python shell: "import this" and read the zen wisdom of Python. *Every line* is condensed wisdom, worth remembering. Trust me.

> **tjansson said:**
> 
NameError: global name 'Label' is not defined


2) Error you got is caused by not importing Label into geomodule.py. geomodule.py is separate from your main program and needs to import all modules it uses. You need something like "from Tkinter import Label"

---

### Post by tjansson on 2007-08-02
1) You are right, but my program is not that big and I don't have problems with namespace. I will keep you concerns in mind though. :D

2) That was exactly the problem -  thanks! :D

---

