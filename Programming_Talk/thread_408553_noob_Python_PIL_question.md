---
title: "noob Python PIL question"
date: 2007-04-13
forum: Programming Talk
---

### Post by cisforcojo on 2007-04-13
Hey guys,

I'm trying to use the PIL to extract pixel information from a .png file and I'm falling on my face.
My sticking point (right now) is Python is saying the list object isn't callable.

Here is my code:
----------------------------------------------------------------------
import Image

image = Image.open('myfile.png')

pix = list(image.load())

for x in pix:
       print x

---------------------------------------------------------------------

The error I'm getting is: 
TypeError: 'list' object is not callable


I've seen this done in tutorials and I don't know why it's not working for me. 
Thanks for the help!

---

### Post by pmasiar on 2007-04-13
why you try to convert loaded image to a list? Did you tried to read the fine manual? [http://www.pythonware.com/library/pil/handbook/image.htm](http://www.pythonware.com/library/pil/handbook/image.htm)

Disclaimer: I never needed to use PIL for anything. But converting image object to a list just does not make sense to me. Does it to you?

---

### Post by WW on 2007-04-13
cisforcojo: Perhaps you meant to use getdata instead of load, e.g. pix = list(im.getdata()).  This is taken from the document that pmasiar linked to; scroll down to "getdata" in the "Methods" section.

---

### Post by cisforcojo on 2007-04-13
Yeah that's actually the link I was using for this. (I actually tried getdata() last night and thought erroneously that getdata() and load() were the same.)

What I want to do is get the color indices from a certain part of the picture.  It sorta looks like a grayscale bar and I thought that I could use getdata() for load the color indices (RGB values) into a list and then view the list.

Solved: I probably shouldn't write posts when I'm exhausted. For some reason it worked perfectly this morning. Thanks for the help, guys!

---

