---
title: "window/application to the top/front, wxPython"
date: 2009-06-12
forum: Programming Talk
---

### Post by tereshkosg on 2009-06-12
Hi,

I am writing a small application that sits in the tray and pops out from time to time with some information.

I am writing it using wxWdigets and python.

Unfortunately, I am pretty much stuck at something that in windows is pretty trivial (SetForegroundWindow) but is not so under GTK and wxWidgets.

my main window is wx.Frame type .. i tried to do frame.Raise() but it does not affect the desktop window order in any way.

changing the window style to wx.STAY_ON_TOP is not a solution as I do not need it constantly at the top.

I read some forums and it seems like gtk has got a function present() ... but i have not clue how to access if from wxPython .. 

Please, help!!!

---

