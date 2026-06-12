---
title: "An IDE that automaticly determines big O?"
date: 2013-01-26
forum: Programming Talk
---

### Post by faceshed on 2013-01-26
I was just thinking how cool it would be to see what the run time efficiency of a function is before I decide to call it up.

Is there any language or IDE or plugin for a IDE that comepiles data on efficiency as you program?

---

### Post by CptPicard on 2013-01-26
As purely static code analysis, that is impossible to do (it would require being able to solve the halting problem, which is known to be impossible).

Empirically speaking, look at profilers. They gather execution time information as you run your program. With various sizes of inputs, you get an idea of the class of the runtime complexity of the program.

---

### Post by trent.josephsen on 2013-01-26
It's impossible to solve the general problem, but it would still be possible to do static analysis on many algorithms to find their efficiency, both in memory and time. (Memory would probably be easier.)

In practice, though, big-O doesn't often tell you very much. I imagine the feature would be used mostly as a curiosity (and to help CS students cheat on their homework).

---

### Post by CptPicard on 2013-01-26
> **trent.josephsen said:**
> It's impossible to solve the general problem, but it would still be possible to do static analysis on many algorithms to find their efficiency, both in memory and time. (Memory would probably be easier.)

It would be interesting to know how easily you run into the "general case" here, and if you can actually know if you're within the special cases you can handle, before actually trying. Infinite loops as bugs are rather common, at least; but on second thought I guess you could run that kind of an analyzer on code that you know to be correct, and if it just hangs, you know you probably have a bug...

Memory analysis is probably quite connected to runtime analysis, as you mostly allocate things depending on how the execution of the algorithm proceeds.

---

### Post by trent.josephsen on 2013-01-26
I've always kind of wondered about that. I imagine you wouldn't often run into the halting problem with most real-life code, but that doesn't mean it would be easy to write a program capable of analyzing any code that can be analyzed, let alone figuring out whether the code it's looking at is in that category...

Actually, I think that determining whether a particular piece of code is "solvable" or not is another unsolvable problem. In which case the best you could do is identify some types of code that do exhibit known behavior and analyze them (omitting the code you didn't recognize).

Could be an interesting AI topic. Definitely beyond the scope of my ability, though.

---

### Post by CptPicard on 2013-01-26
> **trent.josephsen said:**
> I imagine you wouldn't often run into the halting problem with most real-life code, but that doesn't mean it would be easy to write a program capable of analyzing any code that can be analyzed, 

The problem with that would be that I suspect code does not divide into "code that can be analyzed" and "code that can't be analyzed". If you want a code analyzer, you must deal with Turing-complete code, otherwise you're analyzing a subset of programs that won't be able to do "anything a program can do". And if you have such a code analyzer, then you will always able to construct hostile input. How common such hostile input is, is the question of interest.

> let alone figuring out whether the code it's looking at is in that category...

I do think that this kind of a classification problem is also impossible to solve. I can't off the cuff give you a sound theoretical reason as to why, but looking back at my time at uni and studying typical intractable problems, the classification problem of whether an input is in the class of the problem generally is as hard as solving the problem itself. Just a hunch, but a very strong one.

> 
Actually, I think that determining whether a particular piece of code is "solvable" or not is another unsolvable problem.

Oh, I typed before I read your whole post :p

> Could be an interesting AI topic. Definitely beyond the scope of my ability, though.

Sounds more like classic computability plus compilers problem. Then again anything that is not solved yet can be called "AI" :)

The philosophical intersection between AI and computability is really interesting though. Especially if we assume the Church-Turing thesis to be true and if we accept a materialistic explanation of consciousness -- this would mean that the mind is a Turing machine. This has interesting implications concerning the idea that we can understand the incompleteness theorems, which are the basis for intractability in computation. But does this mean that the mind could still have similar limits... some kind of thoughts that can be thought, but that we can't come to within the scope of our own minds? :)

---

### Post by faceshed on 2013-01-27
I was just thinking it would be nice to get a idea of how often I should use or avoid a given function. Sometimes I end up reading tons of code just to size up a library.

It doesn't sound like it would be that hard to make a guess at the level of complexity or even just force the programmers to document functions.

---

### Post by Zugzwang on 2013-01-27
It's an interesting discussion that you people have started here (if you allow me to actually call it a discussion). Let me add a perspective from a fellow computer scientist.

What CptPicard wrote is a sure thing: we will never obtain a technique that will work out correctly the worst-case "big-O" computation time for all algorithms as input, as that problem is undecidable. Also, even if we have a technique that works in the vast majority of "practical cases", it would be pretty much impossible to characterise what constitutes a practical case in a precise manner without someone immediately coming up with a counter-example ("pretty much impossible" here means that if your characterisation is complicated enough, no one would try).

Yet, that doesn't make faceshed's idea useless. People in software verification have come up with clever ways to compute loop invariants automatically and thus prove software to be correct (with respect to its specification) automatically. Surely, there always exist loops for which none of these techniques work. Nevertheless, they cover a nice set of cases, but only give sufficient conditions for coverage, and not necessary ones. One *could* come up with a technique that analyses these loop invariants and derive the big-O-complexity of the algorithm.

But this is far from trivial. Especially if you are calling sub-routines, or use recursive algorithms, a whole set of sub-problems arise that make such an automatic analysis technique cumbersome to develop.

All in all, the idea *might* be suitable for a multi-million-dollar research project in computer science for which it is totally open if the outcome would really be useful in practice. Actually, I wouldn't be surprised if some research funding agency on this planet hasn't funded something like that already.

------

To nitpick, "big-O" analysis might actually not be a big deal, as nested for-loops in which only sub-routines with polynomial complexity are called have polynomial complexity. In this case, the answer "O(2^n)" for the input size n is correct, as for big-O, we are allowed to overapproximate. What the OP probably meant was "Big Theta"-Notation, where this crude approximation is not allowed.

---

### Post by trent.josephsen on 2013-01-27
> **Zugzwang said:**
> To nitpick, "big-O" analysis might actually not be a big deal, as nested for-loops in which only sub-routines with polynomial complexity are called have polynomial complexity. In this case, the answer "O(2^n)" for the input size n is correct, as for big-O, we are allowed to overapproximate.

Right, but you couldn't use that trick for O(3^n) or O(n!) algorithms, for instance. It's probably still an unsolvable problem even so.

I've never heard of an algorithm with greater than O(n!) complexity, but I guess you could probably construct one.

---

### Post by Bachstelze on 2013-01-27
> **trent.josephsen said:**
> 
I've never heard of an algorithm with greater than O(n!) complexity, but I guess you could probably construct one.

Like so: [http://en.wikipedia.org/wiki/Bogosort](http://en.wikipedia.org/wiki/Bogosort)

---

### Post by Zugzwang on 2013-01-27
> **trent.josephsen said:**
> 
I've never heard of an algorithm with greater than O(n!) complexity, but I guess you could probably construct one.

There are decidable problems that have a doubly-exponential complexity, i.e., every algorithm for these problems needs Theta(2^2^poly(n)) time for some polynomial. 

[http://en.wikipedia.org/wiki/2-EXPTIME](http://en.wikipedia.org/wiki/2-EXPTIME) lists one such problem, and Google finds others.

Then there are problems that a NEXPTIME-hard, for which it is open whether there exist exponential-time algorithms for these or not: [http://en.wikipedia.org/wiki/NEXPTIME](http://en.wikipedia.org/wiki/NEXPTIME)

For most of these problems, people have actually designed and implemented algorithms.

---

### Post by JDShu on 2013-01-27
> **Bachstelze said:**
> Like so: [http://en.wikipedia.org/wiki/Bogosort](http://en.wikipedia.org/wiki/Bogosort)

Oh wow, this has a name? I thought of it a while ago and joked about it with friends. The saying goes that if you have a good idea, then three other people have thought of it already. I guess it's the same with bad ideas ;)

---

