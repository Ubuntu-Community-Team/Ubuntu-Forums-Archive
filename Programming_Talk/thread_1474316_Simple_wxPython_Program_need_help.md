---
title: "Simple wxPython Program need help"
date: 2010-05-05
forum: Programming Talk
---

### Post by Eremis on 2010-05-05
Hi everybody!

I am learning wxPython and I ran into a problem...

I have 2 files the first with the class containing "Main Window"
The second with a class containing "Dialog"

What I want to accomplish:
After the user presses a button in main window, a dialog box pops up. In that dialog box the user types a string (for ex. "hello")
when the user click "OK" the program stores the string under a variable, and displays it in the text area in the "Main Window" and destroys the Dialog...

What I have:
I Made both the MainWindow, and dialog (with handlers and components) when the button is pressed the dialog apears, but I dont know how to make the MainWindow read whats inside the dialog text area after the user click OK in the dialog box...

Here are the two files:

MainWindow:
```

import wx
import dialog

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, wx.ID_ANY, title = 'Main Window', size = (200, 200), style = wx.DEFAULT_FRAME_STYLE)
        self.Center()
        
        panel = wx.Panel(self)          
        button = wx.Button(panel, id = wx.ID_ADD, label = 'Show Dialog', pos = (20, 20), size = (120, 60))
        textArea = wx.TextCtrl(panel, pos = (20, 80), size = (120, 40))
        
        wx.EVT_BUTTON(self, wx.ID_ADD, self.OnClick)
        
        self.Show()
        
    def OnClick(self, event):
        dial = dialog.MainDialog(None, -1, 'My dialog')
        dial.ShowModal()
        dial.Destroy()
        
# Program Runner     
app = wx.PySimpleApp()
frame = MainWindow(None, -1, 'Dialog Tester')
app.MainLoop()

```


Dialog:
```

import wx

class MainDialog(wx.Dialog):
    def __init__(self, parent, id, title):
        wx.Dialog.__init__(self, parent, id, title, size=(250, 210))

        panel = wx.Panel(self, -1)
        vbox = wx.BoxSizer(wx.VERTICAL)
        wx.TextCtrl(panel, -1, '', (95, 105))

        hbox = wx.BoxSizer(wx.HORIZONTAL)
        okButton = wx.Button(self, -1, 'Ok', size=(70, 30))
        closeButton = wx.Button(self, -1, 'Close', size=(70, 30))
        hbox.Add(okButton, 1)
        hbox.Add(closeButton, 1, wx.LEFT, 5)

        vbox.Add(panel)
        vbox.Add(hbox, 1, wx.ALIGN_CENTER | wx.TOP | wx.BOTTOM, 10)

        self.SetSizer(vbox)

```


I know there is a dialog that comes with wxPython that I can use that does what I need, but I need to make this work (This is just an example I made, and I am planning to use the example in my final program that is too large to post here...)

Please help,

Thx

---

### Post by robots.jpg on 2010-05-07
One way is to just add a function to your MainDialog class that returns the text in the TextCtrl.  Then you can show the dialog, find out how the user closed it, and then retrieve the value if needed.  Remember that even after it returns, the dialog still exists until it's destroyed.

---

### Post by Eremis on 2010-05-07
Can you show me how this whould be written in code?
(The retriving text from text box....)

---

### Post by robots.jpg on 2010-05-07
Something along these lines:
 
```

class MainWindow(wx.Frame):
 
    # ...
 
    def OnClick(self, event):
        dial = dialog.MainDialog(None, -1, 'My dialog')
        dial.ShowModal()
        # assign the dialog's text to variable dial_text
        dial_text = dial.GetValue()
        dial.Destroy()
 
    #...

```
 
```

class MainDialog(wx.Dialog):
 
    def __init__(self, parent, id, title):
        wx.Dialog.__init__(self, parent, id, title, size=(250, 210))
 
        panel = wx.Panel(self, -1)
        vbox = wx.BoxSizer(wx.VERTICAL)
        textctrl = wx.TextCtrl(panel, -1, '', (95, 105))
 
    #...
 
    def GetValue():
        return textctrl.GetValue()
 

```

---

### Post by Eremis on 2010-05-07
ok, thanks for the help!

---

