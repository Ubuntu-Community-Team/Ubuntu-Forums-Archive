---
title: "Obtaining Local Widgit Name In Event Handler"
date: 2009-04-21
forum: Programming Talk
---

### Post by cmnorton on 2009-04-21
I have a local wx.TextCtrl in my frame. When a button is pushed, I'd like to grab the "handle" of the wx.TextCtrl object, so I can set some text in the wx.TextCtrl. 

What is the best way for an event handler to grab the wx.TextCtrl's "handle"?

Edit:

I want to call FindWindowByName, but finding where to initialize this is my next hurdle.

Edit 2:

    def OnButton1Button(self, event):
        self.FindWindowByName("textCtrl1").SetValue("Button pushed")

---

