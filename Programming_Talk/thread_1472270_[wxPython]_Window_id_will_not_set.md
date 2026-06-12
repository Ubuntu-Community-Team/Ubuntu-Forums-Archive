---
title: "[wxPython] Window id will not set"
date: 2010-05-04
forum: Programming Talk
---

### Post by dodle on 2010-05-04
When I create an instance of a wx.Frame, I set the id to [color=red]-1[/color], but when I try to retrieve that id, it comes back as [color=red]-201[/color].

[php]class App(wx.App):
	def OnInit(self):
		frame = wx.Frame(None, -1, "Blah")  # Set id to "-1"
		print frame.GetId()  # Id prints as "-201"
		frame.Show()
		self.SetTopWindow(frame)
		return True

app = App(0)
app.MainLoop()[/php]Can someone tell me why this is happening?  If I want to set the frame's id, I have to do:```
frame.SetId(-1)
```Then it prints correctly.  But shouldn't that id be set at construction?

---

### Post by robots.jpg on 2010-05-04
-1 is the value of wx.ID_ANY, the "generate a unique ID for me" constant.

---

### Post by dodle on 2010-05-04
Ok, thanks.  I didn't realize that.  But now I have a different issue:  I've created a wx.Frame with a method to print an event object's id.  But once again, after calling the method, the id prints out as [color=red]-201[/color].[php]import wx


class MainWindow(wx.Frame):
	def __init__(self, parent, id=wx.ID_ANY, title=""):
		wx.Frame.__init__(self, parent)
		
		print id # Id prints out correctly here "100"
		
		# Call event handler with wx.Frame as event object
		wx.EVT_WINDOW_CREATE(self, self.PrintId)
		
	
	def PrintId(self, event):
		# Print the Id
		print event.GetEventObject().GetId() # Id prints out as -201
		event.Skip()

class App(wx.App):
	def OnInit(self):
		frame = MainWindow(None, 100, "Blah")
		frame.Show()
		self.SetTopWindow(frame)
		return True

app = App(0)
app.MainLoop()[/php]But I can't see why it wouldn't print out [color=red]100[/color].  Doesn't this call the method with the wx.Frame as the event object[php]wx.EVT_WINDOW_CREATE(self, self.PrintId)[/php]

---

### Post by robots.jpg on 2010-05-04
> **dodle said:**
> But I can't see why it wouldn't print out [COLOR=red]100[/COLOR].  Doesn't this call the method with the wx.Frame as the event object[php]wx.EVT_WINDOW_CREATE(self, self.PrintId)[/php]

It does, but you aren't passing the id from MainWindow.__init__ to wx.Frame.__init__.

---

### Post by dodle on 2010-05-04
Ok, I see.  Thanks, Robots.
[php]wx.Frame.__init__(self, parent, id)[/php]

---

