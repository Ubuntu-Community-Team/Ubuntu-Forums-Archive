---
title: "Problem with wxPython and Ubuntu"
date: 2005-03-11
forum: Programming Talk
---

### Post by Murena on 2005-03-11
Hello, 

Using the packaged version of wxpython on Ubuntu (i've tried both warty and hoary) I receive an error in the following code. The code works on windows or other linuxes.
```

#!/usr/bin/env python

import wx

class plot_printout(wx.Printout):
    def __init__(self):
       wx.Printout.__init__(self)


class GraphsFrame(wx.Frame):
    def __init__(self, parent, ID, title, probe):
       wx.Frame.__init__(self, parent, ID, title, style=wx.DEFAULT_FRAME_STYLE)
       self.Maximize()
       self.probe = probe
       self.CreateStatusBar(1)
       test = plot_printout()


if __name__ == "__main__":
   app = wx.PySimpleApp(0)
   wx.InitAllImageHandlers()
   mainframe = GraphsFrame(None, -1, "Title", 1)
   app.SetTopWindow(mainframe)
   mainframe.Show()
   app.MainLoop()

```

I receive this error

Traceback (most recent call last):
  File "prove2.py", line 22, in ?
    mainframe = GraphsFrame(None, -1, "Grafico", 1)
  File "prove2.py", line 16, in __init__
    gino = plot_printout()
  File "prove2.py", line 7, in __init__
    wx.Printout.__init__(self)
  File "/usr/lib/python2.4/site-packages/wx-2.5.3-gtk2-unicode/wx/_windows.py", line 4363, in __init__
    self.this = newobj.this
AttributeError: 'str' object has no attribute 'this'



Do you receive this error with you Ubuntus?

---

### Post by toojays on 2005-03-11
Your code works on my computer, but I have libwxgtk2.4-python, where you seem to be using version 2.5 of wxpython.

---

