---
title: "(C++) Unbounded Knapsack Problem"
date: 2009-04-07
forum: Programming Talk
---

### Post by Beezleray on 2009-04-07
Hi,
I'm trying to find an algorithm that helps solve an Unbounded Knapsack problem in C++, but I'm having trouble. Any help at all would be great!
Thanks!

EDIT:
I've tried using the Greedy Algorithm but it doesn't get the exact solution, close but not right.

---

### Post by Arndt on 2009-04-07
> **Beezleray said:**
> Hi,
I'm trying to find an algorithm that helps solve an Unbounded Knapsack problem in C++, but I'm having trouble. Any help at all would be great!
Thanks!

EDIT:
I've tried using the Greedy Algorithm but it doesn't get the exact solution, close but not right.

Do you just need an existing solver, in any language, or does it have to be C++, or do you want to write one yourself? Wikipedia has a reference to an existing one in CAML.

When you say the greedy algorithm doesn't get the exact solution, how do you know there is a better solution?

---

### Post by Tony Flury on 2009-04-07
From reading wikipedia myself it does not look like it has a algorithm that gets a perfect solution. Many maths problems (such as the Travelling salesman for instance) are like this.

The Greedy Algorithm may be the best you get, in that it gets you a good approximation to the right answer, but in some case it might be sub-optimal.

And as Arndt says - if you know that the Greedy Algorithm does not always give the best answer - how do you know ?

---

### Post by Beezleray on 2009-04-07
> **Arndt said:**
> Do you just need an existing solver, in any language, or does it have to be C++, or do you want to write one yourself? Wikipedia has a reference to an existing one in CAML.

When you say the greedy algorithm doesn't get the exact solution, how do you know there is a better solution?

Well I know the math for the most part(that's how I know the greedy algorithm isn't working) I just don't know how to implement it in C++. I would like to be able to figure out how to write it myself, (and in ways an existing solver could help me learn) basically I have two arrays one with the price and one with the weight, I know how much it can hold and I have any number of those items. I just can't seem to figure out how to iterate through correctly to find the best possible solution.

---

### Post by Zugzwang on 2009-04-07
> **Beezleray said:**
> Well I know the math for the most part(that's how I know the greedy algorithm isn't working) I just don't know how to implement it in C++. I would like to be able to figure out how to write it myself, (and in ways an existing solver could help me learn) basically I have two arrays one with the price and one with the weight, I know how much it can hold and I have any number of those items. I just can't seem to figure out how to iterate through correctly to find the best possible solution.

As this looks like homework, I'm just giving you an example how iteration might work. Look at the following thread for an example:

[http://ubuntuforums.org/showthread.php?t=846302&highlight=recursion](http://ubuntuforums.org/showthread.php?t=846302&highlight=recursion)

---

### Post by CptPicard on 2009-04-07
I suppose you mean that you are trying with a small enough example that you can just manually construe the optimal solution or something, as there is no mathematical "closed form solution" or anything like that.

We're dealing with an NP-hard problem, so there is no known efficient (polynomial-time) exact algorithm. Trying is either a waste of time or makes you a huge genius if you succeed. :)

There is, however, the pseudo-polynomial DP algorithm for it that is mentioned in the wikipedia article... it is fairly easy to implement.

Or, you can always just simply brute force it.

---

### Post by sujoy on 2009-04-07
you can calculate the ratio of price to weight for each object, sort it in descending order. and fillup the knapsack with as much of the highest ratio object as you can (in whole numbers) and move on to the next object with the highest ratio.

---

### Post by Zugzwang on 2009-04-07
> **sujoy said:**
> you can calculate the ratio of price to weight for each object, sort it in descending order. and fillup the knapsack with as much of the highest ratio object as you can (in whole numbers) and move on to the next object with the highest ratio.

..which is (almost) the greedy algorithm that the OP mentioned and not wanted.

Hint to the OP: You may also try to reduce the problem to SAT solving or something similar if you really want the precise solution. As CptPicard wrote, there's of course no guarantee that this (or any solution, provided that NP!=P) works fast, but it might work fast enough for you on the problem instances you are concerned with. "Branch&Bound" is also a concept you should look up for ideas how to implement a solver for this problem.

---

### Post by Beezleray on 2009-04-07
Thanks for your help guys, its greatly appreciated!

P.S.
Its not homework, just a [fun little side project]("http://www.facebook.com/careers/puzzles.php?puzzle_id=2") to help learn the language.

---

