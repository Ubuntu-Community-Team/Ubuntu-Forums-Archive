---
title: "gcc errors"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-15
Hi,,
i get this error when i compile:

```
raed@raed-laptop:~/Desktop/raed/TTL$ gcc -o test hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```any hints???
thanx

---

### Post by iaculallad on 2008-07-15
> **raedbenz said:**
> Hi,,
i get this error when i compile:

```
raed@raed-laptop:~/Desktop/raed/TTL$ gcc -o test hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```any hints???
thanx

Try installing the essential files:

```
sudo apt-get install build-essential
```

---

### Post by elgoog on 2008-07-15
Worked Fine

---

### Post by Joeb454 on 2008-07-15
It's usually the case, I mean I even forgot to install it yesterday on a fresh install, and I do programming (in C) as well as compiling!

---

