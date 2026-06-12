---
title: "[wxPython] Trouble Overlapping Panels"
date: 2010-04-05
forum: Programming Talk
---

### Post by dodle on 2010-04-05
I have a window with three different panels.  I only want one panel showing at a time depending on which button is pressed (if the "blue" button is pressed, I want only the "blue" panel to be shown).  The problem I am having is that the "blue" and "green" panels are not expanded when I press their corresponding button, though once I resize the window they expand.  I think the problem lies somewhere with the [color=blue]wx.BoxSizer[/color] and the [color=red].Hide()[/color] function used when creating the panels.  

[php]#! /usr/bin/env python

import wx

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title)
		
		# create 3 panels of 3 different colors
		self.bg1 = wx.Panel(self, 1) # red panel is shown by default
		self.bg1.SetBackgroundColour("red")
		self.bg2 = wx.Panel(self, 1)
		self.bg2.SetBackgroundColour("blue")
		self.bg3 = wx.Panel(self, 1)
		self.bg3.SetBackgroundColour("green")
		
		# show some text on each panel
		red_txt = wx.StaticText(self.bg1, -1, "This is the red panel\nPress a button to switch panels")
		blu_txt = wx.StaticText(self.bg2, -1, "This is the blue panel")
		gre_txt = wx.StaticText(self.bg3, -1, "This is the green panel")
		
		# hide blue & green panels
		self.bg2.Hide()
		self.bg3.Hide()
		
		# 3 buttons for changing the panels
		button1 = wx.Button(self, -1, "Red")
		button2 = wx.Button(self, -1, "Blue")
		button3 = wx.Button(self, -1, "Green")
		button_group = (button1, button2, button3)
		
		button_sizer = wx.BoxSizer(wx.HORIZONTAL) #sizer for organizing buttons
		for button in button_group:
			button.Bind(wx.EVT_BUTTON, self.Change)
			button_sizer.Add(button, -1)
		
		self.sizer = wx.BoxSizer(wx.VERTICAL)
		self.sizer.Add(self.bg1, 8, wx.EXPAND)
		self.sizer.Add(self.bg2, 8, wx.EXPAND)
		self.sizer.Add(self.bg3, 8, wx.EXPAND)
		self.sizer.Add(button_sizer, 1)
		
		self.SetAutoLayout(True)
		self.SetSizer(self.sizer)
		self.Layout()
	
	def Change(self, event):
		""" shows the panel corresponding to the button pressed """
		obj = event.GetEventObject()
		label = obj.GetLabel()
		if label == "Red": # hides blue & green panels
			self.bg2.Hide()
			self.bg3.Hide()
			self.bg1.Show()
		elif label == "Blue": # hides red & green panels
			self.bg1.Hide()
			self.bg3.Hide()
			self.bg2.Show()
		elif label == "Green": # hides red & blue panels
			self.bg1.Hide()
			self.bg2.Hide()
			self.bg3.Show()
			

class MainApp(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "Changing Panels")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = MainApp(0)
app.MainLoop()[/php]

**Edit:** Found the answer in the [wxWidgets documentation]("http://docs.wxwidgets.org/stable/wx_sizeroverview.html") and added [color=red]self.sizer.Layout()[/color] to the end of my event handler.

---

