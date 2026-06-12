---
title: "I have gcc and I can get lesstif, but what about X and Xt?"
date: 2009-12-27
forum: Programming Talk
---

### Post by gamphd on 2009-12-27
As far as I can tell, the lesstif package assumes the presence of X11 and Xt and only provides the Xm modules to be compiled from existing libraries.  Am I mistaken?  If not, do I have to go to an MIT site for X?  When I had Redhat, X11 includes and libs came with it, as far as I know, so I never had to deal with this issue.

---

### Post by gamphd on 2009-12-27
Never mind.  I just found this in another post:

apt-get install libx11-dev

---

### Post by gamphd on 2009-12-27
So much for that.  Neither X11 nor lesstif contains Xt (or it's Xt with a release < R5), so I'm still stuck with an unusable lesstif package.  Is this 2009?

---

### Post by gamphd on 2009-12-27
After a could more telepathic apt-get commands, one for x11-xext-dev and one for libxext-dev (!?!?!?), I was finally able to make install with no errors.  It should be intuitively obvious that x11-xext-dev will install libXext.so but not libXext.a, right?!?!?!

---

### Post by gamphd on 2009-12-27
could=couple !!!

---

### Post by gamphd on 2009-12-27
In any event, I was able to build helloworld.c using widgets (from [http://www.linuxjournal.com/article/3666](http://www.linuxjournal.com/article/3666) ) and run it successfully.

---

### Post by wmcbrine on 2009-12-27
> **gamphd said:**
> so I'm still stuck with an unusable lesstif package.  Is this 2009?Almost 2010.

So maybe you should be using something like Gtk? :)

---

### Post by gamphd on 2009-12-28
If I wanted to do conversion, I might, but I want to implement hundreds of thousands of lines of legacy software that was converted from PL/I and GKS to C and Motif, so my main focus is to compile it and get it running, not to make it "state of the art," in the opinion of some.  Regardless, I also want to know why I had libXm.a last time, but now all I have is libXm.so, and I have to prefix an export statement to my command line to run the program.

Thanks anyway.  :P

---

### Post by gamphd on 2009-12-28
Besides, even if lesstif has ignored my fix to the selection-list widget, I have the fixes and can make them available to customers if and when the software itself is released again, rather than just its output.

---

### Post by jpkotta on 2009-12-29
You wanted xorg-dev, which depends on a ton of -dev packages, including the ones you've mentioned.

Also, if you know the name of a file and want to know what package it's in, you will find apt-file and packages.ubuntu.com useful.

---

