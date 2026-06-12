---
title: "[wxPython] How to make alternating ProgressDialog"
date: 2010-04-27
forum: Programming Talk
---

### Post by dodle on 2010-04-27
So I've learned how to make a progress dialog that shows how far along a process is:
[php]import wx

# Make a list of names to display
names = ("Alex", "Dan", "Alice", "Tod", "Jan")

class Progress(wx.ProgressDialog):
	def __init__(self):
		wx.ProgressDialog.__init__(self, "Names", "Progress", len(names), None)

		count = 0
		for name in names:
			wx.Sleep(1)  # Give time to view name
			self.Update(count, name)  # Update progress bar and display name
			count += 1

app = wx.App()
dia = Progress()
dia.Destroy()
app.MainLoop()[/php]

But what about a dialog that doesn't show progress, it just shows a bar alternating direction left and right?  wx.ProgressDialog has the methods [color=red]Pulse()[/color] and [color=red]UpdatePulse()[/color], but when I try to use them an error comes back saying:```
AttributeError: 'Progress' object has no attribute 'UpdatePulse'
```

Does anyone know how to create this type of progress dialog?

**Edit:** The same thing happens when trying to use [color=red]wx.Gauge.Pulse()[/color]:
```
AttributeError: 'Gauge' object has no attribute 'Pulse'
```

---

### Post by dodle on 2010-04-29
Fixed!  The problem was with my python-wxgtk installation.  I re-installed python-wxgtk2.8 (and un-installed python-wxgtk2.6) and now the Pulse() method works.

**Edit:** But [color=red]EVT_MAXIMIZE[/color] still doesn't work for me: [http://ubuntuforums.org/showthread.php?t=1465064](http://ubuntuforums.org/showthread.php?t=1465064)

---

