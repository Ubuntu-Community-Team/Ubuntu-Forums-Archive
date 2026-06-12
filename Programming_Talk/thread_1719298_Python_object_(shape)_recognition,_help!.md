---
title: "Python object (shape) recognition, help!"
date: 2011-04-01
forum: Programming Talk
---

### Post by bestron on 2011-04-01
I'm beginning a project that has shapes of objects recognition as a part of it, I'll be programming in python
any help with this will be acceptable: libraries, algorithms or source codes, as I don't have any ideas on how to implement that in programming

---

### Post by Tony Flury on 2011-04-01
ok - what sort of image (bitmap/raster or vector) ? simple shapes (square, triangle etc), or complex. Shaded or simple colours ?

There are a lot of things to consider

if you are dealing with a bit map image, you will probably want to start with some edge detection, and simplification - i.e. convert your bitmap into a simple vector image.

---

### Post by Arndt on 2011-04-01
> **bestron said:**
> I'm beginning a project that has shapes of objects recognition as a part of it, I'll be programming in python
any help with this will be acceptable: libraries, algorithms or source codes, as I don't have any ideas on how to implement that in programming

Can you give an example?

---

### Post by bestron on 2011-04-01
well that will be an image from a file or a camera such as a mug, clock or something like that

---

### Post by Tony Flury on 2011-04-07
You do realise that there are teams of experts working on this and starting to get results only with 10,000s of hours of work.

Visual recognition of real world objects is tough - you have to deal with colour, shading, lighting, orientation, texture, focus, distance. You could spend a lot of time getting the programm just to consistently recognise the exact same object over and over again - and not to generate false positives.

All in all - not a job for one person i would not have thought.

And then you need to start to thing about classification - for instance - you show your program two objects - can it recognise that they are both clocks - i.e. can it recognise the common features - hands, clock face etc, and then what about clocks with out numerals on the face, or with roman numberals, or where the hand stay still and the face rotates, or digital clocks ?

---

### Post by simeon87 on 2011-04-07
Most of all, I think Python is not fast enough to do real world image processing. You could create an application that loads an image and calls a C library to do the image processing but I don't think you can do image processing with many filters in Python itself.

---

### Post by LemursDontExist on 2011-04-07
You could try looking the the [Python Imaging Library]("http://www.pythonware.com/products/pil/") as a starting point.  This should allow you do do edge detection and relatively fast filter application.  That said, unless you're trying to do is fairly simple, or you're ready to devote hundreds of hours to the task, I think you're out of luck.  As the others have noted, image recognition is still very much in it's infancy.

If you gave us some more details as to what you're hoping to do, we might be able to help more!

---

### Post by g30rg3 on 2011-05-04
Well I'm not an expert, but since I have worked with image processing using Matlab, I think you could code the program in Matlab and use a Matlab to Python conversion library. That would be much easier. But as far as I know, the conversion library is not exhaustive and there may be functions that are not supported

---

### Post by cheapodonuts on 2011-06-10
Anyone notice this thread started on April 1st? ;)
 Still, I'd love to  have some thing like this as a functioning program. I need some automatic system to scare Gulls away from my garden. Not other birds, just Gulls that steal my cat's food. :D

---

