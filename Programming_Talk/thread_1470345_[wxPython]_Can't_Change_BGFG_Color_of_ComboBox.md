---
title: "[wxPython] Can't Change BG/FG Color of ComboBox"
date: 2010-05-02
forum: Programming Talk
---

### Post by dodle on 2010-05-02
[color=#0000BF]wx.ComboBox[/color] is derived from [color=#0000BF]wx.Window[/color], which has the [color=#FF0000]SetBackgroundColour()[/color] and [color=#FF0000]SetForegroundColour()[/color] methods.  But neither work for [color=#0000BF]wx.ComboBox[/color].  Is there a workaround?  I've already checked if ComboBox uses a TextCtrl as a child, but it doesn't.

---

### Post by robots.jpg on 2010-05-03
Just to be clear, SetBackgroundColour is returning True but the color doesn't change for you, right?  The way foreground and background colors are handled for each control is platform-dependent.  If you tried the same code on a Windows system, it would probably work.

If you're using a read-only ComboBox and you only care about how it looks under Ubuntu, you could try wx.Choice instead.  It should let you change the foreground and background color.  I don't know of any direct workaround, though.

---

### Post by dodle on 2010-05-03
Yes, you are right.  People have been telling me that it works under windows.  I got around it by using a [ComboCtrl](http://www.wxpython.org/docs/api/wx.combo.ComboCtrl-class.html) instead, and setting the bg color of its child TextCtrl.

---

