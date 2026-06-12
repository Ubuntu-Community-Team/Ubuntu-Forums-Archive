---
title: "[Python] Class not doing what I want it to"
date: 2009-06-09
forum: Programming Talk
---

### Post by dodle on 2009-06-09
I created a class derived from a wx.Panel that should change colors when [color=red]MyWindow.ChangeColor(color)[/color] is called.  It works when the program is first launched, the color of the widget is set to one of five.  But when I create a button to try and change the color and press it, nothing happens.  

MyClass.py:
[php]import wx, random

class MyWindow(wx.Panel):
    """A widget that changes colors"""
    def __init__(self, parent, id):
        wx.Panel.__init__(self, parent, id)
        
    def ChangeColor(self, color):
        self.SetBackgroundColour(color)

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title)
        
        self.test = MyWindow(self, -1)
        self.BGColor(None) # Sets the background color upon execution
        
        color_button = wx.Button(self.test, -1, "Change Colors") # Button to change the background color
        color_button.Bind(wx.EVT_BUTTON, self.BGColor)
    
    def BGColor(self, event):
        colors = ("Blue", "Black", "Red", "Yellow", "Green")
        random_color = random.randrange(5)
        self.test.ChangeColor(colors[random_color])
        print "color changed to %s" % colors[random_color]

class TestApp(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Testing")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = TestApp(0)
app.MainLoop()[/php]

Where have I gone wrong?

---

### Post by mzi on 2009-06-10
Works fine here.
There might be a very small chance that the random function has always selected the same color at the time you tried.

---

