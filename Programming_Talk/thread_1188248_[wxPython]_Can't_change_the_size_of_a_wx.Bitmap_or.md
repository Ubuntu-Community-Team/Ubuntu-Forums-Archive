---
title: "[wxPython] Can't change the size of a wx.Bitmap or wx.StaticBitmap"
date: 2009-06-15
forum: Programming Talk
---

### Post by dodle on 2009-06-15
No matter what I try, the bitmap is displayed in its original dimensions.

[php]image = wx.Bitmap("im.png")
mypic = wx.StaticBitmap(self, -1, image, wx.DefaultPosition, (50,50), wx.BITMAP_TYPE_PNG)[/php]
[php]image = wx.Bitmap("im.png")
mypic = wx.StaticBitmap(self, -1, image, wx.DefaultPosition, style=wx.BITMAP_TYPE_PNG)
mypic.SetSize((50,50))[/php]
[php]image = wx.Bitmap("im.png")
image.SetSize((50,50))
mypic = wx.StaticBitmap(self, -1, image, wx.DefaultPosition, style=wx.BITMAP_TYPE_PNG)[/php]

How can I change the dimensions of a displayed bitmap?

---

### Post by dodle on 2009-06-15
I learned that I first needed to load the image as a wx.Image instead of wx.Bitmap.  Then use the Rescale() module to size and convert it to a wx.Bitmap with BitmapFromImage().

[php]
start_image = wx.Image("im.png")
start_image.Rescale(50, 50)
image = wx.BitmapFromImage(start_image)
mypic = wx.StaticBitmap(self, -1, image, wx.DefaultPosition, style=wx.BITMAP_TYPE_PNG)[/php]

---

