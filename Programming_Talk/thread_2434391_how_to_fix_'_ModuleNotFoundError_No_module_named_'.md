---
title: "how to fix ' ModuleNotFoundError: No module named 'tkinter' ' error ?"
date: 2020-01-05
forum: Programming Talk
---

### Post by artunix on 2020-01-05
program:::::::::::::

from tkinter import *

root = Tk()

word = Label(root,text="hello word")

word.pack()

root.mainloop()


error message::::::::::::

Traceback (most recent call last):
  File "py_window.py", line 1, in <module>
    from tkinter import *
ModuleNotFoundError: No module named 'tkinter'

using pyphon version 3.6.9 
on ubuntu 18.04.3 lts

how do I get the program to work/run?

capping T in tkinter does nothing to remove error message.

thanks

---

### Post by spjackson on 2020-01-05
```
sudo apt install python3-tk
```

---

### Post by artunix on 2020-01-05
well the internet said that 'tkinter' was already part of python 3.X.

but it was wrong.. again... [-(

your reply got the programs working again, thank you!

---

