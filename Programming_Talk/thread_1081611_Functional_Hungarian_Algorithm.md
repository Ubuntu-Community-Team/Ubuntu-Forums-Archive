---
title: "Functional Hungarian Algorithm"
date: 2009-02-26
forum: Programming Talk
---

### Post by PythonPower on 2009-02-26
I've recently come across the [Hungarian Algorithm]("http://en.wikipedia.org/wiki/Hungarian_algorithm") (also called the Kuhn-Munkres algorithm) and after seeing it outlined have become intrigued if the algorithm can be reformulated nicer in a functional way.

Indeed, at the moment I don't feel I have it fully grasped and think I would better if it was expressed more functionally. The steps are outlined clearly [here]("http://www.cob.sjsu.edu/anaya_j/HungMeth.htm") but without justification.

My intrigue begs two questions: why does that algorithm work? And, as I've said, can we recode it functionally? :p

---

### Post by Tony Flury on 2009-02-26
I think I understand the why - well to a certain extent.

when you find the minimums in each row and each column, and subtract them from those rows and columns - you are basically finding (for each row/column) the additive cost (above minimum), and you get zeroes at each local minimum.

Covering all the zeros gives you (you hope) a set of intersections that covers every zero (and includes every column and every row), and that in theory it should be close to an optimal solution. 

If you have not covered every column/row, this actually means you have a local mimimum that has not previously detected, in which case - you take that into account - and try again.

I hope that helps.

---

### Post by Wybiral on 2009-02-26
> **PythonPower said:**
> And, as I've said, can we recode it functionally? :p

Everything can be recoded functionally. The only real issues come when you have to think about things like I/O.

That's not to say that you wont have to rethink your data structures (for instance, instead of using a mutable dict/hashtable, you can use a persistent immutable hashtable representation with similar properties, 'state' is passed on to other functions as arguments).

---

### Post by Mr.Macdonald on 2009-02-26
Is this algorithm accepted as the fastest algorithm for this problem?

---

### Post by Paul Miller on 2009-02-27
I don't know about fastest, but it's certainly efficient.

As for why it works, here's a bit of an explanation: If you formulate the assignment problem in terms of finding a minimum weight perfect matching in the bipartite graph the joins people to jobs via weighted edges, finding perfect matchings in bipartite graphs is easy (read: can be accomplished in polynomial time).  Because there are only polynomially many perfect matchings in any bipartite graph, and the cost of a given matching can be checked in linear time, even the naive method of generating them all and checking their cost would end up being polynomial.  

The reason you get a minimum weight matching by minimizing the weight of each edge is that the weight of a matching is linear in the weight of each edge.  That linearity allows you to be incredibly naive about it.  If (hypothetically) the method for calculating the total weight of a matching were not linear in the weight of each edge, all you'd have done is reduced a nasty nonlinear minimization to a maybe slightly less nasty nonlinear minimization.

As for the question of whether it can be done functionally, sure it can.  The proof is left as an exercise. :P

---

### Post by CptPicard on 2009-02-27
Hey, that's a new one... and I even did quite a bit of combinatorial optimization / linear programming / primal-dual methods in grad school.... I guess I just always looked at it straight in terms of the network flows in bipartite graphs etc...

---

### Post by PythonPower on 2009-02-27
Thanks for some interesting posts guys.

> **Wybiral]Everything can be recoded functionally. The only real issues come when you have to think about things like I/O.[/QUOTE]

Of course said:**
> ...

Yes; intuitively I can see why it would tend to work very well but I'm a little unhappy with that level of rigor.

[QUOTE=Paul Miller]Because there are only polynomially many perfect matchings in any bipartite graph, and the cost of a given matching can be checked in linear time, even the naive method of generating them all and checking their cost would end up being polynomial.[/QUOTE]

I'm not sure I understand... Surely the first node can go to any other (n possibilities), the second to n-1 possibilities etc... making n! perfect matchings?

---

### Post by Tony Flury on 2009-02-27
I think the point it is not neccessarily fast but it does produce a result which is at least a close to optimal (a real local minimum) solution and may well be the optimal solution (or at least one of them.

The actual problem (also known as the travelling salesman problem) has no simple solution for finding the definite optimal solution (unless you try absolutely every combination of every row/column intersection which is impractical for any reasonable problem)

---

### Post by PythonPower on 2009-02-27
The algorithm is deterministic isn't it? There must be quite simple proof behind it... I'll have some time this weekend to think about it properly.

---

