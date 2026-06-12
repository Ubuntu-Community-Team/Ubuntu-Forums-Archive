---
title: "which type of string is faster?"
date: 2009-05-15
forum: Programming Talk
---

### Post by arikshtiv on 2009-05-15
What string is faster?

this:
```

num = 11
string = 'a long string'
'''Testing Multiline Code
num: %(num)i,
string: %(string)s
num again: %(num)i,
string again: %(string)s

Countinue''' % {'num':num,'string':string }
```

or this?

```

num = 11
string = 'a long string'
'''Testing Multiline Code
num: '''+str(num)+''',
string: '''+string+'''
num again: '''+str(num)+''',
string again: '''+string+'''

Countinue'''
```

if there's a better solution so please tell me because I'm kinda new to python.

thanks.

---

### Post by jimi_hendrix on 2009-05-15
if one is faster, the difference would be so small its not relevent

---

### Post by simeon87 on 2009-05-15
> "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil."

And rightly so.

---

### Post by arikshtiv on 2009-05-15
o-k...

---

### Post by simeon87 on 2009-05-15
> **arikshtiv said:**
> o-k...

To answer your question, we don't know but we don't think it matters for the speed of the application.

What matters is what type of algorithms that you're using (see [http://en.wikipedia.org/wiki/Computational_complexity_theory#Analysis](http://en.wikipedia.org/wiki/Computational_complexity_theory#Analysis)), how your application is designed, etc.

---

### Post by nvteighen on 2009-05-16
I really doubt there can be any difference... Maybe, but just maybe using **str()** may be slower because you're calling an object method (the built-in **__str__** method) in order to get the string representation of something.

But again, it's irrelevant. Specially in high-level languages like Python, you shouldn't care for that kind of optimizations, but better algorithms. If you were coding in C, the story could be different...

---

### Post by scooper on 2009-05-16
I completely agree that getting large scale algorithms right is far more useful than adapting small scale coding style for performance.  I'll take readable code over a 5% performance gain any time.  Write code for clarity and then tweak on an as-needed basis.

That said, Python cookbooks seem to imply that repeated string concatenation is always slower than the formatting operator, because non-mutable Python strings get repeatedly copied.  The format operator or join method just make one pass.

If performance is that critical you can always write some C code to handle the most critical parts.

BTW - you can use a dict constructor to simplify the formatting operation slightly.

```
num = 11
string = 'a long string'
'''Testing Multiline Code
num: %(num)i,
string: %(string)s
num again: %(num)i,
string again: %(string)s

Countinue''' % dict(num=num,string=string)
```

---

### Post by Claus7 on 2009-05-16
Hello,

just check it out for yourself. Yet, as someone mentioned, I do not think that it will have a huge difference. So, save these two as:
script1.sh
script2.sh

and then make them executable (chmod 755 name_of_script)

Then for each one do:
time ./name_of_script

When you do so, it will be nice to close any other application that might be running. And judge from the output you will get.

Regards!

---

### Post by snova on 2009-05-16
If you really want to know, take a look at the **timeit** module and test each one. But as it has been said, why care? Use whichever one looks cleaner.

Personally I think the first one looks nicer. It is also slightly better because the second one (using concatenation) has to copy everything to a new string for each + operator.

---

### Post by Martin Witte on 2009-05-16
Maybe [this document]("http://wiki.python.org/moin/PythonSpeed/PerformanceTips#StringConcatenation") helps

---

### Post by imdano on 2009-05-16
Method two is faster on my machine:

```
>>> import timeit
>>> setup = """num = 11
... string = 'a long string'
... """
>>> s1 = """'''Testing Multiline Code
... num: %(num)i,
... string: %(string)s
... num again: %(num)i,
... string again: %(string)s
... 
... Countinue''' % {'num':num,'string':string }"""
>>> s2 = """'''Testing Multiline Code
... num: '''+str(num)+''',
... string: '''+string+'''
... num again: '''+str(num)+''',
... string again: '''+string+'''
... 
... Countinue'''"""
>>> timeit.timeit(s1, setup)
4.493513822555542
>>> timeit.timeit(s2, setup)
2.2985599040985107
>>> 
```

I wouldn't be surprised if the results changed for either a high number of concatenations or concatenations involving really long strings, though.

---

### Post by arikshtiv on 2009-08-01
And for all those saying it doesn't matters, it does because as you see in imdano's results the second one is twice as fast.

and on my computer(ubuntu) the first one was about 6sec and second was 3sec.

so both results show that the second type is faster.

---

### Post by Mirge on 2009-08-01
Don't know Python (yet)... but here are my results:

```

mike@mike-kubuntu:~$ time python test1.py ; time python test2.py

real    0m0.038s
user    0m0.024s
sys     0m0.016s

real    0m0.040s
user    0m0.020s
sys     0m0.016s
mike@mike-kubuntu:~$ time python test1.py ; time python test2.py

real    0m0.037s
user    0m0.020s
sys     0m0.020s

real    0m0.036s
user    0m0.028s
sys     0m0.008s
mike@mike-kubuntu:~$ time python test1.py ; time python test2.py

real    0m0.038s
user    0m0.024s
sys     0m0.016s

real    0m0.038s
user    0m0.032s
sys     0m0.004s
mike@mike-kubuntu:~$

```

test1.py is the first script, test2.py is the second script (see OP)...

---

### Post by MadCow108 on 2009-08-01
> **arikshtiv said:**
> And for all those saying it doesn't matters, it does because as you see in imdano's results the second one is twice as fast.

and on my computer(ubuntu) the first one was about 6sec and second was 3sec.

so both results show that the second type is faster.

it all depends on the application
the timeit module excutes it a million times so there's a major difference.
but if its only a small part of your application this doubling in speed can very well be irrelevant. (e.g. the algorithm that calls this snippet a million times takes a minute, then 2 seconds speed up doesn't matter much)
The time optimising that part may be put to better use in other places.

---

