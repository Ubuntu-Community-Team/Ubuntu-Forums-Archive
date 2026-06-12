---
title: "will a quad core make my code run faster?"
date: 2008-03-24
forum: Programming Talk
---

### Post by clockwork_alex on 2008-03-24
hi everyone,
I'm writing a program that uses the processor quite intensely. It's gotten to the point where it simply takes too long to be practical and I'm wondering how an upgrade to a quad core would improve
performance (I'm on an intel dual core 1.6Ghz).
I'm still quite new to programming and don't know how to handle threads and the likes. Will my code compiled and ran on a quadcore setup run noticeably faster without needing to change it? (oh and it's C code compiled on gcc)

thanks in advance,
Daniel

---

### Post by LaRoza on 2008-03-24
Is it worth buying a new processor?

It probably won't make a difference. If it is already compiled for the architecture, you don't need to recompile it.

---

### Post by CptPicard on 2008-03-24
The first thing is to always consider whether switching your algorithm would make a difference. Exponential time approaches in particular are often just hopeless no matter how much hardware you throw at them.

To answer your question; no, switching to quad-core will not make a difference. You need to parallelize your solution by making use of threads in order to make use of multi-core processing.

---

### Post by newtonfn on 2008-03-24
No, it won't run any faster. The only way to make it run faster in a multiprocessor environment is to make the program multi threaded. If you don't tell a program to use more than one processor, it will always will use one and only one processor. (and make it multi thread is the way to tell the OS to use more than one processor)

To make it faster changing hardware you must buy a faster processor (a 1.6hz quad-core have the same speed as 1.6 dual-core and also a single core. But a 2.0 single-core es faster than the others.)

Multi-core technology only helps to execute more than one applications at the same time (or applications thats make good use of multiple process and threads)

If I were you, i will be thinking about optimizing code before changing the hardware. (sometimes you have no choice other than change hardware or to be really really patience)

Sorry about my English.

---

### Post by clockwork_alex on 2008-03-24
thanks for the fast replies!
I also agree that optimizing the code is the priority. It's just that I'd like to know that if I am not able to optimize it enough I can always get it done by means of an upgrade. Considering that more cores won't do a thing I'll just have to get a faster dual core if it comes to  that (I won't actually buy them, I have the opportunity to simply borrow them for a while).
And I see that I have to learn about threads right away because from what I gathered from your responses I'm only using a single core as it is!

BTW LaRoza and CptPicard, awesome pics, TNG FTW !!

---

### Post by LaRoza on 2008-03-24
> **clockwork_alex said:**
> 
BTW LaRoza and CptPicard, awesome pics, TNG FTW !!
Resistance is futile. 

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]

(Yes, non threading applications will use one core. The use of multiple cores is good for more than one process, or for multithreaded applications)

---

### Post by Fbot1 on 2008-03-24
Not with gcc or other practical C compilers as far as I know.

---

### Post by CptPicard on 2008-03-24
Data-Parallel Haskell looks really promising though -- pure-functional stuff is automagically parallelizable by the compiler. I'm seriously looking at it at the moment because most of the things I write professionally are easily expressible in terms of data-parallelized transformations of input vector, with very little to be done in terms of difficult algorithms... you just have to crunch all the numbers...

---

### Post by LaRoza on 2008-03-24
> **clockwork_alex said:**
> 
BTW LaRoza and CptPicard, awesome pics, TNG FTW !!

We both got them from PrivateVoid, good at image manipulations :-)

---

