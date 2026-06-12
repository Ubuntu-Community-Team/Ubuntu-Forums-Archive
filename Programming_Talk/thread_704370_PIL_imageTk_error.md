---
title: "PIL imageTk error"
date: 2008-02-22
forum: Programming Talk
---

### Post by KKarasu on 2008-02-22
I trying to create a launcher for programs of mine in Tkinter module.
the point is i want to show an image in a canvas on Tkinter, JPEG or PNG.

So i installed:

python-imaging tk
python imaging
and for jpeg some jpeg support i dont remember.
installed all bye synaptic

so this is the simplified code that should work too:

from Tkinter import *
import ImageTk

IMAGE=ImageTk.PhotoImage(image="L.jpeg")
root=Tk()
canvas=Canvas(root)
canvas1.create_image(0,0,image=IMAGE,anchor=NW)
canvas.pack()

the error being:

Exception exceptions.AttributeError: "PhotoImage instance has no attribute '_PhotoImage__photo'" in <bound method PhotoImage.__del__ of <ImageTk.PhotoImage instance at 0x87c7fac>> ignored
Traceback (most recent call last):
  File "/home/KK/Desktop/TRY.py", line 6, in <module>
    IMAGE=ImageTk.PhotoImage(image="L.jpeg")
  File "/usr/lib/python2.5/site-packages/PIL/ImageTk.py", line 109, in __init__
    mode = Image.getmodebase(mode)
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 235, in getmodebase
    return ImageMode.getmode(mode).basemode
  File "/usr/lib/python2.5/site-packages/PIL/ImageMode.py", line 46, in getmode
    return _modes[mode]
KeyError: 'L.jpeg'


i think it has something to do with the libraries, but i am sure i installed everything, even with other type of image in doesn't work.

---

