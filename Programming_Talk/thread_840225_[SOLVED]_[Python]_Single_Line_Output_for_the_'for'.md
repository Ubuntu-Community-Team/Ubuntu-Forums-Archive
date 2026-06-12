---
title: "[SOLVED] [Python] Single Line Output for the 'for' loop"
date: 2008-06-25
forum: Programming Talk
---

### Post by navneeth on 2008-06-25
This segment in Python
```
for i in range(0,10):
    print i
```

produces the same result as this piece of code in C++
```
for(i=0;i<10;i++)
   cout<<i<<"\n";
```

What should I do in Python to get the output similar to that in C++ but without the newline character? (0123456789)

Thanks

---

### Post by CptPicard on 2008-06-25
This is a slightly obscure bit of Python, but what you essentially do is 

```

print x,

```

The comma omits the newline.

---

### Post by Wybiral on 2008-06-25
```

from sys import stdout

stdout.write("Hello ")
stdout.write("world!")

```

Or, just join all your strings together and print them that way...

```

print "".join(str(i) for i in xrange(10))

```

---

### Post by ghostdog74 on 2008-06-25
```

>>> print ''.join(map(str,range(10)))
0123456789

```

---

### Post by slavik on 2008-06-25
wrong thread

---

### Post by navneeth on 2008-06-25
> **CptPicard said:**
> This is a slightly obscure bit of Python, but what you essentially do is 

```

print x,

```

The comma omits the newline.

> **Wybiral said:**
> ```

from sys import stdout

stdout.write("Hello ")
stdout.write("world!")

```

Or, just join all your strings together and print them that way...

```

print "".join(str(i) for i in xrange(10))

```

> **ghostdog74 said:**
> ```

>>> print ''.join(map(str,range(10)))
0123456789

```

Great! Thank you, all. I learnt a couple of new things, as well. :)

---

### Post by pmasiar on 2008-06-25
Using single print function, and joined arguments, is also slightly more effective: 

1) joining list uses less memory reallocation (especially compared to += accumulation)
2) uses just single I/O call.

---

