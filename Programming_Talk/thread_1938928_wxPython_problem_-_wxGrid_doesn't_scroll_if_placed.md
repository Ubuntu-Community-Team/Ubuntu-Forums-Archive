---
title: "wxPython problem - wxGrid doesn't scroll if placed in wxGridBagSizer"
date: 2012-03-10
forum: Programming Talk
---

### Post by smartbei on 2012-03-10
Hi,
I have been trying to work with wxWidgets on a project, and have run into an annoying problem. I have an application that is mostly a Grid with buttons around it that manipulate and read the grid data. The problem I am facing is that the grid does not show its scrollbar as it should when I place it into a wxGridBagSizer (which I am using to layout the window).

Here is minimal code that appears to exhibit the same problem:
```

#!/usr/bin/env python
import wx
import wx.grid
class gridframe(wx.Frame):
    def __init__(self, *args, **kwargs):
        """Initialize, and let the user set any Frame settings"""
        wx.Frame.__init__(self, *args, **kwargs)
        self.create_controls()
    
    def create_controls(self):
        self.SetSize((300,300))
        
        self.g_sizer = wx.GridBagSizer(hgap=15, vgap=15)
        
        self.grid = wx.grid.Grid(self)
        self.grid.CreateGrid(20,40)
        self.g_sizer.Add(self.grid, pos=(0,0))
        
        self.SetSizer(self.g_sizer)
        

class wxHelloApp(wx.App):
	"""The wx.App for the wxHello application"""

	def OnInit(self):
		"""Override OnInit to create our Frame"""
		frame = gridframe(None, title="Assembly File Manager")
		frame.Show()
		self.SetTopWindow(frame)

		return True

if __name__ == "__main__":
	app = wxHelloApp()
	app.MainLoop()

```

Many thanks!

---

### Post by llanitedave on 2012-03-10
I don't know the answer to that,  but I'm building an application now that will be using wxGrid extensively too, so I hope it's not too serious.  I was using wx.GridSizer and had so much trouble that I gave up and just used nested box sizers, which have so far worked for me.

---

