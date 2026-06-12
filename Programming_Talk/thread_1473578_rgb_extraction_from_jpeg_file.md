---
title: "rgb extraction from jpeg file"
date: 2010-05-05
forum: Programming Talk
---

### Post by cybo on 2010-05-05
i have a matlab code to convert jpeg file into a text file; the text is in hex representing color of each pixel. the problem is that i don't have matalab. does anybody know if it is possible to do something like this in C, C++ or Java? i would really appreciate any help.

---

### Post by PaulM1985 on 2010-05-05
There are Java classes capable of handling and manipulating images.

Probably best starting by looking at the classes:
ImageIO
BufferedImage

[http://java.sun.com/j2se/1.5.0/docs/api/](http://java.sun.com/j2se/1.5.0/docs/api/)

These should bring in your image and you can use the Color class to get the hex representations for each pixel.

Paul

---

### Post by myrtle1908 on 2010-05-06
I wrote some nasty code a while back which did some image stuff in Java.  It did pixel by pixel comparison of two images to check if they were duplicates.  It was not very efficient however there's probably something in the code which may help you.

[http://ubuntuforums.org/showpost.php?p=5334245&postcount=19](http://ubuntuforums.org/showpost.php?p=5334245&postcount=19)

---

### Post by ssam on 2010-05-06
```
#!/usr/bin/env python
from PIL import Image
import sys

def output(filename):
    source_im = Image.open(filename)
    source_im.convert('RGB')
    source_data = source_im.load()
    
    width, height = source_im.size
    #print "width, height:", width, height
    
    for i in xrange(height):
        for j in xrange(width):
            r,g,b = source_data[j,i]
            print "#%02x%02x%02x" % (r,g,b) , # comma to suppress newline
        print # new line add end of row
        
output(sys.argv[1])
```

if python is ok then this should work with any image format.

---

### Post by MindSz on 2010-05-06
I've done image stuff in C, but I did it for PPMs (or BMPs for Windowers) ...There's JPG to PPM program available for free on the web.

---

### Post by cybo on 2010-05-07
@ssam

thanks. i ended up using your code.

---

### Post by lavinog on 2010-05-07
Have you tried octave in place of matlab?

---

### Post by cybo on 2010-05-07
no i didn't. i never used it before. but the python code worked really well. thanks for the help though.

---

