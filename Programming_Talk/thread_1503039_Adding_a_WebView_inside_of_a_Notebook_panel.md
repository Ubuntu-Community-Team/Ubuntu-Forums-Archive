---
title: "Adding a WebView inside of a Notebook panel"
date: 2010-06-06
forum: Programming Talk
---

### Post by ATL™ on 2010-06-06
I'm still fairly new to Python and I'm wondering how to add a webkit.WebView inside of a Notebook tab page.

Using wxPython and python-webkit

what I have:
[PHP]#!/usr/bin/env python

import wx
import webkit

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title, size=(755,476))

		menuFile = wx.Menu()
		menuFile.Append(wx.ID_EXIT, "&Exit")

		menuHelp = wx.Menu()
		menuHelp.Append(wx.ID_ABOUT, "&About")

		menu_bar = wx.MenuBar()
		menu_bar.Append(menuFile, "&File")
		menu_bar.Append(menuHelp, "&Help")
		self.SetMenuBar(menu_bar)

		wx.EVT_MENU(self, wx.ID_ABOUT, self.onAbout)
		wx.EVT_MENU(self, wx.ID_EXIT, self.onExit)

		self.tabbed = wx.Notebook(self, -1, style=(wx.NB_TOP))
		self.panel1 = wx.NotebookPage(self.tabbed, -1)
		self.panel2 = wx.NotebookPage(self.tabbed, -1)
		self.tabbed.AddPage(self.panel1, "Video")
		self.tabbed.AddPage(self.panel2, "Chat")

	def onAbout(self, event):
		About = wx.MessageDialog(self, "bleh", "About", wx.OK)
		About.ShowModal()
		About.Destroy()

	def onExit(self, event):
		self.Close(True)


class program(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "MainWindow")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = program(0)
app.MainLoop()[/PHP]

---

