---
title: "[wxPython] Animated Gif - Gdk-CRITICAL Error"
date: 2010-04-27
forum: Programming Talk
---

### Post by dodle on 2010-04-27
Here is a simple dialog that shows an animated gif:
[php]import wx, wx.animate

class AniGif(wx.Dialog):
	def __init__(self, parent, id, title):
		wx.Dialog.__init__(self, parent, id, title)
		
		clock = "clock.gif"
		
		showclock = wx.animate.GIFAnimationCtrl(self, -1, clock)
		showclock.Play()
		


app = wx.App()
dia = AniGif(None, -1, "Ani Gif")
dia.ShowModal()
dia.Destroy()
app.MainLoop()[/php]

It runs fine, but every time I start it this error is displayed:
```
(python:10891): Gdk-CRITICAL **: gdk_draw_drawable: assertion `GDK_IS_DRAWABLE (src)' failed
```

Is there a way to get rid of the error?  Should I worry about it?

---

