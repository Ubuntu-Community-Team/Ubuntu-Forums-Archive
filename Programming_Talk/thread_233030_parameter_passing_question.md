---
title: "parameter passing question"
date: 2006-08-09
forum: Programming Talk
---

### Post by krypto_wizard on 2006-08-09
I wrote a small app in wxPython using wxGlade as designer tool. wxGlade
brings and writes a lot of code by itself and thats where my confusion
started. Its about parameter passing. Here is my little confusion.
```

***************CODE BEGINS************************************
class MyFrame1(wx.Frame):
    def __init__(self, *args, **kwds):
         .....
         .....
    def OnEdit(self, event):
         sim_name = 'some_string'
         win = MyFrame2(self, -1, "")
         win.Show(True)
********************************************************************

class MyFrame2(wx.Frame):
    def __init__(self, *args, **kwds):
         .....
         .....
    def onLaunch(self, event):
         ## This function needs to use the parameter sim_name which is
in class MyFrame1-->OnEdit
***************CODE ENDS************************************

```
I want to pass sim_name parameter to MyFrame2 in def OnEdit function but I don't know how to do it. I tried couple of things but always got some error. I have done some parameter passing in normal Python code but *args and **kwds is a little confusing.

Could you please tell me how to send parameter "sim_name" from
MyFrame1(in OnEdit function) and how to recieve it in MyFrame2 so that
I can use that parameter in MyFrame2 namespace.

Every help is appreciated.

Thanks

---

### Post by thumper on 2006-08-09
```
class MyFrame1(wx.Frame):
   # ...
   def onEdit(self, event):
      win = MyFrame2('sim_name', self, -1, "")
      win.Show(True)

class MyFrame2(wx.Frame):
   def __init__(self, sim_name, *args, **kwds):
      self.sim_name = sim_name
      ...

```

---

### Post by thumper on 2006-08-09
The *args matches the rest of the positional args passed to the function, whereas the **kwds matches the named args.

By putting the simulation name first in the constructor of MyFrame2 you can then just collect the rest of the args in the same manner and pass them on to the Frame constructor.

---

### Post by krypto_wizard on 2006-08-11
As always thanks thumper.

---

