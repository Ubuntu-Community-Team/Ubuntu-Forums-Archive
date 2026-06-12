---
title: "Peculiar wxPython Problem"
date: 2010-06-28
forum: Programming Talk
---

### Post by Boyohazard on 2010-06-28
So I am learning wxPython, following a basic tutorial, but for some reason I can only run the program once through IDLE before getting an error message.

This is the code:
```

import wx

class sampleApp(wx.Frame):

    def __init__(self, parent, id):
        wx.Frame.__init__(self, parent, id, 'This is the title', size=(500, 300))
        panel = wx.Panel(self)
        exitButton = wx.Button(panel, label="Exit", pos=(130,10), size=(60,60))
        self.Bind(wx.EVT_BUTTON, self.closeButton, exitButton)
        self.Bind(wx.EVT_CLOSE, self.closeWindow)

    def closeButton(self, event):
        self.Close(True)

    def closeWindow(self, event):
        self.Destroy()

if __name__ == '__main__':
    app = wx.PySimpleApp()
    frame = sampleApp(parent=None, id=-1)
    frame.Show()
    app.MainLoop()

```

It runs fine the first time, but when I close the window and try running it again I get the following error in IDLE:

```

Traceback (most recent call last):
  File "/home/marc/sample.py", line 20, in <module>
    frame = sampleApp(parent=None, id=-1)
  File "/home/marc/sample.py", line 6, in __init__
    wx.Frame.__init__(self, parent, id, 'This is the title', size=(500, 300))
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_windows.py", line 497, in __init__
    _windows_.Frame_swiginit(self,_windows_.new_Frame(*args, **kwargs))
PyNoAppError: The wx.App object must be created first!

```

I have to shut down and restart IDLE to be able to run the program again.

Any ideas?

---

### Post by robots.jpg on 2010-06-30
For a workaround, try adding
```
del app
```where the application exits.

I don't have an explanation, but I can only reproduce the problem using IDLE under Ubuntu.  On a Windows system with the same version of IDLE and wxPython, it doesn't happen.  There is also no problem invoking the program multiple times from a command prompt.

---

### Post by manoj_gudi on 2011-12-15
Even I was getting the same problem; I read somewhere that this conflict arises since Python IDLE primarily uses wxpython

The work-around works

Thanks

---

