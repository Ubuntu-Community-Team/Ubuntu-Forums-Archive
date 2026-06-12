---
title: "[wxPython] Errors upon closing the app"
date: 2009-05-08
forum: Programming Talk
---

### Post by dodle on 2009-05-08
Whenever I close my program, written in wxPython, the console displays either "segmentation fault" or "Illegal Instruction".  It's not really affecting anything but it would seem more "clean" if the error would go away.  I've written the same application in PyQt4 and no such error is displayed.  Is this normal for wx programs?

---

### Post by c174 on 2009-05-08
> **dodle said:**
> Is this normal for wx programs?

:) Hopefully not, it shouldn't have that error.

I think you must have some kind of memory corruption in your program some where. I'm not familiar with wxPython but in the C++ version it is quite easy to make such mistakes.

Unfortunately errors like that can be hard to find. One idea might be to quit the program as soon as possible, and then include more a more of the functionality until the error suddenly appears. This might give a hint to where the problem is.

---

### Post by dodle on 2009-05-09
> **c174 said:**
> One idea might be to quit the program as soon as possible, and then include more a more of the functionality until the error suddenly appears. This might give a hint to where the problem is.

I open the program and immediately shut it down and get the error.

I created a test window to see what would happen, and there was no error.  This is going to be tough to figure out.
[php]#! /usr/bin/env python

import wx

class MainWindow(wx.Frame):
	def __init__(self, parent, ID, title):
		wx.Frame.__init__(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)
		
class TestApp(wx.App):
	def OnInit(self):
		frame = MainWindow(None, -1, "Segmentation Fault")
		frame.Show(True)
		self.SetTopWindow(frame)
		return True

app = TestApp(0)
app.MainLoop()[/php]

---

### Post by Kilon on 2009-05-09
> **dodle said:**
> I open the program and immediately shut it 

[php]#! /usr/bin/env python

wx.Frame.__init__(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)[/php]

This one is bothering me, it should be

[PHP]wx.Frame(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)[/PHP]

I am new with python, but maybe this might create your problems.

---

### Post by Kilon on 2009-05-09
Actually I was wrong your code run just fine mine is wrong. Weird.

This how I would have done it .

```
import wx

#class MainWindow(wx.Frame):
#    def __init__(self, parent, ID, title):
#        wx.Frame(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)
        
class TestApp(wx.App):
    def OnInit(self):
        frame = wx.Frame(None, -1, "hello")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = TestApp(0)
app.MainLoop()  

```

---

### Post by dodle on 2009-05-09
> **Kilon said:**
> ...it should be

[PHP]wx.Frame(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)[/PHP]

> line 7, in __init__
    wx.Frame(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)
  File "/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wx/_windows.py", line 485, in __init__
    newobj = _windows_.new_Frame(*args, **kwargs)
TypeError: argument number 1: a 'wxWindow *' is expected, 'MainWindow' is received


I'm not sure that is correct.

---

### Post by Kilon on 2009-05-09
> **dodle said:**
> I'm not sure that is correct.


it is not, but see my previous reply.

I am trying to find out why I was wrong.

---

### Post by dodle on 2009-05-09
Sorry, I didn't refresh my browser in time to see your post.

---

### Post by Kilon on 2009-05-09
> **dodle said:**
> Sorry, I didn't refresh my browser in time to see your post.


no problem, still trying to understand why we need to call , the Frame constructor directly. weird your approach is confirmed by the wxPython samples as well.

---

### Post by c174 on 2009-05-09
> **dodle said:**
> I open the program and immediately shut it down and get the error.

I don't know your program, but I guess you add some widgets, callbacks, etc to a main window (and maybe other windows too). Try to comment away all of it, and then reengage things little by little -- e.g. reengage the "first half", if there is no error then reengage the first half of the "second half" that was commented away (kind of binary search). This might be a way to locate the error.

---

### Post by dodle on 2009-05-09
> **c174 said:**
> I don't know your program, but I guess you add some widgets, callbacks, etc to a main window (and maybe other windows too). Try to comment away all of it, and then reengage things little by little -- e.g. reengage the "first half", if there is no error then reengage the first half of the "second half" that was commented away (kind of binary search). This might be a way to locate the error.

Thanks for the advice, I'll definitely do that.

---

