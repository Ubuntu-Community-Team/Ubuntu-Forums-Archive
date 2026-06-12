---
title: "how to write a C module for python"
date: 2006-02-23
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-23
Hi,

I am writing code in python. I want to call a function which is written in C, all other code is in Python. How can I accomplish this.

```

x = AckermanFunction(m, n)
print x

```

AckermanFunction is written in C. It is well known for testing compilers ability to perform recursion.

Any comments on how to do the job.

Thanks

---

### Post by toojays on 2006-02-23
The official python documentation for what you want to do is [Extending and Embedding the Python Interpreter](http://docs.python.org/ext/ext.html).

An alternative approach is to use SWIG. If you're only passing ints through the interface, it's trivial to do what you want with SWIG. You can probably just modify one of the examples from the swig-doc package.

---

