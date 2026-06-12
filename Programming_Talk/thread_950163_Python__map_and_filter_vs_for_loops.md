---
title: "Python : map and filter vs for loops"
date: 2008-10-16
forum: Programming Talk
---

### Post by Siph0n on 2008-10-16
I am trying to learn about map and filter in python, and I don't see a difference between them and for loops

```

def f(x): return x % 2 != 0 and x % 3 != 0
filter(f, range(2, 25))

```

vs

```

a = []
for i in range(2,25):
    if i % 2 != 0 and i % 3 !=0:
        a.append(i)

```

and


```

def cube(x): return x*x*x
map(cube, range(1, 11))

```

vs

```

a = []
for i in range(1, 11):
    a.append(i*i*i)

```

I see that using filter and map are a couple of lines smaller, but which ones are better to use, and why??? 
Thanks!!

---

### Post by pmasiar on 2008-10-16
That's correct, list comprehension is more modern (in Python) and more procedural-like way to do stuff usualy done in a functional way, like map().

Be happy and use list comprehension instead 8-)

---

### Post by unutbu on 2008-10-16
The underlying implementation of map and filter are different than loops, even though they accomplish the same thing. Which idiom runs fastest can change from version to version.
Right now I think list comprehensions are the fastest.

So instead of
```

filter(f, range(2,25)),

```
the list comprehension would be
```

[x for x in range(2,25) if f(x)]
```

and instead of 
```

map(cube, range(1, 11))
```

the list comprehension would be
```

[cube(x) for x in range(1,11)]

```

You might also find this article by Guido Rossum interesting:
[http://www.artima.com/weblogs/viewpost.jsp?thread=98196](http://www.artima.com/weblogs/viewpost.jsp?thread=98196)

---

### Post by Can+~ on 2008-10-17
Also, instead of

[PHP]x*x*x[/PHP]

use

[PHP]x**3[/PHP]

(base**exponent)

---

