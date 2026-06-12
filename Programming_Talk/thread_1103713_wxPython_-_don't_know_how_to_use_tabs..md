---
title: "wxPython - don't know how to use tabs."
date: 2009-03-23
forum: Programming Talk
---

### Post by dodle on 2009-03-23
I've been looking all around for information on how to create tabs with wxPython, but I haven't found anything.  I've found tab.h in the wx include folder but don't know how to use it.  

I've created a program with options to choose from on the main panel.  But I would like to divide those options up into two or three tabs.  Does anyone know how to do this?

---

### Post by cybergalvez on 2009-03-23
What you want is the notebook control.  Download the wxpython demo.  Here is a copy of the demo code from their site
```


import  sys

import  wx

import  ColorPanel
import  GridSimple
import  ListCtrl
import  ScrolledWindow
import  images

#----------------------------------------------------------------------------

class TestNB(wx.Notebook):
    def __init__(self, parent, id, log):
        wx.Notebook.__init__(self, parent, id, size=(21,21), style=
                             wx.BK_DEFAULT
                             #wx.BK_TOP 
                             #wx.BK_BOTTOM
                             #wx.BK_LEFT
                             #wx.BK_RIGHT
                             # | wx.NB_MULTILINE
                             )
        self.log = log

        win = self.makeColorPanel(wx.BLUE)
        self.AddPage(win, "Blue")
        st = wx.StaticText(win.win, -1,
                          "You can put nearly any type of window here,\n"
                          "and if the platform supports it then the\n"
                          "tabs can be on any side of the notebook.",
                          (10, 10))

        st.SetForegroundColour(wx.WHITE)
        st.SetBackgroundColour(wx.BLUE)

        # Show how to put an image on one of the notebook tabs,
        # first make the image list:
        il = wx.ImageList(16, 16)
        idx1 = il.Add(images.getSmilesBitmap())
        self.AssignImageList(il)

        # now put an image on the first tab we just created:
        self.SetPageImage(0, idx1)


        win = self.makeColorPanel(wx.RED)
        self.AddPage(win, "Red")

        win = ScrolledWindow.MyCanvas(self)
        self.AddPage(win, 'ScrolledWindow')

        win = self.makeColorPanel(wx.GREEN)
        self.AddPage(win, "Green")

        win = GridSimple.SimpleGrid(self, log)
        self.AddPage(win, "Grid")

        win = ListCtrl.TestListCtrlPanel(self, log)
        self.AddPage(win, 'List')

        win = self.makeColorPanel(wx.CYAN)
        self.AddPage(win, "Cyan")

        win = self.makeColorPanel(wx.NamedColour('Midnight Blue'))
        self.AddPage(win, "Midnight Blue")

        win = self.makeColorPanel(wx.NamedColour('Indian Red'))
        self.AddPage(win, "Indian Red")

        self.Bind(wx.EVT_NOTEBOOK_PAGE_CHANGED, self.OnPageChanged)
        self.Bind(wx.EVT_NOTEBOOK_PAGE_CHANGING, self.OnPageChanging)


    def makeColorPanel(self, color):
        p = wx.Panel(self, -1)
        win = ColorPanel.ColoredPanel(p, color)
        p.win = win
        def OnCPSize(evt, win=win):
            win.SetPosition((0,0))
            win.SetSize(evt.GetSize())
        p.Bind(wx.EVT_SIZE, OnCPSize)
        return p


    def OnPageChanged(self, event):
        old = event.GetOldSelection()
        new = event.GetSelection()
        sel = self.GetSelection()
        self.log.write('OnPageChanged,  old:%d, new:%d, sel:%d\n' % (old, new, sel))
        event.Skip()

    def OnPageChanging(self, event):
        old = event.GetOldSelection()
        new = event.GetSelection()
        sel = self.GetSelection()
        self.log.write('OnPageChanging, old:%d, new:%d, sel:%d\n' % (old, new, sel))
        event.Skip()

#----------------------------------------------------------------------------

def runTest(frame, nb, log):
    testWin = TestNB(nb, -1, log)
    return testWin

#----------------------------------------------------------------------------


overview = """\
<html><body>
<h2>wx.Notebook</h2>
<p>
This class represents a notebook control, which manages multiple
windows with associated tabs.
<p>
To use the class, create a wx.Notebook object and call AddPage or
InsertPage, passing a window to be used as the page. Do not explicitly
delete the window for a page that is currently managed by wx.Notebook.

"""


if __name__ == '__main__':
    import sys,os
    import run
    run.main(['', os.path.basename(sys.argv[0])] + sys.argv[1:])







```

---

### Post by dodle on 2009-03-23
Thanks, that is helping me out, although I couldn't get the demo to run.  I've found some useful information on wx.Notebook and have successfully implemented tabs.  But now the "Start Server" button is messed up, it has taken over the whole tab.  [PHP]#! /usr/bin/env python

# wx11vnc 0.2
# A graphical tool to set up a vnc server with x11vnc.

import wx
import os
import socket
import commands
from urllib2 import urlopen

ID_About = 100
ID_Exit = 101

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title, (300,200), (300,400),
						wx.DEFAULT_FRAME_STYLE & ~(wx.RESIZE_BORDER | wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
		
		self.CreateStatusBar()
		#self.SetStatusText("VNC Server")
		output = commands.getoutput('ps -A')
		if "x11vnc" in output:
			self.SetStatusText("Server Status: Running")
		else:
			self.SetStatusText("Server Status: Stopped")
		
		menuFile = wx.Menu()
		menuFile.Append(ID_Exit, "E&xit")
		
		menuHelp = wx.Menu()
		menuHelp.Append(ID_About, "&About")
		
		menu_bar = wx.MenuBar()
		menu_bar.Append(menuFile, "&File")
		menu_bar.Append(menuHelp, "&Help")
		self.SetMenuBar(menu_bar)
		
		wx.EVT_MENU(self, ID_About, self.onAbout)
		wx.EVT_MENU(self, ID_Exit, self.onExit)
		
		self.tabbed = wx.Notebook(self, -1, style=(wx.NB_TOP))
		self.panel1 = wx.NotebookPage(self.tabbed, -1)
		self.panel2 = wx.NotebookPage(self.tabbed, -1)
		self.tabbed.AddPage(self.panel1, "Tab1")
		self.tabbed.AddPage(self.panel2, "Tab2")
		
		startB = wx.Button(self.panel1, -1, "Start Server", (140,250),(100,30))
		stopB = wx.Button(self.panel1, -1, "Stop Server", (5,250),(100,30))
		
		# Button stays pressed, can't stop server
		startB.Bind(wx.EVT_BUTTON, self.startServer)
		stopB.Bind(wx.EVT_BUTTON, self.stopServer)
		
		wx.StaticText(self.panel1, -1, "External IP Address", (20,20))
		wx.StaticText(self.panel1, -1, "Local IP Address", (20,80))
		wx.StaticText(self.panel1, -1, "Password", (20,140))
		
		# Retrieve external and local ip address for reference
		userHostname = socket.gethostname()
		getIP = urlopen("http://www.whatismyip.com/automation/n09230945.asp")
		userIP = getIP.read()
		s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
		s.connect(("ubuntu.com",80))
		localIP = s.getsockname()[0]
		
		# Displays ip address
		self.IN1 = wx.TextCtrl(self.panel1, -1, userIP,(20,40), (200,30), wx.TE_READONLY)
		self.IN2 = wx.TextCtrl(self.panel1, -1, localIP,(20,100), (200,30), wx.TE_READONLY)
		# Sets password for remote connection
		self.IN3 = wx.TextCtrl(self.panel1, -1, "",(20,160), (200,30))
		self.IN3.SetMaxLength(8)
		
		wx.StaticText(self.panel1, -1, "Scale", (108,204))
		sizes = ['2', '1', '3/4', '1/2', '1/4']
		self.SC1 = wx.ComboBox(self.panel1, -1, pos=wx.Point(154,200), size=wx.Size(65,25),
								value=sizes[1], choices=sizes, style=wx.CB_DROPDOWN | wx.CB_READONLY)
		
	def onAbout(self, event):
		About = wx.MessageDialog(self, "\
wx11vnc 0.2\n\nA graphical utility to help set\n\
up a vnc server with x11vnc\n\n\
License: GPL", "About wx11vnc", wx.OK | wx.ICON_INFORMATION)
		About.ShowModal()
		About.Destroy()
	
	def onExit(self, event):
		self.Close(True)
	
	def startServer(self, event):
		output = commands.getoutput('ps -A')
		if "x11vnc" in output:
			self.SetStatusText("Server is already running")
		else:
			vncpass = str(self.IN3.GetValue())
			vncscale = self.SC1.GetValue()
			if vncpass == "":
				self.SetStatusText("Need To Set Password")
			else:
				os.system("x11vnc -bg -forever -scale %s -passwd %s" % (vncscale, vncpass))
				self.IN3.Clear()
				output = commands.getoutput('ps -A')
				if "x11vnc" in output:
				    self.SetStatusText("Server Status: Started")
				else:
					self.SetStatusText("Error: Check Password")
		
	def stopServer(self, event):
		os.system("killall x11vnc")
		output = commands.getoutput("ps -A")
		if "x11vnc" in output:
			self.SetStatusText("Error: Server did not stop")
		else:
			self.SetStatusText("Server Status: Stopped")


class wx11vnc(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "WX11VNC Server")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = wx11vnc(0)
app.MainLoop()[/PHP]

**Edit:** Fixed!  I changed these two lines:[php]		self.panel1 = wx.NotebookPage(self.tabbed, -1)
		self.panel2 = wx.NotebookPage(self.tabbed, -1)
[/php]to:[php]		self.panel1 = wx.Panel(self.tabbed, -1)
		self.panel2 = wx.Panel(self.tabbed, -1)
[/php]

---

### Post by cybergalvez on 2009-03-23
Great, glad to see you got it working :)

---

