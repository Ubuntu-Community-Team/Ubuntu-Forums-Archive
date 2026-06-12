---
title: "Python Image module - PixelAccess object"
date: 2010-04-04
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-04-04
I am new to python and to the Image module.  I want to get some pixel info from one jpg file and then use that info to create another jpg file.  Looking at the module documentation it seemed like using a PixelAccess object might be a good way to do this.  ex/
```

cave = Image.open("cave.jpg")
cave_pix = cave.load()

```

I think that I have manipulated the data correctly, but I have a problem.  I cant seem to find a way to save / display the adjusted PixelAccess object.  Please help this noob get to the next level of python programming ;)

---

### Post by diesch on 2010-04-05
Here's something I did a some time ago, maybe it helps you:

```
#!/usr/bin/env python

import Image

im = Image.open("test.png")

print im.info, im.mode

out = Image.new('I', im.size, 0xffffff)

width, height = im.size
for x in range(width):
    for y in range(height):
        r,g,b = im.getpixel((x,y))
        if g > 1.2*r and g > 1.2*b:
                print x,y, (r,g,b)
                out.putpixel((x,y), 0)

out.save('output.png')

```

---

### Post by WillFerrellLuva on 2010-04-05
ty for the info

---

