---
title: "wxPython - processing 2 button events with 1 handler?"
date: 2009-04-17
forum: Programming Talk
---

### Post by dodle on 2009-04-17
In my program I have a text area and two buttons.  I want each button to print something different to the text area but only using one handler.  The handler should be able to figure out which button was pressed and print according to the result.  I hope that I am clear.  (I hope that I am using the correct terminology: handlers and events)

Here is my code:
[php]import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, wx.DefaultPosition, (400,300))
        
        main_panel = wx.Panel(self, -1)
        
        self.text_area = wx.TextCtrl(main_panel, -1)
        
        buttonA = wx.Button(main_panel, -1, "A")
        buttonB = wx.Button(main_panel, -1, "B")
        
        h_sizer = wx.BoxSizer(wx.HORIZONTAL)
        h_sizer.Add(buttonA, 1, wx.EXPAND)
        h_sizer.Add(buttonB, 1, wx.EXPAND)
        
        v_sizer = wx.BoxSizer(wx.VERTICAL)
        v_sizer.Add(self.text_area, 4, wx.EXPAND)
        v_sizer.Add(h_sizer, 1, wx.EXPAND)
        
        main_panel.SetAutoLayout(True)
        main_panel.SetSizer(v_sizer)
        main_panel.Layout()
        
        wx.EVT_BUTTON(buttonA, -1, self.OnPress)
        wx.EVT_BUTTON(buttonB, -1, self.OnPress)
        
    def OnPress(self, event):
        #### I don't know what to put here ####
        pass
        
class MyApp(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Object Oriented Practice")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = MyApp(0)
app.MainLoop()[/php]

I could create two separate handlers:
[php]def OnPressA(self, event):
    self.text_area.AppendText("Pressed Button A\n")

def OnPressB(self, event):
    self.text_area.AppendText("Pressed Button B\n")[/php]

...but that doesn't seem like efficient coding.  Does anyone know how to help me with my dilemma?  I haven't found a solution yet in the docs, and nothing googling so far.

---

### Post by elCabron on 2009-04-17
You could use different IDs for each button and check on these in the event handler:

```

def OnPress(self, event):
    if event.GetId() == 1:
        self.text_area.AppendText("Pressed Button A")
    else:
        self.text_area.AppendText("Pressed Button B")

```

---

### Post by dodle on 2009-04-17
I'll try out your idea as well, but I've found a solution that works for me:

[php]    def OnPress(self, event):
        button_object = event.GetEventObject()
        button_label = button_object.GetLabel()
        print button_label
        if button_label == "A":
            self.text_area.AppendText("Button A Pressed\n")
        if button_label == "B":
            self.text_area.AppendText("Button B Pressed\n")
[/php]

I found it at [http://genotrance.wordpress.com/2006/09/30/wxpython-widgets-part-ii/](http://genotrance.wordpress.com/2006/09/30/wxpython-widgets-part-ii/)

**Edit:** Using an ID instead of a Label will probably be more useful in the future.

---

