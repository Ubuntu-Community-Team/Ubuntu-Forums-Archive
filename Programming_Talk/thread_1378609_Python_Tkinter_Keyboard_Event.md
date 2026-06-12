---
title: "Python Tkinter Keyboard Event"
date: 2010-01-11
forum: Programming Talk
---

### Post by PropheticAngel on 2010-01-11
I have been having issues getting a Tkinter program to see my keyboard events.  It will see clicks and mouse based events but has not responded to things like <F1> or <Up>

Any ideas?

```
#! /usr/bin/python

from Tkinter import *

root = Tk()

def callback(event):
    print "You Pressed it!"

frame = Frame(root, width=100, height=100)
frame.bind("<F1>", callback)
frame.pack()

root.mainloop()
```

---

### Post by wmcbrine on 2010-01-11
Your frame doesn't have focus. It works if you bind to root instead, or alternatively, add "frame.focus_set()" before "root.mainloop()".

---

### Post by PropheticAngel on 2010-01-11
And that does it.  Wonderful.   Thanks.

---

