---
title: "BASH: quick conditional statement problem"
date: 2010-02-12
forum: Programming Talk
---

### Post by derelict888 on 2010-02-12
I've got a problem with a conditional statement in one of my while loops, bad syntax I'm sure;

```
 while [ "$c" <= "$j" ] ; do
```

I want the statement to work like "while var c is less than or equal to var j, continue. This statement is getting passed to a host via SSH (if that might change how to write this out).

Thanks for any help, the rest of my code is fine since I've tested it, I've got just this conditional wrong.

---

### Post by m_duck on 2010-02-12
I think where you have <= it should be -le:
```
while [ "%c" -le "$j" ]; do
```

[Bash comparisons]("http://tldp.org/LDP/abs/html/comparison-ops.html")

---

### Post by derelict888 on 2010-02-12
> **m_duck said:**
> I think where you have <= it should be -le:
```
while [ "%c" -le "$j" ]; do
```

[Bash comparisons]("http://tldp.org/LDP/abs/html/comparison-ops.html")

Great that did it ty.

---

