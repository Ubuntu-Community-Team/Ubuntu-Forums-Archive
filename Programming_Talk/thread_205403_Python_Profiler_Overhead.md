---
title: "Python Profiler Overhead"
date: 2006-06-28
forum: Programming Talk
---

### Post by warspir on 2006-06-28
Hi

When trying to profile a Python program of mine, I saw that it ran much slower than without the profiler (nearly 6 times).

So I did this experiment.
```

>>> def HelloWorld():
    print "Hello World"
>>> import timeit
>>> t = timeit.Timer('HelloWorld()','from __main__ import HelloWorld')
>>> t.timeit(1)
Hello World
9.7990036017472188e-05
>>> t.timeit(1)
HelloWorld
0.0013089179992675781
>>> import profile
>>> profile.run('HelloWorld()')
HelloWorld
           4 function calls in 0.090 CPU seconds
......... <profiling output>
>>> profile.run('HelloWorld()')
HelloWorld
           4 function calls in 0.000 CPU seconds
......... <profiling output>

```

Does anyone know an explanation for this?

Thanks

---

### Post by ynef on 2006-06-29
Actually keeping track of function calls and timing them makes the program go slower? :)

Profiling code isn't free -- it slows things down. However, it is good at telling you if you have a function that takes way too long in relation to its input -- the actual wall time isn't a good measure, since it's load as well as processor speed (etc) dependant.

---

### Post by warspir on 2006-07-02
But is this overhead a bit too large on Ubuntu?

I have tried this on another Linux distribution (Debian if I remember correctly) and retrieved the following results for the same experiment:

```
t.timeit(1)
Hello World
6.4849853515625e-05
>>> t.timeit(1)
Hello World
3.2901763916015625e-05
>>> import profile
>>> profile.run('HelloWorld()')
Hello World
         4 function calls in 0.000 CPU seconds
.........<profiling output>
>>> profile.run('HelloWorld()')
Hello World
         4 function calls in 0.000 CPU seconds
.........<profiling output>

```

0.09 CPU secs is quite different from 0.00 CPU secs

---

