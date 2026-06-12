---
title: "print powers of 2"
date: 2012-02-05
forum: Programming Talk
---

### Post by conradin on 2012-02-05
Hi all, I wan to print the powers of 2 which this python script does. (I'm learning python)
Im looking to simplify this: 

```
#!/usr/bin/env python
import math
n = 0

while n < 100:
    parents = pow(2, n)
    print 'This generation has %d parents' % parents
    n = (n + 1)
```

anyone have some tips or ideas?

---

### Post by Barrucadu on 2012-02-05
Try using a for loop.

---

### Post by trent.josephsen on 2012-02-05
Powers are built into Python with the ** operator, so you don't have to use pow.

print 2**100

---

### Post by conradin on 2012-02-05
The ** shorten this up a bit! I'm not really sure what sort of loop could 
simplify or even otherwise improve this little script.
```
#!/usr/bin/env python
n = 0
while n < 100:
    print 'Two to the %d, '% n, ' is %d' % 2**n
    n = (n + 1)
```

---

### Post by ve4cib on 2012-02-06
Generally when you know exactly how many times you want to loop through a block of code you use a for-loop instead of a while-loop.  While loops are great for situations where you think "I need to keep doing this until ____" and a for-loop is great for "I need to do this exactly X times."  Your code is an example of the latter.

```
for n in range(100):
    print '2 to the {0}th power = {1}'.format(n,2**n)
```

will print out 2^0, 2^1, 2^2, ..., 2^99.  The string.format function does the same kind of thing as "%d", but uses positional arguments.  The "{0}" will be replaced with the first argument, "{1}" with the second, and so on.

---

### Post by trent.josephsen on 2012-02-06
It didn't occur to me until just now, but the .format() method ve4cib uses is a more Pythonic way than the old % style string formatting, which I think is gone in Python 3 (correct me if I'm wrong)?

---

### Post by Bachstelze on 2012-02-06
> **trent.josephsen said:**
> It didn't occur to me until just now, but the .format() method ve4cib uses is a more Pythonic way than the old % style string formatting, which I think is gone in Python 3 (correct me if I'm wrong)?

Nope, it's still there. (Which is good because it's the only method I know. :p)

---

### Post by ve4cib on 2012-02-06
> **trent.josephsen said:**
> It didn't occur to me until just now, but the .format() method ve4cib uses is a more Pythonic way than the old % style string formatting, which I think is gone in Python 3 (correct me if I'm wrong)?

I believe I read somewhere that the % formatting is going to be deprecated (if it isn't already) and will eventually be dropped.  But there may have been subsequent discussion and they decided not to drop it.

format() is actually pretty cool, because you can use keyword arguments as well as positional ones:

```
for i in range(100):
    print "2 to the {n}th power = {result}".format(n=i,result=2**i)
```

works the same way as with the {0} and {1}.  But this way the string being formatted looks a little cleaner and if you have a LOT of things to substitute in, like in an XML or JSON string for example, it's clearer what values go where.

---

### Post by conradin on 2012-02-06
> **ve4cib said:**
> Generally when you know exactly how many times you want to loop through a block of code you use a for-loop instead of a while-loop.  While loops are great for situations where you think "I need to keep doing this until ____" and a for-loop is great for "I need to do this exactly X times."  Your code is an example of the latter.

```
for n in range(100):
    print '2 to the {0}th power = {1}'.format(n,2**n)
```

will print out 2^0, 2^1, 2^2, ..., 2^99.  The string.format function does the same kind of thing as "%d", but uses positional arguments.  The "{0}" will be replaced with the first argument, "{1}" with the second, and so on.

Ah The format bit is good ve4cib! The % bits I got were from the beginer tutorials on the python website. Im interested, where should I go for more python tutorials?

---

### Post by Arndt on 2012-02-06
> **conradin said:**
> The ** shorten this up a bit! I'm not really sure what sort of loop could 
simplify or even otherwise improve this little script.
```
#!/usr/bin/env python
n = 0
while n < 100:
    print 'Two to the %d, '% n, ' is %d' % 2**n
    n = (n + 1)
```

Instead of computing successive powers of 2, you can keep the latest value and then multiply it with 2 next time round.

---

### Post by conradin on 2012-02-06
Im thinking 2 -3 lines is as good as it will get!
Thank you everyone for helping me write cleaner code!

---

