---
title: "Python and C compatibility"
date: 2009-08-18
forum: Programming Talk
---

### Post by PaulM1985 on 2009-08-18
Hi

I work for a company that has its own in-house language (which is interpreted) that is used to provide extra functionality to the software.  The actual software is written in C and C++.  The in-house language isn't great.  It is similar to C but very stripped down (no for-loops, recursion doesn't work properly).

I was wondering how easily would it be to use python as an alternative to the inhouse language.  Is it possible to:

Call python functions in files from a C/C++ function?
Call C/C++ functions from python functions?
Set global variables in python functions/classes from C/C++ functions?

Python has alot more functionality that would be useful but I wanted to know how difficult it would be to implement.

Thanks

Paul

---

### Post by uljanow on 2009-08-18
I haven't used it, but Boost.Python looks promising.


[1] [http://www.boostpro.com/writing/bpl.html](http://www.boostpro.com/writing/bpl.html)

---

### Post by slavik on 2009-08-18
with perl/python/ruby, you can embed the interpreter into C/C++ code and with just enough sugar and design, you can have ppr run inside you program.

---

