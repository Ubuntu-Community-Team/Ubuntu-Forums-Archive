---
title: "[SOLVED] Tesseract &amp;amp; Python Script as GUI front-end"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-17
Someone has written a gui front end for Tesseract. It is written in Python. I have attached it as a text file to this post. It MUST be renamed with the .py filename extension. Rename the file and remove

.txt

==============

My question is this ... How do I get this to work with Tesseract?

---

### Post by company69 on 2008-11-17
all you have to to is open a terminal window, change to the directory that guitesseract.py is in then type:
*python guitesseract.py* 
The program will then start. I already had tesseract and imagemagick installed using the synaptic package manager on 8.10.

---

### Post by CoolJohnB on 2010-06-12
Installed guitesseract.py and got it working without problem.  But the output text file is a load of garbage!! Does anyone know why? And also what I can do about it?

Thanks for any help offered

---

### Post by rodrigo.hernandez.r3 on 2010-08-11
The program takes the JPG file and when the script is converting to TIFF, remmember that Tesseract only reads TIFF format, it is rotated 90°, so just de-select the rotation, and with that you will have in the correct way of lecture the image.

Regards.

---

