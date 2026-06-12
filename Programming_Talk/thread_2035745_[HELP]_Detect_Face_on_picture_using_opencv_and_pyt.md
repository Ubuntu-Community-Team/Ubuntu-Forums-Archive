---
title: "[HELP] Detect Face on picture using opencv and python"
date: 2012-07-31
forum: Programming Talk
---

### Post by newbie45 on 2012-07-31
Hi, i am a complete beginner to python and i encountered some problem.

I'm using Ubuntu 12.04 LTS, Python 2.7 and OpenCV-2.4.1

What i am trying to do here is to detect face in a picture and the result is to display the coordinates which let me take the coordinates to help me crop the face out. Im trying to use python with opencv together.

The code that im using is taken from this website : [http://creatingwithcode.com/howto/face-detection-in-static-images-with-python/](http://creatingwithcode.com/howto/face-detection-in-static-images-with-python/)
The code is : ```
# http://python.pastebin.com/m76db1d6b

# Usage: python face_detect.py <image_file>

import sys, os
from opencv.cv import *
from opencv.highgui import *

def detectObjects(image):
  """Converts an image to grayscale and prints the locations of any
faces found"""
  grayscale = cvCreateImage(cvSize(image.width, image.height), 8, 1)
  cvCvtColor(image, grayscale, CV_BGR2GRAY)

  storage = cvCreateMemStorage(0)
  cvClearMemStorage(storage)
  cvEqualizeHist(grayscale, grayscale)
  cascade = cvLoadHaarClassifierCascade(
    '/usr/share/opencv/haarcascades/haarcascade_frontalface_default.xml',
    cvSize(1,1))
  faces = cvHaarDetectObjects(grayscale, cascade, storage, 1.2, 2,
                             CV_HAAR_DO_CANNY_PRUNING, cvSize(50,50))

  if faces:
    for f in faces:
      print("[(%d,%d) -> (%d,%d)]" % (f.x, f.y, f.x+f.width, f.y+f.height))

def main():
  image = cvLoadImage(sys.argv[1]);
  detectObjects(image)

if __name__ == "__main__":
  main()
```However, when i tried using this script, it stated that there is no module detected: opencv.cv

My script is called face_detect.py and my picture is called 1.jpg

So, i typed ```
python face_detect.py 1.jpg
```This is the traceback: ```
Traceback (most recent call last):
  File "face_detect.py", line 13, in <module>
    from opencv.cv import *
ImportError: No module named opencv.cv

```I had check that my python is working as i tested out with ```
python ~/OpenCV-2.4.1/samples/python2/turing.py
``` and it works.

So, is there any solution to this problem?
Thanks in advance! :D

---

### Post by albandy on 2012-07-31
Did you installed python-opencv ?

sudo apt-get install python-opencv

---

### Post by newbie45 on 2012-07-31
> **albandy said:**
> Did you installed python-opencv ?

sudo apt-get install python-opencv

Yes. I did installed python-opencv.

---

### Post by albandy on 2012-08-01
> **newbie45 said:**
> Yes. I did installed python-opencv.

I got that error before installing the package (see image attached).

I'm using 10.04, so this makes me think that is a version problem. 

Are you on 32 or 64 bit? I'm going to make an Ubuntu 12.04 installation on VirtualBox to test it.

---

### Post by newbie45 on 2012-08-01
> **albandy said:**
> I got that error before installing the package (see image attached).

I'm using 10.04, so this makes me think that is a version problem. 

Are you on 32 or 64 bit? I'm going to make an Ubuntu 12.04 installation on VirtualBox to test it.

Im on 32bit. This is the error i got : (see image attached)

---

### Post by albandy on 2012-08-01
It's a version problem, read the comments in:
[http://creatingwithcode.com/howto/face-detection-in-static-images-with-python/](http://creatingwithcode.com/howto/face-detection-in-static-images-with-python/)

they explain how to solve it.

---

