---
title: "Python callbacks from C/C++"
date: 2012-02-10
forum: Programming Talk
---

### Post by Colin@oxford on 2012-02-10
I want to be able to pass a function from Python into C or C++ for it to be called later.  In Python this is easy:
```

def called():
**print "OK"

def call_it(f):

```

---

### Post by Colin@oxford on 2012-02-10
Sorry .. some hoe the "submit" button was pressed


I want to be able to pass a function from Python into C or C++ for it to be called later. In Python this is easy:
```

def called():
     print "OK"

def call_it(f):
     f()

callit(called)


```

and similarly in C.

I want to make the "call_it" function into C but I can't work out how to specify it correctly.  I have tried defining its argument as it would be if the function is C, i.e. void (*f)(), and also specifying it as a PyCodeObject*.  Neither works.

Any suggestions?

---

### Post by karlson on 2012-02-10
Have you looked at [Boost Python](http://www.boost.org/doc/libs/1_48_0/libs/python/doc/)?

---

### Post by Colin@oxford on 2012-02-11
> 
Have you looked at Boost Python?


I hadn't - the project is using SWIG - I will now!
Thanks

---

