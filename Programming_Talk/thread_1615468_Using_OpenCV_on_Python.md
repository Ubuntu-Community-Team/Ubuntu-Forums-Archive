---
title: "Using OpenCV on Python"
date: 2010-11-07
forum: Programming Talk
---

### Post by khoi0107 on 2010-11-07
hi guys, I recently install ubuntu 10.04 and openCV for my uni project. I followed this instruction to install openCV 2.1 on ubuntu [http://tutorial.*****************/how-to-install-opencv-2-1-on-ubuntu-10-04.html](http://tutorial.*****************/how-to-install-opencv-2-1-on-ubuntu-10-04.html) 

Now I can use openCV **but only in C language (compiled by gcc/gpp)** I wanna use python but the import module gets error all the time. Even python example from openCV doesnt work.

This is camera.py example
```
#!/usr/bin/python
**import cv**

cv.NamedWindow("camera", 1)

capture = cv.CaptureFromCAM(0)

while True:
    img = cv.QueryFrame(capture)
    cv.ShowImage("camera", img)
    if cv.WaitKey(10) == 27:
        break

```This is the result when i run it:
```


risket@risket-laptop:~/Desktop/python$ python camera.py
Traceback (most recent call last):
  File "camera.py", line 2, in <module>
[B]    import cv
ImportError: No module named cv[/B]

```It happens to all examples, can't use openCV functions at all. 
I did installed SWIG wrapper for python but it's not working either.

I dont know if I have already installed the library for python (based on the instruction above), and if I have, can anybody help me import openCV module to python?  
I'm using ubuntu 10.04, python 2.6.5, openCV 2.1

PS: sorry if I made any silly question, im totally newbie.

---

### Post by fng44 on 2010-11-14
Hello, 
I think this is because you have not the good version of opencv for python. I think your code is for version 2. Checkout opencv wiki, look in install. You should find a way to install it with the version 2.1.
I had the same problem.

---

