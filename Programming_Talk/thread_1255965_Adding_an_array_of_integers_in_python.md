---
title: "Adding an array of integers in python"
date: 2009-09-02
forum: Programming Talk
---

### Post by joeyyy on 2009-09-02
Hello everyone,

Im still a newbie to python so bear with me, i'm trying to add an array of integers in python...

At the moment, my python script is looking like this:
```

x = open("chocin.txt", "r")

y = open("chocout.txt", "w")

x = x.read()
x = x.split()
p = map(int,x)

x = len(x.readlines()

```

As you can see, i'm inputting a list of numbers, converting that to a string, converting that to an array and converting that to an integer-filled array so that if i go:
x = p[0] + p[1]
it will add the first integer and the second one after the comma

I'm just trying to simply add all the integers and google isnt working Sad

Heaps of thanks in advance,

Joe

---

### Post by Arndt on 2009-09-02
> **joeyyy said:**
> Hello everyone,

Im still a newbie to python so bear with me, i'm trying to add an array of integers in python...

At the moment, my python script is looking like this:
```

x = open("chocin.txt", "r")

y = open("chocout.txt", "w")

x = x.read()
x = x.split()
p = map(int,x)

x = len(x.readlines()

```

As you can see, i'm inputting a list of numbers, converting that to a string, converting that to an array and converting that to an integer-filled array so that if i go:
x = p[0] + p[1]
it will add the first integer and the second one after the comma

I'm just trying to simply add all the integers and google isnt working Sad

Heaps of thanks in advance,

Joe

Maybe 'for' can be used.

---

### Post by geirha on 2009-09-02
List comprehension
```

p=[int(x) for x in file("chocin.txt")]
print sum(p)

```

---

