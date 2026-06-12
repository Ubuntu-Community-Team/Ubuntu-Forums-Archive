---
title: "wxPython error, need help"
date: 2006-12-24
forum: Programming Talk
---

### Post by maddog39 on 2006-12-24
Hello all,

I am trying to learn wxPython from their website's tutorial(s) and on the more advanced model of "Hello World" in part 1 I keep getting this error with the menus.
```

maddog39@maddog39-laptop:~$ ./wxpython2.py
Traceback (most recent call last):
  File "./wxpython2.py", line 28, in ?
    app = MyApp(0)
  File "/usr/lib/python2.4/site-packages/wx-2.4-gtk-ansi/wxPython/wx.py", line 1951, in __init__
    _wxStart(self.OnInit)
  File "./wxpython2.py", line 23, in OnInit
    frame = MyFrame(NULL, -1, "Hello from wxPython")
  File "./wxpython2.py", line 12, in __init__
    menu.Append(ID_ABOUT, "&About", "More information about this program.")
NameError: global name 'ID_ABOUT' is not defined

```
Here is the code:
```

#!/usr/bin/env python

from wxPython.wx import *

class MyFrame(wxFrame):
    def __init__(self, parent, ID, title):
        wxFrame.__init__(self, parent, ID, title, wxDefaultPosition, wxSize(200, 150))
        self.CreateStatusBar()
        self.SetStatusText("This is the statusbar.")
        
        menu = wxMenu()
        menu.Append(ID_ABOUT, "&About", "More information about this program.")
        menu.AppendSeparator()
        menu.Append(ID_EXIT, "E&xit", "Terminate the program.")
        
        menuBar = wxMenuBar()
        menuBar.Append(menu, "&File");
        
        self.SetMenuBar(menuBar)

class MyApp(wxApp):
    def OnInit(self):
        frame = MyFrame(NULL, -1, "Hello from wxPython")
        frame.Show(true)
        self.SetTopWindow(frame)
        return true

app = MyApp(0)
app.MainLoop()

```
Anyone have an idea of the problem.

Thanks
-maddog39

---

### Post by kperkins on 2006-12-25
Yes.
You didn't define ID_ABOUT (or  ID_EXIT)
Either define them:
ID_ABOUT = 100
ID_EXIT = 101 
eg.
or ID_ABOUT = wx.NewId() etc.
Or instead of:
```

menu.Append(ID_ABOUT, "&About", "More information about this program.")

```do this:
```

menu.Append(wx.NewId(), "&About", "More information about this program.")

```

---

### Post by maddog39 on 2006-12-25
Ahh, thanks! Im new to python as well and missed the part about defining globals. lol. I got it now.

---

