---
title: "[wxPython] Can't load menu icons"
date: 2010-04-06
forum: Programming Talk
---

### Post by dodle on 2010-04-06
I've tried following [[color=blue]this tutorial[/color]](http://wiki.wxpython.org/AnotherTutorial#wx.MenuBar) to create icons for menus.  But when I start the program I get this error: > Can't load image from file 'stock_exit-16.png': file does not exist.I can't find any other tutorials on how to access the stock icons for Gtk+ with wxPython.  Does anyone have any advice or know of a good tutorial?

---

### Post by sharpdust on 2010-04-06
I really doubt that that image is part of the wxPython library. I imagine that when they say the word 'stock' they are referring to a generic image for a stop icon, not something specific to wxPython. You should try loading an image that you know exists.

---

### Post by dodle on 2010-04-06
For some reason it's not working when I point to a specific image.  The error doesn't pop up, but there is still no icon in the menu.  Does the image need to be a specific resolution?

**Edit:** Okay, menu icons were disabled on my system.  But I still have to point to an absolute filename ("/usr/share/icons/Human/16x16/stock/generic/stock_exit.png") to get it to work in my program.  Is there a set of default icons for wxPython or Gtk?

---

