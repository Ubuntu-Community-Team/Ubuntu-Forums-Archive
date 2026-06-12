---
title: "use C structure type in Python"
date: 2009-02-10
forum: Programming Talk
---

### Post by djbushido on 2009-02-10
Okay, finally generated a .so of a C program. Now I need to use some of its types to get it to work. I can technically recode everything to a new python class, but would prefer to avoid this if at all possible.

To import, I did
%from ctypes import *
%lib_flam3 = cdll.LoadLibrary("libflam3.so")

so everything should be accessible from lib_flam3, right?
so can i just do "test = lib_flam3.flam3_genome()"? (the flam3 genome is a structure, I've checked source code)

Thanks for your help...

---

### Post by jpkotta on 2009-02-11
[http://docs.python.org/library/ctypes.html#structures-and-unions](http://docs.python.org/library/ctypes.html#structures-and-unions)

I'm learning ctypes too, though my DLL doesn't have any structs.  I don't think you can get at typedefs from a DLL, at least I haven't seen anything to suggest it.  Some way or another, you need to have Python code explaining what the struct looks like.  So you can do this by hand as you say, or...

[http://www.swig.org/Doc1.3/Python.html#Python_nn19](http://www.swig.org/Doc1.3/Python.html#Python_nn19)

Swig will automatically generate that Python code, if you have the C source.  I've only played with Swig the tiniest bit, but I really wish I had the source to my DLL so I could use it.

---

### Post by djbushido on 2009-02-11
So I just feed SWIG the structure source? Is it really that easy? Surely not, in the realm of C.

Will try unless anybody else has an idea.

---

### Post by The Cog on 2009-02-11
[http://docs.python.org/library/struct.html](http://docs.python.org/library/struct.html)
should do the trick for you.

---

### Post by djbushido on 2009-02-11
that apparently was for a structure string. However, I got accomplished what I needed to, so closing unless further notice.

---

