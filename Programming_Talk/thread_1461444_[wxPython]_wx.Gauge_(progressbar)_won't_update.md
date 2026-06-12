---
title: "[wxPython] wx.Gauge (progressbar) won't update"
date: 2010-04-24
forum: Programming Talk
---

### Post by dodle on 2010-04-24
I can't figure out why my gauge isn't updating, it skips from 0 to 100:
[php]import wx, time

class Progress(wx.Frame):
	def __init__(self, parent, id, title):
		wx.Frame.__init__(self, parent, id, title)
		
		
		self.progress = wx.Gauge(self, -1, 100)  #create a progress bar with max 100
		self.button = wx.Button(self, -1, "Go")  #button to start progress
		
		wx.EVT_BUTTON(self.button, -1, self.OnGo)
		
		sizer = wx.BoxSizer(wx.VERTICAL)
		sizer.Add(self.progress, 1, wx.EXPAND)
		sizer.Add(self.button, 1, wx.ALIGN_CENTER|wx.ALL, 5)
		
		self.SetAutoLayout(True)
		self.SetSizerAndFit(sizer)
		self.Layout()
	
	def OnGo(self, event):  # Start the guage
		self.progress.SetValue(0)
		count = 0
		while count < 100:
			count += 1
			self.progress.SetValue(count)  #gauge stays at 0 until iteration is finished???
			print count  #this prints correctly for every iteration
			time.sleep(0.05)  #wait for next iteration

class App(wx.App):
	def OnInit(self):
		frame = Progress(None, -1, "Testing Progress")
		frame.Show()
		self.SetTopWindow(frame)
		return True

app = App(0)
app.MainLoop()[/php]

Am I doing something wrong?  I wrote this from a tutorial, but maybe I didn't follow it right.

---

### Post by smartbei on 2010-04-24
Right after you set the value for the progress bar, stick this line:
```
wx.Yield()
```
As far as I can understand, what this does is allow the application to process the message that is sent to the progress bar (which sets its position), by yielding the control to the event processing loop.

Anyway, it solves the problem.

Enjoy!

---

### Post by dodle on 2010-04-25
Interesting, thank you.

---

