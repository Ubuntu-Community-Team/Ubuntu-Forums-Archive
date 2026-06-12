---
title: "Noob python question about lists"
date: 2007-08-22
forum: Programming Talk
---

### Post by triptoe on 2007-08-22
hey I have a problem..

I have a list and i want to make 6 lists inside of it (actually more)

when i declare it like this:

```
list = [[1],[1],[1],[1],[1],[1]]
```

it works fine... BUT when i do this

```
list = [[1]] * 6
```

it makes 6 lists inside of it, however when i modify each element with append... instead of adding a value to the individual index, it adds it to each one!! for instance:

```
list[0].append(1)
```

will look like this: ([1,1],[1,1],[1,1],[1,1],[1,1],[1,1]

but in the first method it looks like this: ([1,1],[1],[1],[1],[1],[1])

any ideas what is going on ?

---

### Post by ghostdog74 on 2007-08-22
firstly, don't use "list" as  a variable name, because list is a builtin function used by Python. secondly, this is a common problem. I leave it to you to read the docs for explanation , however, the solutoin to your problem is to make a copy
```

>>> a = [ [1],[1] ]
>>> b=a[:]
>>> b[0] = [2]
>>> 
>>> b
[[2], [1]]
>>> a
[[1], [1]]
>>> 

```
also check out the deepcopy() function.

---

### Post by pmasiar on 2007-08-22
"[[1]] * 6" does exactly what you told it: create list, and make 6 copies of reference to it. "handle" of anonymous list reference like any other object, so you have 6 references to the same object [1].

---

### Post by triptoe on 2007-08-22
> **pmasiar said:**
> "[[1]] * 6" does exactly what you told it: create list, and make 6 copies of reference to it. "handle" of anonymous list reference like any other object, so you have 6 references to the same object [1].

ahh that explains it.

---

