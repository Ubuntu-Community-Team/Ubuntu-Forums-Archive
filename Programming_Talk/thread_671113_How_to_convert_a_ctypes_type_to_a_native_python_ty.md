---
title: "How to convert a ctypes type to a native python type"
date: 2008-01-18
forum: Programming Talk
---

### Post by IMOC on 2008-01-18
I am quite new to Python and trying to call functions in a windows DLL, but have run into a problem.  The function in question has a pointer to a uint32 passed to it, which it then uses to return data.

I can easily pass a pointer to a variable of the correct type (c_uint), but I cannot then convert that value back to a native python type to use.

A simplified example showing the problem:


[FONT="Courier New"]
[B]import ctypes
test_param = ctypes.c_uint(10)
print "test_param value: %x" % test_param[/B]
[/FONT]


The output from this is:
Traceback (most recent call last):
  File "test2.py", line 3, in <module>
    print "test_param: %x" % test_param
TypeError: int argument required
>>> 

So how do I convert 'test_param' back to a native python type so the string formatting operation does not fail.

Thanks,
Chris

---

### Post by IMOC on 2008-01-18
Okay I have figured this one out for myself!

[FONT="Courier New"]import ctypes
test_param = ctypes.c_uint(10)
print "test_param value: %x" % test_param**.value**[/FONT]

---

