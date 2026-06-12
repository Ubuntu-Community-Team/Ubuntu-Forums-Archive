---
title: "Image scaling with wxPython"
date: 2009-06-03
forum: Programming Talk
---

### Post by Volt9000 on 2009-06-03
I must be missing something, because I can't find a simple, effective way of resizing an image in wxPython.

I've already got the image loaded

```

icon = wx.Image("myicon.gif", wx.BITMAP_TYPE_GIF)

```

The file in question is a transparent GIF.

Here are the methods I've tried and their results:
ResampleBicubic - Works nicely but fills in all transparent areas with #FF00FF.
ResampleBox - This makes it look ugly, and also gives it the #FF00FF colour.
Scale, Rescale - Makes the image look ugly.
ShrinkBy - This gives the best results but only accepts integer scaling factors.

I know I could just manually resize the image in Gimp, but I'd like to use this image in several places with several sizes, so I figured (at least previously I did!) that it would be easier to have a single image and resize it as necessary.

---

### Post by ThinkBuntu on 2009-06-03
[http://www.wxpython.org/docs/api/wx.Image-class.html#Rescale](http://www.wxpython.org/docs/api/wx.Image-class.html#Rescale)
[http://www.wxpython.org/docs/api/wx.Image-class.html#Scale](http://www.wxpython.org/docs/api/wx.Image-class.html#Scale)

---

### Post by Volt9000 on 2009-06-03
As I stated in my original post, I already tried these methods and they produced an ugly-looking image.

I realized that a GIF wasn't the best thing to resize because of its limited colour palette so I converted the image to a PNG and set it to RGB colourspace and tried again. No dice-- the image still looks ugly when resized.

---

### Post by ThinkBuntu on 2009-06-03
Sorry, I missed that you mentioned these methods. The docs recommend scaling with wx.IMAGE_QUALITY_HIGH...are you using that, or normal quality?

---

### Post by Volt9000 on 2009-06-03
> **ThinkBuntu said:**
> Sorry, I missed that you mentioned these methods. The docs recommend scaling with wx.IMAGE_QUALITY_HIGH...are you using that, or normal quality?

I tried both. They both produce the same result-- an ugly image.

---

### Post by ThinkBuntu on 2009-06-03
If both attributes result in the same quality image, you probably should file a bug report to the wxPython project...I'm not aware of another way to resize images while retaining quality. I suppose you could ship it out to ImageMagick (or a similar utility) and let that handle the resizing, but it may be slow.

---

