---
title: "How do I write a python wrapper around C++ code?"
date: 2010-07-14
forum: Programming Talk
---

### Post by stair314 on 2010-07-14
Can anyone point me to a tutorial somewhere?

---

### Post by nvteighen on 2010-07-14
> **stair314 said:**
> Can anyone point me to a tutorial somewhere?

Do you mean having a C++ compiled shared library and creating a Python binding for it? I'm not sure if this is possible as it is in C.

But, what's possible is creating a C++ extension module... if it's about having some part of a Python program written in C++ for more efficiency or whatever. Look at this: [http://docs.python.org/extending/extending.html](http://docs.python.org/extending/extending.html)

---

### Post by Mordred on 2010-07-14
Try swig:

[http://www.swig.org/]("http://www.swig.org/")

This generates a.o. python wrappers for C/C++ functions.

---

### Post by nvteighen on 2010-07-14
> **Mordred said:**
> Try swig:

[http://www.swig.org/]("http://www.swig.org/")

This generates a.o. python wrappers for C/C++ functions.

Wow... I heard about SWIG before and just didn't pay any attention to it... Now that I've tried it I highly recommend it. It's really awesome.

Take a look at the Tutorials... Be aware that you may have to install python2.x-dev (or python-dev) in order to make it work.

---

### Post by stair314 on 2010-07-14
Oh wow, yeah swig looks great. Thanks!

---

