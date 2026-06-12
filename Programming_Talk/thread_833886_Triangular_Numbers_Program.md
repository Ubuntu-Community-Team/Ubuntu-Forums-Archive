---
title: "Triangular Numbers Program"
date: 2008-06-19
forum: Programming Talk
---

### Post by Semong on 2008-06-19
I'm trying to learn how to program and have been given the task of writing a program in Python that displays triangular numbers in tabular form ie:

```

>>>print_triangular_numbers(5)
1       1
2       3
3       6
4       10
5       15

```

The code below determines the nth triangular number but I just seem to grasp the concept of wrapping it into a function that produces the above output. Any and all guidance would be greatly appreciated.

```

 def tri(n):
    if n<=1: return n
    else: return n + tri(n-1) 

```

---

### Post by NovaAesa on 2008-06-19
You probably want something like this:
```

def ptn(n):
    for x in range(n):
        print "%s %s" % (x, tri(x))

```

Something like that anyway. It's been a while since I've used Python.

---

### Post by Joe Y-lee on 2008-06-19
This is the function your looking for:

```

def tri(n):
    i = 1
    while i <= n:
        print i, i * (i + 1) / 2, '\t'
        i += 1
        print

```

---

