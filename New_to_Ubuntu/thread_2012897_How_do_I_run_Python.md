---
title: "How do I run Python?"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by afz12 on 2012-06-30
I've intended to try programming in Python for some time (Ubuntu 12.04) and I think I have it installed. I have a sample text program as follows to start with,

# This is a new text file for Python
def foo(omega, phi, t):
import numpy
import pylab
t = numpy.arrange(o,30,0.01)
y = foo(1.1, 0, t)
N = 5
print numpy.random.normal(1,0.5)
omega = [1,2,3,1.4]
phi = [0.4,0.1,0.4,0.1]
print y
s = t * 0.0;
for i in range(N-1):
	print i
	s = s + foo(omega[i], phi[i], t)
pylab.plot(t,s)
pylab.show()

My question is - How do I make it run???

It saves and shows some colored text so I assume something is being recognized but what do I need to do in order to make it, or parts of it RUN? Do I need to download additional files? Do I need to add a "path"? - if so how do I do this?

I am not a software programmer but I'm familiar with using Mathcad for complex programming (e.g. "least squares" (A^T A)^-1 A^T y = x given y = A x, neural nets, etc). Mathcad runs easily, so please indicate what steps I need to take for Python (don't assume I know any jargon terms in Linux!)

Thanks in advance

---

### Post by rai4shu2 on 2012-06-30
You should probably refer this question to this forum:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Lots of good threads there.

---

### Post by guilleme on 2012-06-30
If I am not completely wrong, you need a compiler for running it. 
A compiler is a program that takes your code, and converts it into a thing that can run on the computer. 
You can check the download python webpage, and get the files you need from there to get your compiler running. ([http://www.python.org/download/](http://www.python.org/download/)). 
Another, easier, way to do it would be to search for "python" on the software centre on the left bar. A program named "IDLE" could be good for you. IDLE is an "IDE" ("Integrated Development Environment"). That means you can edit you code and run it from there without changing programs. 
To use IDLE: open it, open a new window, put your code in there, save it, and press "f5" to run it. The first window in IDLE is used to print the output of your programs. 
Hope this helps!

---

### Post by alenis on 2012-06-30
Save your program in a file, give it a name, e.g. test.py, then open a terminal and give this command:

```
python test.py
```

---

### Post by afz12 on 2012-06-30
Hi Alenis

Thanks Alenis - that was exactly the information I needed. Python runs perfectly now - after I corrected a few typo's that it indicated. It displayed text and then a plot - and quite fast.

Thanks also guilleme and rai4shu2 for your best intentions. I had run Python some years ago (shortly) and forgot the method of starting it. I thought I needed to save the text file and then run it in a terminal somehow - I'll eventually want to compile the final program but initial debugging needs to be done real time - especially with maths were many approaches need practical side-side evaluation.

My main interest is to use Python to emulate a neural network. I have these running well in Mathcad/Windows but I only have a 32 bit version and this severely restricts the number of neurons I can simulate. With Python (and Octave and SciLab - I might look at these later also) I can run 64 bits and this limitation "should disappear".

Thanks

---

