---
title: "Python WXCallAfter"
date: 2012-10-09
forum: Programming Talk
---

### Post by Kodeine on 2012-10-09
So I'm trying to add changes to my GUI after first initializing it via the 'app.MainLoop()' command. Once such a line has been carried out it's then stuck in a loop so I can't do anything else. So the GUI has to be ran in another thread. But once the GUI has been brought up how can I make further changes to it?

For instance how can I create an image on the window.[php]def DrawImg(pth,loc): #Procedure to draw given image at given location
    
      img = wx.Image(pth,wx.BITMAP_TYPE_PNG).ConvertToBitmap()
      wx.StaticBitmap(frame,-1,pth,loc)
    
def RunGUI():
      
      app = wx.App()
      frame = wx.Frame(None, -1,'WindowTitle',None,(700,500))
      frame.Show()
      bg = wx.Image("imgs/bg.png",wx.BITMAP_TYPE_PNG).ConvertToBitmap()
      wx.StaticBitmap(frame,-1,bg)
      
      app.MainLoop()
    
thread = threading.Thread(target=RunGUI)
thread.start()
#Do other things here and then eventually...
DrawImg('imgs/Square.png',(40,5))[/php]

It seems I need to use wxCallAfter but can't figure out exactly how to use it.

**I've found the module pygame more up my URL, so to speak, and have marked the thread as solved.

---

### Post by MadCow108 on 2012-10-09
you are correct you need to use CallAfter to modify the gui from another thread.
The usage is just wx.CallAfter(Function, argument1, argument2, ...)
the rest is just make sure the state is available everywhere
e.g.:
```
import wx
def DrawImg(frame, pth, loc): #Procedure to draw given image at given location

      img = wx.Image(pth,wx.BITMAP_TYPE_PNG).ConvertToBitmap()
      wx.StaticBitmap(frame,-1,img, loc)

import threading
url = "img2"
url2 = "img1"

app = wx.App()
frame = wx.Frame(None, -1,'WindowTitle',None,(700,500))
bg = wx.Image(url,wx.BITMAP_TYPE_PNG).ConvertToBitmap()
wx.StaticBitmap(frame,-1,bg)
frame.Show()

thread = threading.Thread(target=app.MainLoop)
thread.start()

import time
time.sleep(2)
wx.CallAfter(DrawImg, frame, url2, (40, 5))
thread.join()
```

---

