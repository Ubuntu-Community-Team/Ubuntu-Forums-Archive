---
title: "C++ rand()"
date: 2014-11-26
forum: Programming Talk
---

### Post by cb2494 on 2014-11-26
Hey everyone,

I'm new to Ubuntu in general, but also c++ programming. To learn I'm messing around with simple loops and functions. When trying to generate random numbers though it always submits "0." Any help is welcome and appreciated. I'm currently using code::blocks.

Thanks in advance,
Chris

---

### Post by steeldriver on 2014-11-26
Hello and welcome to the forums

It's going to be hard for anyone to help you unless you post a minimal snippet of your code

---

### Post by 3246251196 on 2014-11-28
I find it unlikely, but there is a chance that rand() is always returning 0 when you stop/start the program. It returns anything from 0 to some value which can change depending on the environment. But, unless you use srand() and give, as a parameter, some different value each time the sequence of randomly generated values will be the same every time you start the program.

As said, it is hard to know without looking at the code.

---

