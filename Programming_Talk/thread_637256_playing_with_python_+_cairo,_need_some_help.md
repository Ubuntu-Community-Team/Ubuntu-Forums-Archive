---
title: "playing with python + cairo, need some help"
date: 2007-12-10
forum: Programming Talk
---

### Post by deepbluepixel on 2007-12-10
hi, I have been playing around a bit with python the last day or so and decided to try out some cairo stuff while I was at it. after running/modifying  some of the example scripts I decided I wanted to make a reflecting image(ye ye, all the cool kids do it so why cant I). 

here is the example script I used as a little base

```

import math
import cairo

WIDTH, HEIGHT  = 256, 256

surface = cairo.ImageSurface(cairo.FORMAT_ARGB32, WIDTH, HEIGHT)
ctx = cairo.Context(surface)

ctx.scale (WIDTH/1.0, HEIGHT/1.0)

pat = cairo.LinearGradient (0.0, 0.0, 0.0, 1.0)
pat.add_color_stop_rgba (1, 0, 0, 0, 1)
pat.add_color_stop_rgba (0.3, 1, 1, 1, 0)


ctx.rectangle (0,0,1,1)
ctx.set_source (pat)
ctx.fill ()

surface.write_to_png('gradient.png')

```

that gives me a nice transparent gradient, now I wanted to use that on a image plus add a bit of blur to the image(using pli, might be here the problem is but im not sure)

```

import cairo
import Image
import ImageFilter
from array import array 

WIDTH, HEIGHT  = 1920, 1200

im = cairo.ImageSurface.create_from_png("Screenshot.png")

im1 = Image.frombuffer("RGBA",( im.get_width(),im.get_height() ),im.get_data(),"raw","RGBA",0,1)

imwidth = im.get_width()
imheight = im.get_height()

im1 = im1.filter(ImageFilter.BLUR)

imgd = im1.tostring()
a = array('B',imgd)

stride = imwidth * 4
surface = cairo.ImageSurface.create_for_data (a, cairo.FORMAT_ARGB32,
                                              imwidth, imheight, stride)

ctx = cairo.Context(surface)

ctx.scale (WIDTH/1.0, HEIGHT/1.0)

pat = cairo.LinearGradient (0, 0, 0, 1)
pat.add_color_stop_rgba (1, 0, 0, 0, 0)
pat.add_color_stop_rgba (0.3, 1, 1, 1, 1)

ctx.mask (pat)

surface.write_to_png('gradientImage.png')

```

running that and the nice transparent gradient is gone and just paints black instead. 

any help would be appreciated

---

