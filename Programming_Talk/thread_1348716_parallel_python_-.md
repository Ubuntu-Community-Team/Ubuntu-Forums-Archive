---
title: "parallel python -"
date: 2009-12-07
forum: Programming Talk
---

### Post by bigdidz on 2009-12-07
I try to use [parallel python]("http://www.parallelpython.com/") to do multiprocessing task.

I download the package using Synaptic and the python-dev.

When I run the [sum_prime.py]("http://www.parallelpython.com/content/view/17/31/") example, the first thing I see is:

> DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  import popen2
/usr/lib/pymodules/python2.6/pp.py:40: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
/usr/lib/pymodules/python2.6/pptransport.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
/usr/lib/pymodules/python2.6/pp.py:57: DeprecationWarning: the sets module is deprecated
  from sets import Set as set
Usage: python sum_primes.py [ncpus]
    [ncpus] - the number of workers to run in parallel, 
    if omitted it will be set to the number of processors in the system



And then all the program run using only one processor.

How do I fix that?  I find no help on google.  Is parallel python the good python to do multiprocessing using python?

Thanks
Didier A.

---

### Post by Can+~ on 2009-12-07
Apparentley, that module is for python 1.5.7. Python currently is on 2.6.x (and the 3.x branch), so it's no surprise that it doesn't work.

Use the threading module:
[http://docs.python.org/library/threading.html](http://docs.python.org/library/threading.html)

---

### Post by bigdidz on 2009-12-08
I found a package call [PaPy]("http://code.google.com/p/papy/").  It seem more complicated to use but more complite.  I'll work on that and repost my solution.

Thanks

---

