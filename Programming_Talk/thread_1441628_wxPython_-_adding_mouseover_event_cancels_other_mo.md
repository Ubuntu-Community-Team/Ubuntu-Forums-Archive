---
title: "wxPython - adding mouseover event cancels other mouse events"
date: 2010-03-29
forum: Programming Talk
---

### Post by dodle on 2010-03-29
I have a panel that is divided into two sections.  The top is a group of radio buttons and the bottom displays text with information about the radio buttons.  

When the mouse hovers over a radio button, I want the displayed information to change in the lower section.  My problem is that when I add the [color=red]wx.EVT_ENTER_WINDOW[/color] the other mouse events are destroyed, e.g. clicking on the radio button doesn't do anything.  How can I add my mouseover and mouseout events and retain the default mouse events for the radio buttons?

[php]import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title)
        
        # --- Main window's background
        bg = wx.Panel(self, -1)
        
        # --- Create two radio buttons
        radio_A = wx.RadioButton(bg, -1, "A", style=wx.RB_GROUP)
        radio_B = wx.RadioButton(bg, -1, "B")
        
        # --- Descriptions for radio buttons
        self.text_A = "A big fat hunk of cheese"  #text to show when mouse over "A"
        self.text_B = "Two turtles turn tediously toward town"  # text to show when mouse over "B"
        
        # --- Default displayed text
        self.info_text = "Hover mouse over options to see description"
        self.info = wx.StaticText(bg, -1, self.info_text)
        
        # --- Add mouseover and mouseout events to radio buttons
        button_group = (radio_A, radio_B)
        for i in button_group:
            wx.EVT_ENTER_WINDOW(i, self.onMouseOver)
            wx.EVT_LEAVE_WINDOW(i, self.onMouseOut)
        
        # --- Organizing widgets
        radio_sizer = wx.BoxSizer(wx.HORIZONTAL)
        radio_sizer.Add(radio_A, 1)
        radio_sizer.Add(radio_B, 1)
        
        main_sizer = wx.BoxSizer(wx.VERTICAL)
        main_sizer.Add(radio_sizer, 1)
        main_sizer.Add(self.info, 5)
        
        bg.SetSizer(main_sizer)

    def onMouseOver(self, event):  #Display text when mouse hovers over radio button
        obj = event.GetEventObject()
        label = obj.GetLabel()
        if label == "A":
            self.info.SetLabel(self.text_A)
        elif label == "B":
            self.info.SetLabel(self.text_B)

    def onMouseOut(self, event):  #Reset the text back to default when the mouse is removed
        self.info.SetLabel(self.info_text)

class MainApp(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Mouseover Radio Button")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = MainApp(0)
app.MainLoop()[/php]

**Edit:** Got answer at [www.python-forum.org]("http://www.python-forum.org/pythonforum/viewtopic.php?f=4&t=17663&start=0"):  added [color=red]event.Skip()[/color] to the end of my event handlers.

[php]    def onMouseOver(self, event):  #Display text when mouse hovers over radio button
        obj = event.GetEventObject()
        label = obj.GetLabel()
        if label == "A":
            self.info.SetLabel(self.text_A)
        elif label == "B":
            self.info.SetLabel(self.text_B)
        event.Skip()

    def onMouseOut(self, event):  #Reset the text back to default when the mouse is removed
        self.info.SetLabel(self.info_text)
        event.Skip()[/php]

---

