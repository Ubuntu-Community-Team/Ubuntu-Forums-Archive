---
title: "[wxPython] EVT_MAXIMIZE doesn't work"
date: 2010-04-29
forum: Programming Talk
---

### Post by dodle on 2010-04-29
[php]import wx

class MainWindow(wx.Frame):
	def __init__(self, parent, id):
		wx.Frame.__init__(self, parent, id, "Maximize Event")
		
		wx.EVT_MAXIMIZE(self, self.OnMaximize)
	
	def OnMaximize(self, event):
		print "Maximized"


app = wx.App()
frame = MainWindow(None, -1)
frame.Show()
app.MainLoop()[/php]

The documentation says that this is the event to use, and I can't find a solution googling.  Does this code work for anyone else?  When the window is maximized, "Maximized" should print out to the terminal.  But it doesn't for me.

**Edit:** [color=red]EVT_ICONIZE[/color] works.

---

