---
title: "TK inter"
date: 2008-11-05
forum: Programming Talk
---

### Post by chips24 on 2008-11-05
does ubuntu come with TKinter by default? or do i have to use IDLE to get TKinter

---

### Post by crazyfuturamanoob on 2008-11-05
> **chips24 said:**
> does Python come with TKinter  or do i have to use IDLE to program with TKinter.

Excuse me? Could you explain a little more clear?

---

### Post by stevescripts on 2008-11-05
*IF* (and at my age, that's a big if ;) ) I recall correctly Tkinter comes with
ubuntu, but IDLE doesn't.  (somebody will correct me if I am wrong here).

You do not *have* to use IDLE to program with Tkinter, any text editor will do.

A simple example:
```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("PlusOne")

root.resizable(0, 0)

def mycommand():
	temp = w.cget("text")
	temp = temp + 1
	w.configure(text=temp)

w = Label(root, text=0, fg="red", width=16)

w.grid(row=0, column=0)

b = Button(root, text="Add 1", command=mycommand )

b.grid(row=0, column=1)

root.mainloop()

```

Copy and paste with your favorite text editor (such as Gedit)

Save, and chmod +x ...

Have fun!

Steve

---

