---
title: "How to compile C program using GCC so that I can use GDB?"
date: 2008-03-01
forum: Programming Talk
---

### Post by amazingjxq on 2008-03-01
I just know this: gcc -o xxx xxx.c
But it seems that something is wrong when I debugging it.

---

### Post by loell on 2008-03-01
```
gcc  -g -o xxx xxx.c
```

or rather 

```
gcc  -ggdb -o xxx xxx.c
```

---

### Post by amazingjxq on 2008-03-01
OK,thx!

---

