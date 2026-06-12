---
title: "problem with pysol"
date: 2013-05-25
forum: Packaging and Compiling Programs
---

### Post by poker master on 2013-05-25
I am new to python but not programming as a whole. I downloaded pysol ver 4.82.1. .After reading the install notes I tryed running pysol.py in python 2.27. I get back this. 
 
Traceback (most recent call last):
  File "/home/dan/build1/pysol-4.82.1/src/pysol.py", line 47, in <module>
    from main import main
  File "/home/dan/build1/pysol-4.82.1/src/main.py", line 48, in <module>
    from app import Application
  File "/home/dan/build1/pysol-4.82.1/src/app.py", line 54, in <module>
    from images import Images, SubsampledImages
  File "/home/dan/build1/pysol-4.82.1/src/images.py", line 47, in <module>
    from pysoltk import tkversion, loadImage, copyImage, createImage
  File "/home/dan/build1/pysol-4.82.1/src/pysoltk.py", line 81, in <module>
    exec "from " + m + " import *"
  File "<string>", line 1, in <module>
  File "/home/dan/build1/pysol-4.82.1/src/tk/soundoptionsdialog.py", line 44, in <module>
    from pysolaudio import pysolsoundserver
  File "/home/dan/build1/pysol-4.82.1/src/pysolaudio.py", line 44, in <module>
    import pysolsoundserver
ImportError: No module named pysolsoundserver
>>> 

I also tryed running the executeable Pysol  in the main dir. The notes say this should run the byte code version. 
 
It comes back saying ./pysol: could not find the file 'pysol_27.pyc

there is an install script but i can't seem to do anything with it either.

If i can get this running I would like to look at the code as I have an idea for a good card game.
 
Help.

---

