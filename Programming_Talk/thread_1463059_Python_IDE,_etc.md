---
title: "Python IDE, etc"
date: 2010-04-26
forum: Programming Talk
---

### Post by HHx66 on 2010-04-26
I've recently taking an interest in learning to program in Python, I'm relatively new to programming, though not entirely a beginner (I have some experience in basic, pascal, and various scripting languages) I have a book and some other resources, but I was wondering if anyone knows of a good development enviroment for Python? Also, what compiler should I use, etc? Basically some intro level stuff and forgive the newbiness, I'm just getting into this and starting to read it, I'm dedicated to learning it, I just need a few more pointers and some help. Thanks all.

---

### Post by sheperson on 2010-04-26
> **HHx66 said:**
> I've recently taking an interest in learning to program in Python, I'm relatively new to programming, though not entirely a beginner (I have some experience in basic, pascal, and various scripting languages) I have a book and some other resources, but I was wondering if anyone knows of a good development enviroment for Python? Also, what compiler should I use, etc? Basically some intro level stuff and forgive the newbiness, I'm just getting into this and starting to read it, I'm dedicated to learning it, I just need a few more pointers and some help. Thanks all.

I think you could use PyDev with Eclipse and you should use the Python interpreter which comes with Ubuntu.
You can find info on how to install PyDev here:
[http://pydev.org/](http://pydev.org/)

---

### Post by raydeen on 2010-04-26
For beginning, I'd use IDLE (available from the repos and also available in Windows and OSX if you want to test cross-platform - this can come in handy if you want to make sure that text formats properly across all three), or Geany which is also available on all three but might take some extra legwork to get going on a Mac. As for compilers, Python is interpreted so no compilation is necessary. Just enter the code and hit Run. It actually produces a byte-code similar to Java that is read by the Python app on your system and you can make self-contained and executable scripts if you need to but that's usually for after you've tested and made sure everything runs properly.

If you want to go real barebones, just open up a text editor, type in some code, save it with a name and the .py extension and from the Terminal type python and the name of your program. 

$ python myprog.py

And it will run.

---

### Post by phrostbyte on 2010-04-26
[Geany]("apt:geany") is pretty decent.

---

### Post by HHx66 on 2010-04-26
Thank you all very much for the info, I'll try out each one see what fits me. Any tips/advice on sites for beginners or some basic starting info?

---

### Post by HHx66 on 2010-04-26
Also, what about (for when I get there) gui programming? what would be used for that? or am I thinking too far ahead at this point?

---

### Post by xaegis on 2010-04-26
> **phrostbyte said:**
> [Geany]("apt:geany") is pretty decent.


+1 to the vote for Geany.


I'm a beginner as well and I've found that the documentation for PyQt  is excellent. (It,Qt, also has a very snazzy gui designer in the repos ):)

Good luck, and happy coding!

---

### Post by HHx66 on 2010-04-27
I'm using Geany and PyQt, thanks for all the help.

---

