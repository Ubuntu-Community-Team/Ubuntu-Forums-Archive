---
title: "beginning WXPython - nothing in frame"
date: 2012-03-16
forum: Programming Talk
---

### Post by mferarri on 2012-03-16
Hi UbuntuForums,

I'm just beginning to learn python, and I'd thought I'd try out WXpython.i'm learning off youtube, but i cant seem to get anything to appear on the frame. help anyone? btw - i have python 2.6 and python-wxgtk2.6 installed.

```
  1 import wx
  2 class bucky(wx.Frame):
  3     def __int__(self,parent,id):
  4 
  5         wx.Frame.__init__(self,parent,id,'Frame aka Window',size=(100,100))
  6         panel=wx.Panel(self)
  7         button=wx.Button(panel,label="exit",pos=(130,10),size=(60,60))
  8         self.Bind(wx.EVT_BUTTON, self.closebutton, button)
  9         self.Bind(wx.EVT_CLOSE, self.closewindow)
 10 
 11     def closebutton(self,event):
 12         self.Close(True)
 13 
 14     def closewindow (self, event):
 15         self.Destroy()
 16 
 17 if __name__ =='__main__':
 18     app=wx.PySimpleApp()
 19     frame=bucky(parent=None,id=-1)
 20     frame.Show()
 21     app.MainLoop()

```

---

### Post by cgroza on 2012-03-16
You placed your button outside the frame.
Your frame is 100x100 pixels wide, but you placed your button at 130 pixels.
Also make sure you learn about sizers later on because absolute positioning isn't the best way to place widgets. It's better to let sizers take care of positioning the widgets for you according to a layout.

---

### Post by mferarri on 2012-03-16
thanks dude ur cool

---

### Post by llanitedave on 2012-03-17
But to be fair, sizers can be pretty frustrating and non-intuitive, and for me, they don't always work as advertised.  I've been forced to combine a kludge of sizers together with absolute size assignments to get items arrange properly on my project's pages.  Fortunately, my current project is designed for a fixed frame size on a notebook screen.  I'm not real sure how it would fare if all the pages were expandable.

---

### Post by cgroza on 2012-03-17
> **llanitedave said:**
> But to be fair, sizers can be pretty frustrating and non-intuitive, and for me, they don't always work as advertised.  I've been forced to combine a kludge of sizers together with absolute size assignments to get items arrange properly on my project's pages.  Fortunately, my current project is designed for a fixed frame size on a notebook screen.  I'm not real sure how it would fare if all the pages were expandable.
I had problems grasping sizers too. That's why I rarely use a sizer other than wx.BoxSizer.
If you use wxGlade to build the interfaces, dealing with sizers is a lot easier.
Good luck with wxPython. :p

---

### Post by llanitedave on 2012-03-18
Looks like I need to spend some time and learn wxGlade.

---

