---
title: "wxpython - How to check if a control is enabled?"
date: 2009-04-04
forum: Programming Talk
---

### Post by dodle on 2009-04-04
I want to check to see if a text control is enabled.  
[PHP]textarea = wx.TextCtrl(self, -1)

if textarea == Enabled:
    print "Text area enabled"
if textarea == Disabled:
    print "Text area is disabled"[/PHP]
Something like that.  How is this accomplished?  I haven't found anything in wx's documentation.

---

### Post by simeon87 on 2009-04-04
TextCtrl is a subclass of Window which has IsEnabled.. you could try that: [http://www.wxpython.org/docs/api/wx.Window-class.html#IsEnabled](http://www.wxpython.org/docs/api/wx.Window-class.html#IsEnabled)

---

### Post by dodle on 2009-04-04
> **simeon87 said:**
> TextCtrl is a subclass of Window which has IsEnabled.. you could try that: [http://www.wxpython.org/docs/api/wx.Window-class.html#IsEnabled](http://www.wxpython.org/docs/api/wx.Window-class.html#IsEnabled)

Thank you, that works great.  Here is an example if anyone wants to see it:[PHP]#! /usr/bin/env python

# Testing text controls

import wx

class test(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title)
        
        self.Center()
        
        self.toggle_box = wx.CheckBox(self, -1, "toggle")
        self.toggle_box.Bind(wx.EVT_CHECKBOX, self.onToggle)
        
        self.textarea = wx.TextCtrl(self, -1, "textarea Disabled")
        self.textarea.Disable()
        
        verticalsizer = wx.BoxSizer(wx.VERTICAL)
        verticalsizer.Add(self.toggle_box, 1, wx.EXPAND)
        verticalsizer.Add(self.textarea, 1, wx.EXPAND)
        
        self.SetAutoLayout(True)
        self.SetSizer(verticalsizer)
        self.Layout()
    
    def onToggle(self, event):
        toggleVal = self.toggle_box.GetValue()
        if toggleVal == True:
            self.textarea.Enable()
        if toggleVal == False:
            self.textarea.Disable()
        if self.textarea.IsEnabled() == True:
            self.textarea.SetValue("textarea Enabled")
        if self.textarea.IsEnabled() == False:
            self.textarea.SetValue("textarea Disabled")

class TestApp(wx.App):
    def OnInit(self):
        frame = test(None, -1, "testing")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = TestApp(0)
app.MainLoop()[/PHP]

For this example I could have accomplished the same outcome with the following:[PHP]defOntoggle(self, event):
    toggleVal = self.toggle_box.GetValue()
    if toggleVal == True:
        self.textarea.Enable()
        self.textarea.SetValue("textarea Enabled")
    if toggleVal == False:
        self.texarea.Disable()
        self.textarea.SetValue("textarea Disabled")
[/PHP]

But I wanted to know directly if the textarea was enabled or not.  Thanks again simeon.

---

