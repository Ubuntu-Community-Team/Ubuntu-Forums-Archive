---
title: "Cython - how to compile Python smart way"
date: 2008-08-20
forum: Programming Talk
---

### Post by pmasiar on 2008-08-20
Reading [this maxithread on python mailing list](http://groups.google.com/group/comp.lang.python/browse_frm/thread/8c7c359b600881e0/f84617b03f0ddfc1) about compiling Python [and if goal is making it as fast as C, or c (== speed of light) is the ultimate (even if unattainable) goal, with subdiscussion about Star Wars], I found interesting project:

[http://cython.org/](http://cython.org/)

> Cython is a language that makes writing C extensions for the Python language as easy as Python itself. Cython is based on the well-known Pyrex, but supports more cutting edge functionality and optimizations.

The Cython language is very close to the Python language, but Cython additionally supports calling C functions and declaring C types on variables and class attributes. This allows the compiler to generate very efficient C code from Cython code.

This makes Cython the ideal language for wrapping for external C libraries, and for fast C modules that speed up the execution of Python code. 

This is the speed done right way: Write **all**your pilot code in Python, profile it, extract libraries (still in Python!) and test the API: then sprinkle in some type definitions, and translate Python --> Cython --> C. Done!

Now if someone says that Python is slow, my answer is: it just shows utter ignorance: With Cython, Python can be as fast as you care it to be, close to the speed of C (even if not c :-) )!

---

### Post by slavik on 2008-08-20
If the "sprinkling" of types is mandatory then:
Cython kills one of the features that I like about Python. Automatic bignum. Then you are running the risk of setting something as float instead of int, possibly messing up any remainder check (x%y == 0).

Otherwise, it is something that Perl6 has that allows you to tell the interpreter that there is some range of values that a variable can take on, thus the optimisations on size and the way things are evaluated ...

---

### Post by days_of_ruin on 2008-08-20
Nice!I have pyrex installed this is even better.
So would it be possible to wrap a c module that uses gtk and
use it in pygtk?Like have the c module return a gtk.Pixmap or something?

---

### Post by pmasiar on 2008-08-20
> **slavik said:**
> If the "sprinkling" of types is mandatory then:

You missed the point (if you read website): it is optional, and types can be also inferred.

But of course not all Python constructs are allowed, say, no dynamic messing with object attributes, of changing function body.

---

### Post by pmasiar on 2008-08-20
> **days_of_ruin said:**
> Nice!I have pyrex installed this is even better.
So would it be possible to wrap a c module that uses gtk and
use it in pygtk?Like have the c module return a gtk.Pixmap or something?

Yes, it is designed to be better.

Ask developers what is possible, I did not tried it yet.

---

