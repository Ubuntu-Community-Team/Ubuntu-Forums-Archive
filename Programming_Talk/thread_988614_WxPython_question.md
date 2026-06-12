---
title: "WxPython question"
date: 2008-11-20
forum: Programming Talk
---

### Post by jacensolo on 2008-11-20
I'm starting to learn WxPython, so right now I'm just playing around. I did this (derived from a tutorial):
[php]import wx
class MainWindow(wx.Frame):
    """ We simply derive a new class of Frame. """
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, size=(200,100))
        self.control = wx.TextCtrl(self, 1, style=wx.TE_MULTILINE)
        self.Show(True)
app = wx.PySimpleApp()
frame=MainWindow(None, wx.ID_ANY, 'Small editor')
list = ['a', 'b', 'c', 'd']
for x in list:
	frame = MainWindow(None, wx.ID_ANY, x)
app.MainLoop()
[/php]

To my suprise, the first (and all) frame still showed up. Why is this? Am I not changing the contents of "frame" each time I make a new one with the same name.

If I did this, I wouldn't be suprised. [php]
frame=MainWindow(blahblahblah)
frame2 = MainWindow(blahblahblah)
[/php]

---

### Post by jacensolo on 2008-11-21
Nobody?

---

