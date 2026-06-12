---
title: "python - update control backcolor in wx"
date: 2009-11-11
forum: Programming Talk
---

### Post by OffAxis on 2009-11-11
I would like to change the backcolour of a panel (and the controls on it), but it's not working.

Any ideas on how to fix?

```
import wx
 
class MyForm(wx.Frame):
 
    def __init__(self):
        wx.Frame.__init__(self, None, wx.ID_ANY,
                                 "change control background")

        self.panel = wx.Panel(self, wx.ID_ANY)
        self.sldr=wx.Slider(self.panel, -1, 206, 0, 255, style=wx.SL_HORIZONTAL|wx.SL_LABELS)
        blueBtn = wx.Button(self.panel,
                           label="Change Background Color")
        blueBtn.Bind(wx.EVT_BUTTON, self.onChangeBackground)
        resetBtn = wx.Button(self.panel, label="Reset")
        resetBtn.Bind(wx.EVT_BUTTON, self.onReset)
 
        topSizer = wx.BoxSizer(wx.VERTICAL)
        btnSizer = wx.BoxSizer(wx.HORIZONTAL)
 
        btnSizer.Add(blueBtn, 0, wx.ALL|wx.CENTER, 5)
        btnSizer.Add(resetBtn, 0, wx.ALL|wx.CENTER, 5)
 
        topSizer.Add(self.sldr, 0, wx.ALL, 5)
        topSizer.Add(btnSizer, 0, wx.CENTER)
        self.panel.SetSizer(topSizer)
 
    def onChangeBackground(self, event):
        """
        Change the background color of the panel
        """
        self.panel.SetBackgroundColour("Blue")
        self.panel.Refresh()
        frame.sldr.Refresh()
    def onReset(self, event):
        """
        Reset the color of the panel to the default color
        """
        self.panel.SetBackgroundColour(wx.NullColor)
        self.sldr.SetBackgroundColour(wx.NullColor)
        self.panel.Refresh()
 
# Run the program
if __name__ == "__main__":
    app = wx.PySimpleApp()
    frame = MyForm()
    frame.Show()
    app.MainLoop()
```

---

### Post by OffAxis on 2009-11-13
what's happening is that the slider back color isn't updating until I click on the control. I've tried using a frame, using a panel, and calling a .Refresh() of the control explicitly, but nothing seems to be working.

any suggestions would be welcome.

---

