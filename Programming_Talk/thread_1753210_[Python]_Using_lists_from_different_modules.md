---
title: "[Python] Using lists from different modules"
date: 2011-05-08
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-08
I'm building a program and would like to use a list I have build in a module.

```
def function:
. . . Code to build list. . . pow[] and off[]

print pow
print off

```

The code says that off is not defined. Any idea what is going on?

---

### Post by cgroza on 2011-05-08
def module?
You are declaring a function there.

---

### Post by ki4jgt on 2011-05-08
> **cgroza said:**
> def module?
You are declaring a function there.

Yeah sorry, LOL busy and didn't pay attention to what I was writing :-(

---

### Post by ki4jgt on 2011-05-08
Nevermind. . . Just declared global worked great. . .

---

### Post by Tony Flury on 2011-05-09
Avoid Globals if you can - wrap your lists in a class is a much better idea.

or have two functions - which return each list.

Or have one function that returns the two lists in a single return.

---

### Post by simeon87 on 2011-05-09
Don't you just want to import the function from that module?

```
from modulename import functionname
```

---

