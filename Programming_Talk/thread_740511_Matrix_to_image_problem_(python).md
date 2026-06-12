---
title: "Matrix to image problem (python)"
date: 2008-03-30
forum: Programming Talk
---

### Post by bigdidz on 2008-03-30
I am having a issu now.  I'm programming in python and my results are huge matrices.  My matrices are about 1000 X 1000 and the values are reels in [-2,2].

I would like to have a picture of my matrices.  I'd like to produce an image from each matrix that each pixel would be in bijection with a color.  For example, [-2, 0] would be from dark blue to white and [0 , 2] from white to yellow.   I know all my matrices will be the same size ( n * n ).

Afther, if possible, I would like to make a movie from all my pictures.  Like a scrab-book cartoon.  Probably there is already tonnes of (open) programmes that do that.  Just tell me if you know them.

I know Java and Python.  Presently, my program is in Python and I like it that way.  If possible, I'd like to do it all in Python.  actully, I am not a "hardcore programmer".  I'm better in mathematics.:lolflag:  

Thanks to help me

---

### Post by CptPicard on 2008-03-30
Check this out, I think it does what you need:

[http://matplotlib.sourceforge.net/](http://matplotlib.sourceforge.net/)

(There's an ubuntu package in the repos)

---

### Post by bigdidz on 2008-03-30
I'm looking at it.

---

### Post by bigdidz on 2008-03-30
The only function that would maybe help me is "matshow".  But I did not succed to test the example.  This is what I wrote...

```

from matplotlib import *

def samplemat(dims):
    aa = zeros(dims)
    for i in range(min(dims)):
        aa[i,i] = i
    return aa
 
dimlist = [(12,12),(128,64),(64,512),(2048,256)]
 
for d in dimlist:
    im = matshow(samplemat(d))
show()
```

what am I doing wrong

---

### Post by bigdidz on 2008-03-30
Precision; I did it with "maple" and this is what I got.  I is exactly what I want.  Just to have better control on it.

[ATTACH]64382[/ATTACH]

---

### Post by pmasiar on 2008-03-30
**pprint** module is for prettyprinting stuff - if that is what you want :-) **numpy** is module for numerical processing.

---

### Post by WW on 2008-03-31
You can use the [Python Imaging Library](http://www.pythonware.com/products/pil/).  For example, this code creates a 200x200 image and saves it as a PNG file:
```

import Image

size = (200,200)
im = Image.new('RGB',size)
pix = im.load()
for i in range(size[0]):
    for j in range(size[1]):
        pix[i,j] = (i,j/2,j)  # Assign (R,G,B) values to the pixels
im.save('image.png')

```
The image that it creates is attached.

Instead of the example that I used for the (R,G,B) values of the pixels, you could create a function, say rgbvalue(f), that converts the floating point number f to an (R,G,B) tuple.

Edit: The Ubuntu package is [python-imaging](http://packages.ubuntu.com/gutsy/python-imaging).

---

### Post by bigdidz on 2008-03-31
Thanks a lot. I'll use the Python Image library.  I'll take the complete control of what i'm doing.

Thanks again folks for your help

---

