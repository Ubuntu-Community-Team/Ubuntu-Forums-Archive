---
title: "[SOLVED] wxpython: no attribute 'Frame'"
date: 2008-05-31
forum: Programming Talk
---

### Post by Bill magee on 2008-05-31
Hello python fans,

I have just installed wxpython and I cut and pasted this sample code as a test:

```

import wx

class Frame(wx.Frame):
    pass
class App(wx.App):
    def OnInit(self):
        frame = wx.Frame(parent=None, title='Bare')
        frame.Show()
        return True
app = App()
app.MainLoop()

```

But I get the following error message from Idle:

```

Traceback (most recent call last):
  File "/home/bill/python/wx2.py", line 1, in <module>
    import wx
  File "/home/bill/python/wx.py", line 3, in <module>
    class MyFrame(wx.Frame):
AttributeError: 'module' object has no attribute 'Frame'
>>> 

```

Any ideas what I am doing wrong?

Cheers!

---

### Post by cdekter on 2008-06-01
> **Bill magee said:**
> Hello python fans,

I have just installed wxpython and I cut and pasted this sample code as a test:

```

import wx

class Frame(wx.Frame):
    pass
class App(wx.App):
    def OnInit(self):
        frame = wx.Frame(parent=None, title='Bare')
        frame.Show()
        return True
app = App()
app.MainLoop()

```

But I get the following error message from Idle:

```

Traceback (most recent call last):
  File "/home/bill/python/wx2.py", line 1, in <module>
    import wx
  File "/home/bill/python/wx.py", line 3, in <module>
    class MyFrame(wx.Frame):
AttributeError: 'module' object has no attribute 'Frame'
>>> 

```

Any ideas what I am doing wrong?

Cheers!


Your problem here is that you have a file called 'wx.py' which is actually masking the real module 'wx'. So when you say 'import wx', the Python interpreter thinks you mean import your wx.py module (as in /home/bill/python/wx.py) Rename your wx.py to something else and that should fix it.

---

### Post by Bill magee on 2008-06-01
Brilliant! Now it is working perfectly.

---

