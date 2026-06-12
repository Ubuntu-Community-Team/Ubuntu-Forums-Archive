---
title: "PIL &quot;blend&quot; of transparent cornered mask onto image not working?"
date: 2009-06-20
forum: Programming Talk
---

### Post by kaivalagi on 2009-06-20
Hi All,

I have a bit of an issue using PIL (python image library) when trying to Image.blend a mask (solid colour image with transparent corners) onto an existing image. It seems that the result applies the transparencies in the corners loosing the original image content. I want the original image content left intact, as it was before the blend.

I've attached the 2 images I am blending and the resultant output. "img.jpg" is the main image, "mask.png" is the mask img. The mask is actually rendered in code using ImageDraw arc functions etc, but to demonstrate I saved a png from it in code and am using the resultant file here.

The simple code to generate the output looks like this:

```
from PIL import Image

mask = Image.open("/tmp/mask.png")
img = Image.open("/tmp/img.jpg")
img = img.convert("RGBA") #convert to same mode as mask for blend...
#mask = mask.convert("RGB") #convert to same mode as img for blend...

print "\npre blend:"
print "img.mode:"+img.mode
print "mask.mode:"+mask.mode

# apply mask to background image
img = Image.blend(img, mask, 0.5)

print "\npost blend:"
print "img.mode:"+img.mode
print "mask.mode:"+mask.mode

img.save("/tmp/output.png")
```

I have tried converting the png to RGB and the jpg to RGBA for the blend, either way I get the same result.

Any one got any ideas on how to achieve the result I am after? I need the mask to apply on all the image bar the corner pieces...

Any alternative suggestions on how to do this in code are welcome too, maybe I have chosen the wrong method? Does PIL just not handle overlaying transparencies onto an image? If I paste on top I lose the image behind even if the top image has some opacity.

Thanks,
K

---

