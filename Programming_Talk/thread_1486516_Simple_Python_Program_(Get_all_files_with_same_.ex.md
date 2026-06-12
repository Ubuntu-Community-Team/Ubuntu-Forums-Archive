---
title: "Simple Python Program (Get all files with same .ext)"
date: 2010-05-17
forum: Programming Talk
---

### Post by Eremis on 2010-05-17
Hi All!

I am making a program that will resize all pictures (JPEG) in a given directory. For my final product I want to be able to just do something like this:

Eremis@linux-machine:~$ python /home/Eremis/Pictures/Myphotos

and the result would resize every picture in that directory to a certain size (800 X 600 default). I don't want to worry about arguments yet (For size....). I just want to have a working program that would resize every single .JPG file into 800X600 size...

I have the code written to resize a single image, which I will post below. My question is how would I get all the files in a certain directory only with JPG ending and resize them with my resize function....

```

import Image
import os

def ResizePicture(pathFrom, pathTo = os.getenv('HOME'),width = 800, height = 600):

    fileName = os.path.basename(pathFrom)
    
    img = Image.open(pathFrom)
    imgResized = img.resize((width, height), Image.ANTIALIAS)

    picture.save(pathTo + '/' + fileName)

```

Thx!

---

### Post by jeffathehutt on 2010-05-17
The [glob]("http://docs.python.org/library/glob.html") module can return a list of filenames based on a pattern, such as *.jpg

The glob returns a list, so to apply your function to each file, just iterate over the list.

```
for filename in glob.glob('*.jpg'):
    <run your function on filename>

```
(that's just an example) :)

---

### Post by Eremis on 2010-05-17
I will try it...

Thanks!

---

### Post by Eremis on 2010-05-18
It all worked out... Thanks again!

Here's my code:

```

import Image
import os
import glob

def ResizePicture(pathFrom, pathTo = os.getenv('HOME'),width = 800, height = 600):

    fileName = os.path.basename(pathFrom)
    
    img = Image.open(pathFrom)
    imgResized = img.resize((width, height), Image.ANTIALIAS)

    imgResized.save(pathTo + '/' + fileName)
    
for filename in glob.glob('*.jpg'):
    print filename
    ResizePicture(filename, width = 800, height = 600)

```

---

