---
title: "Python timing"
date: 2009-08-20
forum: Programming Talk
---

### Post by CrazyMonkeyFox on 2009-08-20
I have been writing quite a few small python scripts lately, and I am interested in finding out the time it takes for these scripts to execute. I am aware of the time module, but unsure how to implement it, also whether its the most reliable or not.

I include a script that gets the sum of all primes below 2 million here. If I wanted to time it, how would I go about it? 

```
#!/usr/bin/env python

def isprime(n):
    for x in range(2, int(n**0.5)+1):
        if n % x == 0:
            return False
    return True

sum = 0

for i in range (3, 2000000, 2):
    if isprime(i) == True: sum += i

sum = sum + 2
print sum
```Thanks in advance :)

---

### Post by pepperphd on 2009-08-20
you@computer$ time pythonscript.py

---

### Post by CrazyMonkeyFox on 2009-08-20
> **pepperphd said:**
> you@computer$ time pythonscript.py


I was kind of looking for an in-script way of doing it. I am aware of that method, but thanks anyway.

---

### Post by unutbu on 2009-08-20
Check out the print_timing decorator:

[http://www.daniweb.com/code/snippet368.html#](http://www.daniweb.com/code/snippet368.html#)

And if you use IPython, you might also like its builtin timeit function:

[http://scienceoss.com/test-the-speed-of-your-code-interactively-in-ipython/](http://scienceoss.com/test-the-speed-of-your-code-interactively-in-ipython/)

---

### Post by smartbei on 2009-08-21
You can use python's basic time functions and create your own.
```

import time
t1 = time.time()
EXECUTE_FUNC()
print time.time() - t1

```
Of course, you can stick that in a function, make it execute the function a large number of times, average it out, etc.

---

