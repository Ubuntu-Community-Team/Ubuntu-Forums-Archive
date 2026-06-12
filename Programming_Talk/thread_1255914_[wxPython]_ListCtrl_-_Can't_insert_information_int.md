---
title: "[wxPython] ListCtrl - Can't insert information into second column"
date: 2009-09-02
forum: Programming Talk
---

### Post by dodle on 2009-09-02
I've been working at this for a while today, but I can't figure out how to insert a string into the second column of my ListCtrl.  Everything is automatically inserted into the first column:

[php]import wx

class MainWindow(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title)
		
		people = {"Person 1": "Joe", "Person 2": "Steve", "Person 3": "Frank", "Person 4": "Al", "Person 5": "Ted"}
		
		MyList = wx.ListCtrl(self, -1, style=wx.LC_REPORT)
		MyList.InsertColumn(0, "Rank")
		MyList.InsertColumn(1, "Name")
		
		for key in people:
			MyList.InsertStringItem(0, key)
			MyList.InsertStringItem(0, people[key])  # I want this to add to the second column
		

class MyApp(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "List Control")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = MyApp(0)
app.MainLoop()[/php]

---

