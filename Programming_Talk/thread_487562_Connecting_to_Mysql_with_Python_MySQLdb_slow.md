---
title: "Connecting to Mysql with Python MySQLdb slow"
date: 2007-06-29
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2007-06-29
Hey guys

can anyone give me some advice on speeding up queries in my Python program that sends a SQL query across my ethernet network to a remote server in another room.

The query only returns three records atm but still takes about 10 seconds to return the results. This isn't the kind of performance I was expecting and I was wondering if there are any tips you can give me to make it work as fast as it can?

Thanks In Advance!

Mike

---

### Post by OlleEriksson on 2007-06-29
Do you experience the same problems with other frontends? It's not impossible that something's wrong with the database.

---

### Post by Mickeysofine1972 on 2007-06-29
> **OlleEriksson said:**
> Do you experience the same problems with other frontends? It's not impossible that something's wrong with the database.

Well i havent really tried any other front ends tba. I wrote this Python script to demonstrate how you can use the same script in linux, windows and mac, and it does just that.

The database is just a standard install of Mysql for ubuntu 7.04 and only has a very small table in it with three records in it.

It takes about ten seconds to retrieve those three records when it runs on either windowz or llinux, (i havent got a mac to test it on)

here's my python program to look at:
```

import wx
import MySQLdb

ID_ABOUT = 101
ID_EXIT = 110
ID_LOGIN = 111

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, wx.ID_ANY, title, size = (400, 200), 
								style = wx.DEFAULT_FRAME_STYLE | wx.NO_FULL_REPAINT_ON_RESIZE )
		self.control = wx.TextCtrl( self, 1, style = wx.TE_MULTILINE )
		self.CreateStatusBar()
		filemenu = wx.Menu()
		filemenu.Append(ID_LOGIN, "L&ogin", "Login to the Mysql DB")
		filemenu.AppendSeparator()
		filemenu.Append(ID_ABOUT, "&About", "About this program")
		filemenu.AppendSeparator()
		filemenu.Append(ID_EXIT, "E&xit", "Exit this program")
		menubar = wx.MenuBar()
		menubar.Append(filemenu, "F&ile")
		# link up events to menu selections
		wx.EVT_MENU(self, ID_LOGIN, self.OnLogin)
		wx.EVT_MENU(self, ID_ABOUT, self.OnAbout)
		wx.EVT_MENU(self, ID_EXIT, self.OnExit)
		self.SetMenuBar(menubar)
		self.Show(True)
		
	def OnAbout(self, event):
		d = wx.MessageDialog(self, "A simple Database Connector", "About DB Connector", wx.OK)
		d.ShowModal()
		d.Destroy()
		
	def OnExit(self, event):
		self.Close(True)
		
	def OnLogin(self, event):
		# logiin to a mysql db
		db = MySQLdb.connect(host='10.10.3.179', user='myUID', passwd='MyPWD',db='MyDBName')
		cursor = db.cursor()
		cursor.execute('SELECT * FROM tblUsers')
		result = cursor.fetchall()
		for record in result:
			self.control.AppendText(record[1])
			self.control.AppendText(" ")
			self.control.AppendText(record[2])
			self.control.AppendText("\n")
			
		
app = wx.PySimpleApp()
frame = MainWindow(None, -1, "Network Database Test")
app.MainLoop()

```


Mike

---

### Post by jurkki on 2007-06-29
it's definately not python.
here's the code for this test:
```

#!/usr/bin/env python

import MySQLdb

db = MySQLdb.connect(host='192.168.1.1',user='testuser',passwd='testuser',db='amarok')
cursor=db.cursor()
cursor.execute('SELECT * FROM related_artists')
results=cursor.fetchall()
print len(result)

```

```

jurkki@buildikone:~$ time python test.py
10004

real    0m0.242s
user    0m0.056s
sys     0m0.120s
jurkki@buildikone:~$

```

dunno how to help you with your problem tho :|

---

### Post by steve.horsley on 2007-06-29
I wonder if it's a problem connecting, or something to do with the GUI. Try this code and look-see where the problem lies:
```

#!/usr/bin/env python

import MySQLdb

print "Connecting..."
db = MySQLdb.connect(host='10.10.3.179',user='myUID',passwd='myPWD',db='MyDBName')
cursor=db.cursor()
print "Running query..."
cursor.execute('SELECT * FROM related_artists')
results=cursor.fetchall()
print "results =", results


```

---

### Post by jrocnuck on 2011-05-04
While this thread is quite old, I wanted to point out something that people may over look that can sometimes cause issues.

On the database host pc make sure there are no DNS resolving issues that could cause problems.

In my case, I had a server (redhat) with a bogus nameserver entry in /etc/resolve.conf that was causing connections to be very slow.

After removing the bad entries, the thing is fast as expected.

---

