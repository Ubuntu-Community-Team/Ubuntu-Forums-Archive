---
title: "PIL convert 16bit grayscale to 8 bit"
date: 2010-05-14
forum: Programming Talk
---

### Post by lavinog on 2010-05-14
I made a utility that works with some scanned images.  Everything was working until I started scanning grayscale images.

It seems that the only issue is that the images cannot be displayed in the gui if they are 16bit, but it looks like the manipulations work fine.  So as a fix I wanted to convert the image that is displayed in the gui to 8 bit, but I have not been successful with this. Any ideas?

```

#! /usr/bin/env python

import Image
import sys
filename = sys.argv[1]

im = Image.open(filename)
print im.size
print im.mode
im2 = im.convert('L')  # this doesn't do what I was wanting
print im2.mode

im2.show()

```

```
python imgtest.py grayscale_example.png 
(85, 63)
I
L

```
Edit:  Attached is an example image
Edit2: realized convert creates a new object instead of replacing existing, but it still doesn't convert the pixel data to be visible.  The displayed image is solid white.

---

### Post by lavinog on 2010-05-14
Ok, I figured it out:
```

#! /usr/bin/env python

import Image
import sys

filename = sys.argv[1]

im = Image.open(filename)
print im.size
print im.mode

table=[ i/256 for i in range(65536) ]

im2 = im.point(table,'L')

print im2.mode

im2.show()

```

---

