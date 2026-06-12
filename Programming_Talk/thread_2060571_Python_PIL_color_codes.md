---
title: "Python PIL color codes?"
date: 2012-09-20
forum: Programming Talk
---

### Post by conradin on 2012-09-20
HI all, 
I have a Python Image Language example Im trying to work with. I understand what its doing but I don't know the colour scheme its referencing. The Current target is red pixels (specified as 220) out of an image. The Image I am trying to use is green. I don't know how to change the code to get green pixels out. 

Any one have any ideas?
```

#!/usr/bin/python
from PIL import Image

im = Image.open("someimage.png")
im = im.convert("P")
im2 = Image.new("P",im.size,255)

im = im.convert("P")

temp = {}

for x in range(im.size[1]):
  for y in range(im.size[0]):
    pix = im.getpixel((y,x))
    temp[pix] = pix
    if pix == 220 or pix == 227: # these are the numbers to get red out
      im2.putpixel((y,x),0)

im2.save("output.png")

```

---

### Post by Lux Perpetua on 2012-09-20
> **conradin said:**
> HI all, 
I have a Python Image Language example Im trying to work with. I understand what its doing but I don't know the colour scheme its referencing. The Current target is red pixels (specified as 220) out of an image. The Image I am trying to use is green. I don't know how to change the code to get green pixels out. 

Any one have any ideas?
Here's a hack, which I lifted [from the PIL handbook](http://www.pythonware.com/library/pil/handbook/imagepalette.htm), to get the palette for a palette image:
```
def get_PIL_palette(image):
    tmp = image.resize((256,1))
    tmp.putdata(xrange(256))
    return tmp.convert("RGBA").getdata()

```By looking at the palette, you can determine which indices you want. You could also try a programmatic solution by comparing the palette colors to (0,255,0) or something. For that matter, you could also just compare the colors in the original image (without converting to palette mode) to the color you want to pick out. 

Also, small correction: PIL stands for "Python Imaging Library," not "Python Imaging Language."

---

