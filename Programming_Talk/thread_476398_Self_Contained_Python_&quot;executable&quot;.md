---
title: "Self Contained Python &quot;executable&quot;?"
date: 2007-06-17
forum: Programming Talk
---

### Post by Tr0janV0dka on 2007-06-17
Is there any way I can make a self contained python executable? By self contained, I mean when the .py or .pyw is ran, it doesn't need pre-existing Python stuff on your computer (in both Windows and Ubuntu, but I'm pretty sure Ubuntu comes pre-packaged with it anyway). If so, how is it possible?

Python is awesome! I'm making a simple yes or no question program right now.  I only had to read Instant Hacking until the start of the Flow section and it's pretty much experimentation that got me where I am!

And just another quick question, why doesn't this work?

Yes=1
yes=1
No=0
no=0
q1 = input('Question1')
if q1=1:
   print "blahblahblah"

It say's the "=" in "q1=1:" is a syntax error! The way I got it to work properly was:

if 1.1>q1>0.9:
   print "blahblahblah"

---

### Post by Gustav on 2007-06-17
> **Tr0janV0dka said:**
> Is there any way I can make a self contained python executable? By self contained, I mean when the .py or .pyw is ran, it doesn't need pre-existing Python stuff on your computer (in both Windows and Ubuntu, but I'm pretty sure Ubuntu comes pre-packaged with it anyway). If so, how is it possible?

Python is awesome! I'm making a simple yes or no question program right now.  I only had to read Instant Hacking until the start of the Flow section and it's pretty much experimentation that got me where I am!

And just another quick question, why doesn't this work?

Yes=1
yes=1
No=0
no=0
q1 = input('Question1')
if q1=1:
   print "blahblahblah"

It say's the "=" in "q1=1:" is a syntax error! The way I got it to work properly was:

if 1.1>q1>0.9:
   print "blahblahblah"

When comparing stuff you need to use the double equal sign (==)
```
if q1==1:
   print "blahblahblah"
```

---

### Post by Tr0janV0dka on 2007-06-17
> **Gustav said:**
> When comparing stuff you need to use the double equal sign (==)
```
if q1==1:
   print "blahblahblah"
```

Nice! Thanks for that! When I tried that before, it didn't work for some reason, probably because I had it as:

```
if q1==Yes:
print "blahlblahlblah"
```

---

### Post by drummer on 2007-06-17
EDIT: oops... too slow

---

### Post by christhemonkey on 2007-06-17
For Windows you can use py2exe to create an exectuable that has everything that you need to run it, although then you have to distribute all the .dlls etc with it.
See here:
[http://www.py2exe.org/index.cgi/Tutorial](http://www.py2exe.org/index.cgi/Tutorial)

You can then use NSIS to build one .exe or an installer that will run your program and be just one file to distribute.

---

### Post by kknd on 2007-06-17
> **christhemonkey said:**
> For Windows you can use py2exe to create an exectuable ...


Yep! And in Linux... well, you dont need to do anything, 99% of the distros come with python 2.4+

---

