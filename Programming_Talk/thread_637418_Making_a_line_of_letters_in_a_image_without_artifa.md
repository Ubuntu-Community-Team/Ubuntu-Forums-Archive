---
title: "Making a line of letters in a image without artifacts"
date: 2007-12-10
forum: Programming Talk
---

### Post by tyoc on 2007-12-10
Hi there people, I'm trying to automatize something that a people do at work, we need to output abc...z to an image, in this case a bmp.

There is no problem with the code, but with the output, if you see it at first sight it look OK. But now Zoom in like 800%, you will see some random artifact all around the letters, even printing only 1 has this artifacts.

The question is, how to eliminate all those artifacts, or is there another font lib I can use, for the moment I want precision (I mean no artifacts or blurring between chars, if I need to output 1 at a time and then "concatenate" the chars for get a,b,c,...,z is OK). I accept any suggestion (open to see if I can use what you suguest).

Yes I know by instance, I can take a screenshoot to FF and zoom in at more than 800% and not see even 1 artifact, but I also will retrieve other info about the chars.

if is not possible to eliminate the artifacts, then my only chose will be take the workaround, I will need take the screenshoot to FF or another app that zooming doesn't show those artifacts, and write the part of the program that retrieve some info of the chars for this case, instead as a part of the program of output the image file.



```

#original from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/440588


import random
import Image
import ImageFont
import ImageDraw
import ImageFilter
 
 
def gen_captcha(text, fnt, fnt_sz, file_name, fmt='JPEG'):
    fgcolor = 0x000000
    bgcolor = 0xFFffFF
 
    font = ImageFont.truetype(fnt,fnt_sz)
    dim = font.getsize(text)
 
    im = Image.new('RGB', (dim[0]+5,dim[1]+5), bgcolor)
    d = ImageDraw.Draw(im)
    x, y = im.size
 
    # add the text to the image
    d.text((3,3), text, font=font, fill=fgcolor)
    #im = im.filter(ImageFilter.EDGE_ENHANCE_MORE)
 
    im.save(file_name, format=fmt)
 
if __name__ == '__main__':
    gen_captcha("pycaptcha", '/var/lib/defoma/fontconfig.d/L/LucidaSans.ttf', 25, "test.png")

```Hope you get what I said, and what I don't like and want to achieve.

If you ask, this is not for OCR, only for alleviate a little the stress of a guy :P.

---

### Post by tyoc on 2007-12-11
For you to know...

The "problem" apparently is when saving the image, like I see the default value for save, is a low quality value, you can put the desired quality adding an extra arg to save

```
quality = 100
```
that is what I want, like I see, no artifacts, I will check the result more deep later.

---

### Post by tyoc on 2007-12-11
o yes, I forget my extra question.


Do you know of any good font editor that can output .ttf?

---

### Post by DavidBell on 2007-12-11
You seem to be saving in the default format JPEG (you don't pass an argument for it).

JPEG is 'lossy', it compresses by slightly moving things around. Set you format to BMP, PNG or GIF

DB

---

### Post by tyoc on 2007-12-11
yes, you are right and has to do with the saving, because doing 

```

    pix = im.load()

```And searching for pix[x,y] different than the 2 colores for fore/background, there where only like 4 pixels different, thus the problem was saving, thx for the hint about that default value that havent seen.


I also managed doing a .raw... but deleting that default val is what I wnt from first time.

---

