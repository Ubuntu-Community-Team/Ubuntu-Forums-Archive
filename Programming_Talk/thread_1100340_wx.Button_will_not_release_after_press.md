---
title: "wx.Button will not release after press"
date: 2009-03-19
forum: Programming Talk
---

### Post by dodle on 2009-03-19
I am having some trouble with my code.  The button that is used to start the vnc server remains pressed after x11vnc is executed.  The program then freezes and I have to force it to close by killing it's process.  Here is the code:[PHP]#! /usr/bin/env python

# wx11vnc 0.1
# A graphical tool to set up a vnc server with x11vnc.

import wx
import os
import socket
from urllib2 import urlopen

ID_About = 100
ID_Exit = 101

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title, (300,200), (250,300),
						wx.DEFAULT_FRAME_STYLE & ~(wx.RESIZE_BORDER | wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
		
		# Create the status bar
		self.CreateStatusBar()
		self.SetStatusText("VNC Server")
		
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
		
		self.panel1 = wx.Panel(self, -1)
		
		startB = wx.Button(self.panel1, -1, "Start Server", (140,200),(100,30))
		stopB = wx.Button(self.panel1, -1, "Stop Server", (5,200),(100,30))
		
		# Button stays pressed, can't stop server
		startB.Bind(wx.EVT_BUTTON, self.startServer)
		stopB.Bind(wx.EVT_BUTTON, self.stopServer)
		
		# Input boxes
		wx.StaticText(self.panel1, -1, "External IP Address", (20,20))
		wx.StaticText(self.panel1, -1, "Local IP Address", (20,80))
		wx.StaticText(self.panel1, -1, "Password", (20,140))
		
                # Retrieve external and local ip address for reference
		userHostname = socket.gethostname()
		getIP = urlopen("http://www.whatismyip.com/automation/n09230945.asp")
		userIP = getIP.read()
		localIP = "I don't know"
		self.IN1 = wx.TextCtrl(self.panel1, -1, userIP,(20,40), (200,30), wx.TE_READONLY)
		self.IN2 = wx.TextCtrl(self.panel1, -1, localIP,(20,100), (200,30), wx.TE_READONLY)
		self.IN3 = wx.TextCtrl(self.panel1, -1, "",(20,160), (200,30))
		
	def onAbout(self, event):
		pass
	
	def onExit(self, event):
		self.Close(True)
	
	def startServer(self, event):
		vncpass = self.IN3.GetValue()
		os.system("x11vnc -passwd %s" % vncpass)  # ERROR: Program freezes
		self.IN3.Clear()
	
	def stopServer(self, event):
		os.system("killall x11vnc")


class wx11vnc(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "WX11VNC Server")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = wx11vnc(0)
app.MainLoop()[/PHP]For some reason, this problem only occurs with x11vnc.  If I change the following line:[PHP]os.system("x11vnc -passwd %s" vncpass)[/PHP]to:[PHP]os.system("firefox http://homestarrunner.com")[/PHP]or other programs like gedit, it works fine.  Does anyone know what's going on?

**Edit:** It looks like this problem occurs when trying to launch terminal based programs.

---

### Post by krunge on 2009-03-19
> **dodle said:**
> For some reason, this problem only occurs with x11vnc.  If I change the following line:[PHP]os.system("x11vnc -passwd %s" vncpass)[/PHP]to:[PHP]os.system("firefox http://homestarrunner.com")[/PHP]or other programs like gedit, it works fine.  Does anyone know what's going on?

**Edit:** It looks like this problem occurs when trying to launch terminal based programs.

I'm not sure what is going on, but you might want to add the '-bg' option to x11vnc to have it go into the background.  Or put it there yourself with a '&'.

If your scripting language is confused by all of x11vnc's output, perhaps use the -logfile file, or -quiet x11vnc options.

Another thing to try is to launch it in a terminal, e.g.:```

    xterm -iconic -title x11vnc-console -e x11vnc -passwd ...

```
This is also useful for debugging problems.

---

### Post by dodle on 2009-03-19
[PHP]os.system("x11vnc -bg -passwd %s" % vncpass)[/PHP]Thanks.  The background mode is exactly what I needed.

---

