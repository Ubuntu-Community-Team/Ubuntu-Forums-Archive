---
title: "wx - python, possibly last question :P"
date: 2010-06-18
forum: Programming Talk
---

### Post by smitty92 on 2010-06-18
Ok, so im beginning to use wxPython for my gui and i finally have it to where i know a little, but i just need one thing, how do i display what it does in the terminal in a dialogue box instead or even the status bar thanks
im trying to venture completely away from the terminal

---

### Post by soltanis on 2010-06-18
Well, there's no direct way of doing it, but if you're trying to print status output into a GUI then one way to use it is to use a text editing element. See wxTextCtrl:

[http://www.devshed.com/c/a/Python/A-Close-Look-at-wxPython-Controls/4/](http://www.devshed.com/c/a/Python/A-Close-Look-at-wxPython-Controls/4/)

Useful information there.

---

### Post by DanielWaterworth on 2010-06-18
You can override stdout with your own class, something like:
```
import sys

text_in_box = ''

class CustomPrinter:
        def write(self, value):
                text_in_box += value
                sys.__stdout__.write(value)

sys.stdout = CustomPrinter()
```

Where text_in_box is changed to the textbox contents.

---

