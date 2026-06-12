---
title: "Advanced Challenges???"
date: 2008-08-05
forum: Programming Talk
---

### Post by slavik on 2008-08-05
I have a quadcore system with 8GB of RAM (700MB is being used by my entire system under regular load, leaving 7GB with headroom to one program).

One person asked about advanced challenges.

We could definitely have those.

The advanced challenges would probably involve something close to scientific computing (the simple stuff) like finding prime numbers (upto a point and using something other than the well known brute force method), multiplying large matrices (something along the lines of 10000 by 10000), tensor product, some others that I haven't thought of.

In these challenges though, speed would be taken into consideration. But speed not as in who is 5 seconds faster in a 2 minute program, but which program is 2 or 3 times faster and such. In other words, parallel programs are encouraged.

The specification of the challenges would be the following:
- input is specified (specially named files or stdin, depending on the challenge), no error checking for input is needed
- output will also be specified (either file or stdout)
- a (smaller than the actual test) sample input and the resulting output given (so you can test the correctness of your code)
- at the end, I will post my own code as well as the stats of everyone's code (programs will be run with the time command and possibly with different size inputs to create some nice graphs).

**EDIT:**
- the code is only allowed to depend on libraries available in the Ubuntu Hardy Heron repositories.

Questions/comments/complaints?

---

### Post by LaRoza on 2008-08-05
What is the question?

For advanced challenges, perhaps someone can continue the "old" line. Lster? Where are you?

---

### Post by slavik on 2008-08-05
> **LaRoza said:**
> What is the question?

For advanced challenges, perhaps someone can continue the "old" line. Lster? Where are you?
well, that is my proposal :)

---

### Post by LaRoza on 2008-08-05
> **slavik said:**
> well, that is my proposal :)

Well, start one and see if they are popular :-)

---

### Post by tamoneya on 2008-08-05
advanced doesnt necessarily mean resource intensive.  It would be more "advanced" if you made your program more efficient.

---

### Post by sisco311 on 2008-08-05
Solving the Rubik's Cube?

---

### Post by slavik on 2008-08-05
> **sisco311 said:**
> Solving the Rubik's Cube?
that's a good idea. :)

> **tamoneya said:**
> advanced doesnt necessarily mean resource intensive.  It would be more "advanced" if you made your program more efficient.
I never said that it will be resource intensive, but sometimes in order to test efficiency of something, you have to give it lots of stuff to do. :) (ie: finding out 10! is going to separate average code from really good code).

---

### Post by tamoneya on 2008-08-05
that would be a fun one.  What is the best benchmarking tool that works cross language. 

Just to be on the record I say the best way to solve that problem(large factorials) is with the gamma function: [http://mathworld.wolfram.com/GammaFunction.html](http://mathworld.wolfram.com/GammaFunction.html)

---

### Post by lisati on 2008-08-05
> **sisco311 said:**
> Solving the Rubik's Cube?
If you want some ideas for this one, check [here]("http://wrongway.org/cube/solve.html")

---

### Post by slavik on 2008-08-05
> **tamoneya said:**
> that would be a fun one.  What is the best benchmarking tool that works cross language. 

Just to be on the record I say the best way to solve that problem(large factorials) is with the gamma function: [http://mathworld.wolfram.com/GammaFunction.html](http://mathworld.wolfram.com/GammaFunction.html)
write code and time it. :)

---

### Post by dnzz on 2008-08-05
s

---

### Post by pmasiar on 2008-08-05
I have hard time to imagine that people with skills capable of solving that kind of problems have free time to waste on them - maybe competition should be in number of patches submitted to any ubuntu-related (or even non-related) project?

I am not that kind of expert, but if I had time I would have no problem to find a challenge worth solving.

Just opinion, feel free to publish and solve any tasks you wish. But IMNSHO only beginner has problem to find task worth solving (and within a reach), that's all.

---

### Post by Torajima on 2008-08-05
Well.. you could always try doing the beginner challenges, and see how few lines of code you can do them in (preferably without resorting to a bunch of semi-colons)

I did the second beginner challenge in only two lines (although I cheated... no error testing).

---

### Post by Wybiral on 2008-08-06
It's kind of discriminative... Not everyone has an awesome computer to waste cycles on. Even better would be if the proper, elegant solution, didn't use that much CPU whereas the naive solutions are nearly impossible (like some of project euler).

> **slavik said:**
> (ie: finding out 10! is going to separate average code from really good code).

```

from operator import mul
fact = lambda x: reduce(mul, xrange(1, x + 1))
print fact(10)

```

---

