---
title: "Efficiently selecting L unique pairs out of (M*N) pairs of numbers"
date: 2010-04-25
forum: Programming Talk
---

### Post by WebDrake on 2010-04-25
Hello all,

An algorithmic issue that's bugging me, and that I'm wondering how to solve.  I'm implementing this in C++.

Suppose that I want to select L unique pairs of integers from the set of pairs (x,y), where x is in [0,M) and y is in [0,N).

There are two ways I can think of to do this.

(i) create an empty **std::set** to hold **std::pair<int,int>** values.  Randomly generate pairs of integers in [0,M) and [0,N) and try to add them to the set -- if it succeeds, it's a selected pair.

Problem with this approach: works only if L << M*N, otherwise you get major slow-ups with lots of duplicate pairs being generated.

(ii) create a vector of the complete set of M*N pairs.  Randomly generate integers in the range [0,vec.size()) and remove the selected entry from the vector.

Problem with this approach: no major speed problems, but if M and N are large, a major allocation problem generating and storing all M*N pairs.

Of course, if L is anywhere near the order of M*N (enough for the problem with the first way of doing things to arise), the program will need to allocate lots of space anyway.  But I'm wondering if there's any space- and speed-efficient method that I've missed.

Advice and thoughts gratefully received ... :-)

Thanks & best wishes,

    -- Joe

---

### Post by CptPicard on 2010-04-25
I'm not that well-versed in sampling algorithms, but I would probably approach this by recognizing that those pairs can be numbered according to their lexicographical ordering (this mapping is not very hard to come by). Assuming there are K such unique pairs, I would take an array of integers 0..K-1, shuffle that, take the first L and and map  back into the corresponding pair.

The numbering is not really necessary but it may produce a more compact representation than actually using the pairs themselves.

---

### Post by croto on 2010-04-25
I was thinking... some random number generators give you non-repeating sequences covering all the range. Maybe you can tailor one up to generate a non repeating random sequence from 0 to M*N-1 (also, I'm thinking of your superset of M*N pairs as a one dimensional object... you'll need to convert from the random integer z from 0 to M*N-1 to the pair (x,y), maybe something like x=z/M, y=z%m would work, maybe there are better ways)

As for your method number 2, deleting elements from a vector is an expensive operation. I would improve it by first choosing a random element z from 0 to M*N-1, then swapping the z-th element with the 0-th element. The second step involves choosing a random integer z from 1 to 0 to M*N-1 and swapping the zth element with the 1-th element, and so on. Your L pairs will be in the beginning of the vector.

---

### Post by Lux Perpetua on 2010-04-25
I'm assuming you want to generate a uniformly random L-element subset of a Z-element set (where Z = MN), i. e., so that each subset appears with equal probability. Ideally, we'd like O(L) time and space complexity. That might be possible, but I'll show you O(L*log(L)) time and O(L) space. (L*log(L) isn't too bad, but it's still superlinear.) For simplicity, I'll assume the Z-element set is just [a, b), where b-a = Z. I leave it to you to transform an element of that set into an element of [0, M)x[0, N). 

```
random_subset(L, a, b):
    if b-a or L are small enough:
        return basis_case(L, a, b)

    c = floor((a + b)/2)
    (S1, S2) = (c-a, b-c)
    (L1, L2) = (0, 0)

    repeat L times:
        r = rand_int([0, S1 + S2))
        if r < S1:
            L1++
            S1--
        else:
            L2++
            S2--

    return union(random_subset(L1, a, c),
                 random_subset(L2, c, b))
```I think you can see what's going on here. It's just divide-and-conquer: take your big set of Z balls and color half of them black and half of them white. Randomly pick L balls without replacement and record the numbers of black and white balls. Declare the black balls to come from the lower half of the interval [a, b), and the white balls to come from the upper half. Now recurse on the balls from each half. 

Unfortunately, the "repeat L times" loop in each recursive call introduces a log(L) factor in the time complexity, which is annoying. In contrast, CptPicard's solution is O(L) time and O(Z) space. There might be a way to get the best of both worlds, but I'm not seeing it at the moment. In any case, both his method and mine beat yours. ;-)

---

### Post by Some Penguin on 2010-04-25
> **Lux Perpetua said:**
> 
Unfortunately, the "repeat L times" loop in each recursive call introduces a log(L) factor in the time complexity, which is annoying. In contrast, CptPicard's solution is O(L) time and O(Z) space. There might be a way to get the best of both worlds, but I'm not seeing it at the moment. In any case, both his method and mine beat yours. ;-)

A full shuffle will actually be at least linear (and probably worse -- naively, O(Z log Z)) in the possible space.  A very obvious way to reduce this to O(Z log L) in time complexity is to not shuffle the entire thing, but to insert each item with a priority into an at-most-size-L heap; heap operations are O(log heapsize).   

This is still inefficient where L << Z, or where L ~ Z (which is basically the same case as L << Z; you select a few  and then return the remainder, provided that you're trying to select a random subset and not a randomly ordered list; if you are, you are basically asking about shuffling, and are likely stuck with sort costs).  Where L << Z, just select and retry if you repeat a selection, using a hash-based approach to detect collisions. 

There are also perhaps weirder approaches.  For instance, you could create a Z-size array of lists  Assign each pair to a random list (not necessarily distinct).  If you implement these lists using linked lists with addition at the head, each of these additions takes constant time.  Then iterate over the lists.  If you at least as many picks than the list size, you grab the whole list and move on (and if you need a *shuffled* set, then you shuffle the list, which is likely to be very small; this minimizes the log() factor); otherwise, you shuffle the list  and take what you need, and stop.  This is space-hungry but potentially rather time efficient.

---

### Post by CptPicard on 2010-04-25
Shuffling is linear. You seem to be talking about sorting?

---

### Post by WebDrake on 2010-04-26
Thanks very much to everyone for the detailed replies -- very kind of you all. :-)

First off, yes, it clearly makes sense to select "pairs" by actually selecting a subset of integers in the interval [0,M*N).

As for algorithms -- the aim here is to optimize from the point of view of memory usage but without (too badly) hitting performance.  The practical case might be having on the order of 1e+12 _potential_ pairs but only wanting to select (say) 1e+8 of them.

Alternatively it is surely possible to select one or another algorithm depending on various magnitudes ... :-)

Couple of concrete questions for Lux Aeterna -- first, I have the feeling I should know this algorithm -- does it have a name? :-)

Second, what's the basis_case() that you refer to?

Thanks and best wishes,

    -- Joe

---

### Post by WebDrake on 2010-04-26
Further to the above: any good general recommendations for further reading, references etc. on problems like the above?  And are there any good C/C++ libraries out there providing such algorithms?

It's not that I don't want to write the code myself, but it is always nicer to not reinvent the wheel, and to make use of development resources already available within Ubuntu.

---

### Post by CptPicard on 2010-04-26
Well, Knuth's "Art of Computer Programming" may be of interest. Really, you will want to study algorithmics in general; and combinatorial algorithms such as this are a really nice starting point for various reasons... they are building blocks for many other algorithms, and often it can be discovered that some computationally very hard problem in this vein is actually the "hard part" in some more general problem. The downside is that they often end up being NP-hard/-complete, yet are deceptively simple at first sight and tend to show up with disturbing regularity almost anywhere...

Looking for ready-made implementations is not the route to go down here, as you want to be able to identify the problems and creatively deal with them as a part of whatever you're doing otherwise.

---

### Post by Lux Perpetua on 2010-04-26
> **WebDrake said:**
>  first, I have the feeling I should know this algorithm -- does it have a name? :-)I don't know either. If it does, I think Knuth's book would be a great place to look first. 
> **WebDrake]Second, what's the basis_case() that you refer to?[/quote]It's there to prevent infinite recursion. The idea of a recursive algorithm is typically to repetitively reduce your problem into smaller subproblems until the subproblems are small enough to be trivial. At that point, you solve those tiny subproblems nonrecursively said:**
> Alternatively it is surely possible to select one or another algorithm depending on various magnitudes ...That's the beauty of recursion. For performance reasons, you might want a larger cutoff for the basis case: it might turn out that if L <= C (C is some constant), or L >= K*(b-a), it pays off to use a different algorithm. Those can be your basis case: 
```
random_subset(L, a, b):
    if L <= C:
        return algorithm1(L, a, b)
    if L >= K*(b-a):
        return algorithm2(L, a, b)

    ...
```It's a very flexible approach. As you implied earlier, rejection sampling isn't bad if L << b-a. Also, CptPicard's solution of shuffling [a,b) and taking the first L items makes sense if L is close to b-a. The recursive solution can accomodate all of that. 

However, don't worry about this until you have the simplest solution working, and then only worry about it if it's too slow.

---

### Post by WebDrake on 2010-04-27
> **CptPicard said:**
> Looking for ready-made implementations is not the route to go down here, as you want to be able to identify the problems and creatively deal with them as a part of whatever you're doing otherwise.

In general, sure.  The above problem as Lux Perpetua has described it -- generating a subset of size L from the integers in the interval [b,a) -- seems generic enough that I was wondering if there was a 'standard' implementation.

I really, really must get my own copy of Knuth....

Thanks ever so much to all of you for your detailed and kind explanations.  I'll have a go at implementing this and see what I can make out of it ... :-)

---

### Post by WebDrake on 2010-05-09
Funny, isn't it, how missing the appropriate terminology is a major block to finding what you want ... :-)

Armed with the term 'sampling algorithms' I was able to make much more progress with a literature search, and came across this set of interesting papers:
[http://doi.acm.org/10.1145/358105.893](http://doi.acm.org/10.1145/358105.893)
[http://doi.acm.org/10.1145/23002.23003](http://doi.acm.org/10.1145/23002.23003)
[http://doi.acm.org/10.1145/79505.356313](http://doi.acm.org/10.1145/79505.356313)

... which provide an algorithm with minimal storage requirements [O(L) if you store the selected items in memory all at once, constant otherwise] and average O(L) running time, with approximately L random numbers being required.

I think I'll have a go at implementing this algorithm and will post code here when I'm done.  It also looks like it is generic enough to be decoupled to an extent from application.

---

### Post by WebDrake on 2010-05-12
> **WebDrake said:**
> I think I'll have a go at implementing this algorithm and will post code here when I'm done.  It also looks like it is generic enough to be decoupled to an extent from application.
As per the above, please see:
[http://ubuntuforums.org/showthread.php?t=1481246](http://ubuntuforums.org/showthread.php?t=1481246)

... for an announcement of a new extension to GSL currently in development, that will implement these algorithms and hopefully others.

---

### Post by WebDrake on 2010-05-15
The efficient algorithm D from the above papers (Vitter 1984, 1987) is now implemented and available for testing ... :-)
[http://github.com/WebDrake/GrSL/](http://github.com/WebDrake/GrSL/)

Algorithm E from Nair (1990) soon to follow.

---

### Post by slavik on 2010-05-16
> **WebDrake said:**
> The efficient algorithm D from the above papers (Vitter 1984, 1987) is now implemented and available for testing ... :-)
[http://github.com/WebDrake/GrSL/](http://github.com/WebDrake/GrSL/)

Algorithm E from Nair (1990) soon to follow.
look at database code and see how they do joins :P

other than that ... are N and M large enough where O(m*n) is prohibitive?

---

### Post by WebDrake on 2010-05-17
> **slavik said:**
> look at database code and see how they do joins :P

other than that ... are N and M large enough where O(m*n) is prohibitive?

I don't know about 'prohibitive', but it is certainly annoying :-)

The greater benefit of the particular algorithms by Vitter and Nair is that they actually don't require the data (either the complete dataset or the selected subset) to be stored in memory -- and memory _is_ where O(m*n) becomes prohibitive ...

---

