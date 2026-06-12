---
title: "Codelite g++ 64 bit compile"
date: 2010-11-19
forum: Programming Talk
---

### Post by lucasart on 2010-11-19
hello

i'm writing C++ code using codelite and g++ (installed CodeLite from the Ubuntu 10.10 repositries).

how do i compile the program for amd64 ?#

i tried to add -m64 to g++ -c command but it doesn't seem to work as sizeof(int) still equals 4.

thank you

---

### Post by Foxcow on 2010-11-19
Not sure how from that ide but you can compile using the terminal and g++.


in the terminal
```


g++ thenameofyourprogram.cpp


```

If you're running on a 64 bit machine, it will be compiled as such.  If I'm not mistaken...  I'm relatively new to the game.

---

### Post by spjackson on 2010-11-19
> **lucasart said:**
> 
i tried to add -m64 to g++ -c command but it doesn't seem to work as sizeof(int) still equals 4.

On amd64, sizeof(int) is 4.

---

### Post by lucasart on 2010-11-19
> **spjackson said:**
> On amd64, sizeof(int) is 4.

thanks, i naively assumed it would be 8.

---

### Post by Arndt on 2010-11-19
> **lucasart said:**
> thanks, i naively assumed it would be 8.

sizeof(long) is probably 8, though.

---

### Post by Queue29 on 2010-11-20
> **Arndt said:**
> sizeof(long) is probably 8, though.

Indeed it is. So is type long long.

---

