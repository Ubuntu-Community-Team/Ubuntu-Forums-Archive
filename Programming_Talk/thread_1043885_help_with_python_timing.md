---
title: "help with python timing"
date: 2009-01-18
forum: Programming Talk
---

### Post by grepgav on 2009-01-18
Hey all - I am working on a homework assignment that involves implementing RSA and now doing some benchmarking on factoring. I chose to do the work in python, and I am fine with actually getting the algorithms to work correctly.

I'm looking for help with timing how long certain functions take to execute. I have looked all around and most solutions involve:

```

t1 = time.time()
somefunction()
t2 = time.time()

elapsed = t2 - t1

```

which seems to work - but it lacks the precision I need. With all my sample cases for the assignment I get runtimes of 0. 

Does anybody know of any other ways of figuring out elapsed time?? Or is this the most precise I can get?

Thanks

---

### Post by WW on 2009-01-19
Take a look at the [timeit](http://docs.python.org/library/timeit.html) module in the standard library.

---

### Post by grepgav on 2009-01-19
ah I will give that a try -- thanks

---

