---
title: "gcc / g++ increasing stack size"
date: 2011-05-06
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-06
In windows, visual c++ has a pragma which can be used to increase the function stack size. And in linux, this can be done by giving compiler options, but is it possible to do it from inside the code? like the way vc did?

I need to know it, because heavy recursions and long depth dfs calls get Runtime Errors because of stack overflow :(

---

### Post by Phenax on 2011-05-06
[http://linux.die.net/man/2/setrlimit](http://linux.die.net/man/2/setrlimit)

---

### Post by zobayer1 on 2011-05-06
wow, nice, thanks :):KS

---

### Post by schauerlich on 2011-05-06
> **zobayer1 said:**
> I need to know it, because heavy recursions and long depth dfs calls get Runtime Errors because of stack overflow :(

Increasing the stack size might alleviate the problem temporarily, but it's just delaying it until the problem grows again. It's probably best to find some way of converting your algorithm to a tail recursive or iterative algorithm.

---

### Post by zobayer1 on 2011-05-06
Sometimes writing iterative algorithms seems difficult to me, instead, recursions are so clear to visualize... That's why I asked :)

---

