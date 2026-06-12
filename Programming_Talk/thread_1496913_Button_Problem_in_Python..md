---
title: "Button Problem in Python."
date: 2010-05-29
forum: Programming Talk
---

### Post by Axolotl9250 on 2010-05-29
I have a problem with a Text Editor coded in Python, and created with the help of wxGlade.
Its a plain Frame with some sizers, a File menu with Open, About, and Exit. And a button under the txtctrl called Close that should close the application. Everything works apart from when I try to use File->Exit or the close button. When I click on either I get the following error appear in the terminal:
```
ben@ben-laptop:~/Documents/Programming/wxPython$ python gwgladetexteditor
Traceback (most recent call last):
  File "gwgladetexteditor", line 69, in ButtonClose
    self.Close(True)
TypeError: 'Button' object is not callable
Traceback (most recent call last):
  File "gwgladetexteditor", line 66, in OnExit
    self.Close(True)
TypeError: 'Button' object is not callable
```

The following are the bits of python for the frame with the button and the menubar. And then the coding for the events. I'd be grateful if someone could tell me where I've gone wrong as I can't see where I've gone wrong.

Code for The frame, menubar, and button (TextCtrl is in there too)
```
def __init__(self, *args, **kwds):
        # begin wxGlade: MainFrame.__init__
        kwds["style"] = wx.DEFAULT_FRAME_STYLE
        wx.Frame.__init__(self, *args, **kwds)
        self.label_1 = wx.StaticText(self, -1, "Edit text-files below.", style=wx.ALIGN_CENTRE)
        self.text_ctrl_1 = wx.TextCtrl(self, -1, "", style=wx.TE_MULTILINE)
        self.Close = wx.Button(self, -1, "Close")
    self.Bind(wx.EVT_BUTTON, self.ButtonClose, self.Close)        

        # Menu Bar
        self.frame_2_menubar = wx.MenuBar()
        self.File = wx.Menu()
        self.Open = wx.MenuItem(self.File, wx.NewId(), "&Open", "Open a File for Editing", wx.ITEM_NORMAL)
        self.File.AppendItem(self.Open)
        self.About = wx.MenuItem(self.File, wx.NewId(), "&About", "About the Text Editor", wx.ITEM_NORMAL)
        self.File.AppendItem(self.About)
        self.Exit = wx.MenuItem(self.File, wx.NewId(), "&Exit", "Close the Program", wx.ITEM_NORMAL)
        self.File.AppendItem(self.Exit)
        self.frame_2_menubar.Append(self.File, "&File")
        self.SetMenuBar(self.frame_2_menubar)
        # Menu Bar end
        self.frame_2_statusbar = self.CreateStatusBar(1, 0)

        self.__set_properties()
        self.__do_layout()
        # end wxGlade
    self.Bind(wx.EVT_MENU, self.OnExit, self.Exit)
    self.Bind(wx.EVT_MENU, self.OnAbout, self.About)
    self.Bind(wx.EVT_MENU, self.OnOpen, self.Open)
```

Code for the Event.
```
def OnExit(self,e):
    self.Close(True)

    def ButtonClose(self,e):
    self.Close(True)

    def OnAbout(self,e):
    # A message dialogue box with an OK button.
    dlg = wx.MessageDialog(self, "A small text editor", " About Sample Editor", wx.OK)
    dlg.ShowModal() # Show it.
    dlg.Destroy() # finally destroy it when finished.

    def OnOpen(self,e):
    """ Open a file"""
    self.dirname = ''
    dlg = wx.FileDialog(self, "Choose a file", self.dirname, "", "*.*", wx.OPEN)
    if dlg.ShowModal() == wx.ID_OK:
            self.filename = dlg.GetFilename()
            self.dirname = dlg.GetDirectory()
            f = open(os.path.join(self.dirname, self.filename), 'r')
            self.control.SetValue(f.read())
            f.close()
        dlg.Destroy()

```

---

### Post by simeon87 on 2010-05-29
Like the error indicates, you're calling the button itself now: self.Close is the button, not a function (see your __init__).

See the documentation [here]("http://www.wxpython.org/docs/api/wx.Window-class.html"). You're now hiding the Close function of the wx Window by redefining Close yourself. You should rename the button and it should work.

---

### Post by Axolotl9250 on 2010-05-29
I corrected the button but now it gives me:
```
ben@ben-laptop:~/Documents/Programming/wxPython$ python gwgladetexteditor
Traceback (most recent call last):
  File "gwgladetexteditor", line 92, in <module>
    frame = MainFrame (None, title="Text Editor")
  File "gwgladetexteditor", line 37, in __init__
    self.__do_layout()
  File "gwgladetexteditor", line 58, in __do_layout
    sizer_1.Add(self.Close, 0, wx.ADJUST_MINSIZE, 0)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 11711, in Add
    return _core_.Sizer_Add(*args, **kwargs)
TypeError: wx.Window, wx.Sizer, wx.Size, or (w,h) expected for item

```Of which I have no idea about as the code was generated with xwGlade, especially the layout stuff, If I'd written it myself I would have gone for a cruder way of writing it which I would have found easier to follow at this point. None of the tutorials I've read so far have really explain what the _init_ line with *args and **kwds means as its a case of "copy this, well done you have box now".

---

### Post by Axolotl9250 on 2010-05-29
Apologies, I did a bit more tweaking and now it works, although I do  still have the issue with my other post (The one without xwGlade where no events work. And thanks for the help, simeon87.

---

