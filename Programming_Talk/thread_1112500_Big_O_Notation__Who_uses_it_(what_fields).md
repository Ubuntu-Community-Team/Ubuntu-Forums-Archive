---
title: "Big O Notation  Who uses it (what fields)"
date: 2009-03-31
forum: Programming Talk
---

### Post by brian77095 on 2009-03-31
I just wanted to know who uses this?  Is it mainly for big projects?  Is there any other good sites to learn more about it?

[http://en.wikipedia.org/wiki/Big_O_Notation](http://en.wikipedia.org/wiki/Big_O_Notation)

Is it less important now that memory and cpu speed has grown so much??

Thanks for the help as always...
B

---

### Post by kjohansen on 2009-03-31
It is still really important.  CPUs are fast, but data sets are getting larger.

In software engineering, the topics will be less important, but in numerical analysis, machine learning and anywhere extensive computation is used it will be important.

Recently I was working on an algorithm that in one way is O(n^3) but if you cleverly rearrange it it is O(n^2), this saved a significant amount of time.

The seminal book is "Introduction to Algorithms" by Cormen et al.  It is a big book, but well written and organized.  I took two courses in algorithms, one at the undergraduate level and one at the graduate level.  Algorithms is something that is probably best learned in a formal education...

Here is a link to an instructor that I had who is currently teaching the course and posts his lecture notes online: [http://www.cse.ohio-state.edu/~lai/680/680.htm](http://www.cse.ohio-state.edu/~lai/680/680.htm)

Also MIT's open courseware has full video lectures for thier introduction to algorithms course.  It is taught by one of the authors of the book I previously mentioned.  I watched the videos to prepare for my qualifying exams and they are quite good.

---

### Post by wmcbrine on 2009-03-31
It's not really something you'd "use", unless you're a computer scientist; more like something you'd internalize, understand, and recognize when you see it. Project size is irrelevant, and no, it will never be obsolete.

---

### Post by monkeyking on 2009-03-31
big oh notations is a good way of proofing to yourself and others what the complexity of a series of statements is.

It goes with commensense,

Finding an element in an array might have to search throuhg all elements. So it depends on the length of the array.

Multipling to n-digit numbers depends on n^2.

It's not something you need in big projects only.

If you have written a program that is to slow,
you might want to break down where the problem is.

So you would first profile to find the bottleneck.
And then you would analyse the complexity of this bottleneck  part.

---

### Post by slavik on 2009-03-31
traveling salesman problem

first one to solve it for 100 nodes on their home computer gets 1musd from me ... on and it has to be done by this time next week.

---

### Post by CptPicard on 2009-04-01
The whole point of the big-oh notation is to extract the asymptotically dominating parts of the expression that characterizes the runtime of some algorithm so that things like speed differences of CPUs become irrelevant and you can meaningfully compare the algorithms themselves.

Things like constant, logarithmic, linear, polynomial and exponential runtimes will always be in classes of their own and the faster to be preferred regardless of how much improvement you manage to squeeze from your hardware.

---

### Post by sujoy on 2009-04-01
> **slavik said:**
> traveling salesman problem

first one to solve it for 100 nodes on their home computer gets 1musd from me ... on and it has to be done by this time next week.

you got some other NP complete problems to throw at us? ):P cause i hate salesmen


EDIT: big O, small O and all those complexities can help you judge algorithms that does the same thing. time complexity might not seem to be an issue at first, however, now that we have faster processors, we also have more and more data to process. and having a fast processor aint no excuse for writing sloppy codes

---

### Post by Wybiral on 2009-04-01
> **wmcbrine said:**
> It's not really something you'd "use", unless you're a computer scientist; more like something you'd internalize, understand, and recognize when you see it. Project size is irrelevant, and no, it will never be obsolete.

I agree. I think the obvious distinctions to make will be constant, linear, exponential, and factorial. Once you learn to recognize those kinds of patterns, for the most part, you don't need to over-analyze everything. And most of the time, just knowing common algorithms and how they scale on the bestcase/worstcare will help you quite a bit (unless you're in some research area of uncharted territory, it's probably been done and studied).

---

### Post by slavik on 2009-04-01
subset sum, sudoku, knapsack problem

---

