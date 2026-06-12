---
title: "a quick java syntax question"
date: 2008-12-28
forum: Programming Talk
---

### Post by babacan on 2008-12-28
I am trying to understand a java code however stucked at a point where I don't know what this stands for:

```
        int x = (y > 0) ? 1 : -1;
```

I will be greatful is someone explains this notation.

cheers.

---

### Post by _duncan_ on 2008-12-28
if y is greater than 0 then x gets the value +1, else x = -1.

---

### Post by Ruhe on 2008-12-28
It's called [Ternary operation]("http://en.wikipedia.org/wiki/Ternary_operation")

---

### Post by slavik on 2008-12-28
I believe it was first seen in C.

Basically, this is a cut down version of the if..else statement. and the result of the statement goes into x. the result being 1 if the condition is true and -1 otherwise.

---

