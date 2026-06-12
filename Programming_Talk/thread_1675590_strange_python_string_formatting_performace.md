---
title: "strange python string formatting performace"
date: 2011-01-25
forum: Programming Talk
---

### Post by ssam on 2011-01-25
I noticed some odd results in string formatting performance

```

sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%i"%1'
10000000 loops, best of 3: 0.0357 usec per loop
sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%s"%1'
10000000 loops, best of 3: 0.0357 usec per loop

```

here %i and %s take identical time. i would slightly expect %i to win (%s is more generic so ought to do more checking).

```
sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%i%i"%(1,2)'
1000000 loops, best of 3: 1.44 usec per loop
sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%s%s"%(1,2)'
1000000 loops, best of 3: 0.361 usec per loop
```

now with 2 numbers. %s is 4 times faster than %i. i really would not expect the more generic function to win. also why the change. any ideas whats going on?

i have also tried python 2.7 and got the same result.

---

### Post by MadCow108 on 2011-01-25
%s does not care what type of object it handles. it only needs that object to have __str__ implemented
%i on the other hand must check if the argument is a number before doing so.

so %s needs to do less work and is faster
this comes with the cost of less type safety in this case, you could have a string printed when you want an exception thrown.

do this:
if type(1) == type(int()) and type(2) == type(int()): "%s%s"%(1,2)
and the times will be similar

---

### Post by ssam on 2011-01-26
```
sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%s%s"%(1,2)'
1000000 loops, best of 3: 0.361 usec per loop
sam@oberon:~$ /usr/lib/python2.6/timeit.py '"%i%i"%(1,2)'
1000000 loops, best of 3: 1.44 usec per loop
sam@oberon:~$ /usr/lib/python2.6/timeit.py 'if type(1) == type(int()) and type(2) == type(int()): "%s%s"%(1,2)'
1000000 loops, best of 3: 1.29 usec per loop
```

so python is not using EAFP (Easier to Ask Forgiveness than Permission) internally in this case.

---

### Post by Queue29 on 2011-01-26
The "%" way of formatting strings is being deprecated anyway. You should get used to not using this wonderful feature before you get accustomed to it. 

[http://docs.python.org/release/3.0.1/whatsnew/3.0.html#pep-3101-a-new-approach-to-string-formatting](http://docs.python.org/release/3.0.1/whatsnew/3.0.html#pep-3101-a-new-approach-to-string-formatting)

---

### Post by ssam on 2011-01-26
yes. although the new style needs python 2.6 (some people like to run scientific linux with python 2.4 :-( )

i have a bunch of code that looks like

```

def f(f1):
    return "%.12e" % float(f)

def i(i1):
    return str(int(i))

out = ""
out += f(d['a']) + " " + f(d['b']) + " " + f(d['c']) + "\n"
out += i(d['d']) + " " + i(d['e']) + " " + i(d['f']) + "\n"
...

```

the output is an ascii input file of an old program, so f() and i() are functions so that the format could be easily tweaked (bad things happen if you give too many decimal places).

so i have been playing around with ways to make it faster.

---

### Post by MadCow108 on 2011-01-26
you might want to use join or direct formating instead of the + operator

the + operator performance varies over implementations and can be very slow. Strings are immutable so it implies a bunch of copying on each + call (=> N^2 complexity)
cpython can optimize that partly, others it may not.

---

