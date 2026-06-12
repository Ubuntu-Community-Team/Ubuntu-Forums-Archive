---
title: "[Python] Image handling coding advice"
date: 2008-07-01
forum: Programming Talk
---

### Post by IMOC on 2008-07-01
I have some Python code which loads a gif image from a file and stores the raw image data (just one channel) into a Python array ready to be sent to a display.  This code snippet (which does work) shows how I am currently doing this:

```

import os, time, sys, array  # Standard python modules
from Tkinter import *

# Load a .gif file
image_filename = "test.gif"  # 1280 x 950 image
start_time = time.time()
root = Tk()
bg_image = PhotoImage(file = image_filename)
image_y_size = bg_image.height()
image_x_size = bg_image.width()

# Copy image data into an array
bg_image_array = array.array('B')  # Clear array
# Assume landscape mode background image
for y in range(image_y_size):
    for x in range(image_x_size):
        bg_image_array.append(int(bg_image.get(x, y).split(' ')[0]) >> 4)

        
stop_time = time.time()
# Code to send bg_image to read H/W display goes here...
#

# Output time taken
print "Time taken: %f" % (stop_time - start_time)

```

The problem I have is this code takes 17 seconds to run with a 1280 x 960 image, which is far too long for my application.

I am quite new to Python and this is my first attempt at coding this.  Is there a better was to code this which will speed it up?

Is it worth coding this part of the code in C to speed it up?


Thanks

---

### Post by xlinuks on 2008-07-01
Since Python is an interpreted language the only way to go is find a library of some native language (like C) and use that, there's no way you do fast bytes pushing from an interpreted language.

---

### Post by WW on 2008-07-01
You can use the [Python Imaging Library](http://www.pythonware.com/library/pil/handbook/index.htm) (PIL).  It has a library of transformations, so once you read the file, you can process it yourself or use an appropriate PIL function.

For example,
```

import Image


im = Image.open('pic.gif')

print "Format: %s   Width: %d  Height: %d" % (im.format,im.size[0],im.size[1])

pix = im.load()  # Load the image into a pixel access object

print "At (0,0): ", pix[0,0]


```

---

### Post by evymetal on 2008-07-01
> **WW said:**
> You can use the [Python Imaging Library](http://www.pythonware.com/library/pil/handbook/index.htm) (PIL). 


I'll second that - PIL is fairly good, and if you want to do lots of bit handling you may also want to look at Numpy - it's got special arrays designed for fast math tricks.

---

### Post by IMOC on 2008-07-01
Thanks for all the advice everyone.  The PIL code snippet was very interesting.  However this code has to check out of a repository and run on many platforms, Cygwin being one of the platforms.  Since the Python in Cygwin does not come with PIL as standard I am not able to use it.

It looks like I shall need write some C code to do this operation.

Thanks again.

---

### Post by pmasiar on 2008-07-01
> **IMOC said:**
> It looks like I shall need write some C code to do this operation.

Or script installing PIL if not present?

---

### Post by IMOC on 2008-07-02
> **pmasiar said:**
> Or script installing PIL if not present?

That is an interesting idea, I didn't think of that.

However when I installed PIL into Cygwin's Python it broke Tkinter and then it didn't work anyway.  If I could only get the Cygwin platform dropped many of the problems I am seeing would go away.

---

### Post by pmasiar on 2008-07-02
Dropping support for a platform is business decision. Tell them how much the cost/time will be without cygwin, and what is increase with cygwin - and they can decide if it is worth the cost.

It looks like broken dependencies for PIL on cygwin. One possible way is to investigate and fix dependencies - ask on cygwin list. 

Or, does cygwin has some different image library in C? You may be able to create python bindings for it (easy), without  doing the programming. Then create a python wrapper, and use that on cygwin and PIl elsewhere.

---

