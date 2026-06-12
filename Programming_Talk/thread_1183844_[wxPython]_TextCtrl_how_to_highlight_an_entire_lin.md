---
title: "[wxPython] TextCtrl: how to highlight an entire line?"
date: 2009-06-10
forum: Programming Talk
---

### Post by dodle on 2009-06-10
I'm trying to highlight a whole line when the left mouse button is pressed within a wx.TextCtrl.  I don't know if I am going about it the right way, but here is my code so far:

lineselect.py:
[php]#! /usr/bin/env python

# Select the entire line when the left mouse button is pressed

import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, wx.DefaultPosition, (100,200),
                            style=wx.DEFAULT_FRAME_STYLE & ~(wx.RESIZE_BORDER|wx.RESIZE_BOX|wx.MAXIMIZE_BOX))
        
        self.Center()
        
        self.display_area = wx.TextCtrl(self, -1, style=wx.TE_MULTILINE|wx.TE_READONLY)
        
        text = "Line 1\nLine 2\nLine 3\nLine 4\nLine 5"
        self.display_area.SetValue(text)
        
        wx.EVT_LEFT_DOWN(self.display_area, self.selectLine)
        self.POS = wx.EVT_MOTION(self.display_area, self.mousePOS)
    
    def selectLine(self, event):
        """Uses the mouse position to find which line to highlight"""
        self.display_area.SetFocus()
        print self.POS
    
    def mousePOS(self, event):
        """Finds the position of the mouse"""
        self.POS = event.GetPosition()
        return self.POS

class LineSelect(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "Line Select")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = LineSelect(0)
app.MainLoop()[/php]

---

