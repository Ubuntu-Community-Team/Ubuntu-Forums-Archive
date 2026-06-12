---
title: "[C++]  GNU C++ Profiler"
date: 2010-12-04
forum: Programming Talk
---

### Post by lucasart on 2010-12-04
Hello,

Let's assume we're in the directory where all my *.h and *.cpp files are, then a simple
```

g++ -o myprog *.cpp

```works fine and produces an executable called myprog.

Now if I want to create information for the GNU C++ profiler gprof, I've read somewhere that I should to
```

g++ -p -o myprog *.cpp

```but it doesn't seem to work as it doesn't create the file gnom.out that has the profiling info.

Does anyone know what the correct syntax is to produce the gnom.out file ?

thank you

---

### Post by dwhitney67 on 2010-12-04
You need to _run_ the program before the gmon.out file is generated.

```

g++ -p -o myprog *.cpp

./myprog

gprof ./myprog

```

---

### Post by lucasart on 2010-12-04
> **dwhitney67 said:**
> You need to _run_ the program before the gmon.out file is generated.

```

g++ -p -o myprog *.cpp

./myprog

gprof ./myprog

```

Thank you so much!

Profiling is a very valuable thing for what I'm currently programming. It's so simple, I feel silly not to have tried that.

I already managed to reduce the exec time by 35% with only minor code changes !! and more to come :)

=> 39.3% now ! woaw !!

---

### Post by Queue29 on 2010-12-04
> > **lucasart said:**
> 
I already managed to reduce the exec time by 35% with only minor code changes 

You may be interested in the -O3 switch. Those minor code changes are pointless; the compiler is capable of optimizing code for you, almost always better than what you can do manually.

---

### Post by schauerlich on 2010-12-04
> **Queue29 said:**
> You may be interested in the -O3 switch. Those minor code changes are pointless; the compiler is capable of optimizing code for you, almost always better than what you can do manually.

But when you're doing school assignments where you're not allowed to use -O3 and you're graded on speed, it's very useful. :) And anyways, when you're learning it's good to see what sort of things you CAN do to speed it up, so you have a better appreciation of what's going on in the "black box" of the compiler.

---

### Post by lucasart on 2010-12-04
> **Queue29 said:**
> You may be interested in the -O3 switch. Those minor code changes are pointless; the compiler is capable of optimizing code for you, almost always better than what you can do manually.

Thank you so much, I was naively thinking that it was a default behaviour to optimize the code.

Indeed I was expecting some inlining to lead to a lot of loop invariants optimization, and it wasn't happening! It's good because I can keep my code simple, knowing that the O3 will do what I would otherwise do manually, thereby making the code longer and harder to read and more error prone.

Now with O3, my code is 8.2 times faster than the first version (before using O3 and doing some manual optimizations): woaw !

Just to give you an idea, I'm currently writing a chess engine. I've only done the board representation and move generator. I've benchmarked it generating all the moves for a given position at depth 5, and it ran through 125 million positions in only 14 seconds! It's simply amazing, considering that it has to compue a lot of things, such as material scores, pinned pieces, attaqued square for both sides and so on.

However I did create some manual optimizations which beat O3, and those are of two kinds:
1/ places where the optimizer just can't do anything for me. the only way to optimize is to know the rules of chess, and therefore not ask for useless cases to be considered etc.
2/ places where the optimizer should do the job itself, but my improvements are very small in that area.

---

### Post by lucasart on 2010-12-04
> **Queue29 said:**
> You may be interested in the -O3 switch. Those minor code changes are pointless; the compiler is capable of optimizing code for you, almost always better than what you can do manually.

Another thing I've always been wondering. Using the optimizer, should I even bother to use the inline keyword where appropriate, or is it pointless ?

---

