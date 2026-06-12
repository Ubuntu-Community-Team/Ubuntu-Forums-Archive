---
title: "Optimal solution == brute force solution?"
date: 2008-11-03
forum: Programming Talk
---

### Post by YetAnotherNoob on 2008-11-03
I have a problem which involves calculating a maximum "optimal" result from two sets of inputs.

I won't go into the details because it is boring and finance related.  

Simply put, I have two sets of inputs: A's and B's. Using my formula I can calculate the result for each individual pair of A and B.  Using different combinations of A and B result in better or worse results.

What kind of maths/algorithm would you recommend to avoid using a brute force approach?  (By brute force I mean calculating all possible combinations of A and B and comparing the results).

Do you know of any specific algorithm implementations I can refer to?

:confused:
puzzled.

---

### Post by pp. on 2008-11-03
> **YetAnotherNoob said:**
> I have two sets of inputs: A's and B's. Using my formula I can calculate the result for each individual pair of A and B.

Having no idea what the As and Bs or myFormula might be, it is a bit hard to tell if there is any way of finding the 'optimal' solution.

---

### Post by Tony Flury on 2008-11-03
Without details of your formula it would be near on impossible for anyone to assist you, and it also depends on your definitions of best and worst.

For instance - say your formula was a simple addition - and the best result meant the biggest answer... in this case simple choose the largest number in set A, and the largest in set B.

If your formula is a division though (say A/B) then you want the largest A and the smallest B.

if your formula is more complex then it might be very difficult - if not impossible to determine a simple rule to identify the best arguments.

What you will need to do is analyse your formula - and identify how it changes when you change A & B - that might lead you to a method of finding the optimal inputs - use of differential calculus might help here - but you are dealing with two variables so it will be complex - good luck.

---

### Post by AndyCee on 2008-11-03
As already pointed out, difficult to do without knowing details.

HOWEVER

If you need to find which two inputs give the single best solution, and don't want to compare all of them, you just need some variable/box to remember the best one, and compare new ones to the best one only. If the new one is better, make it the new 'best' one.

ie.

best = function(a[1],b[1])

For x in a
  For y in b
    result = function(a[x],b[y])
    if best betterthan result
      best = result

Sorry, I only really know C, not pseudocode :o(

---

### Post by Reiger on 2008-11-03
Yes it is possible and it involves Math. Remember how you'd find the maxima and minima of an arbitrary function f(x) ? You'd differentiate and solve for f'(x) = 0.

---

### Post by Npl on 2008-11-03
> **Reiger said:**
> Yes it is possible and it involves Math. Remember how you'd find the maxima and minima of an arbitrary function f(x) ? You'd differentiate and solve for f'(x) = 0.That would mean your 'arbitrary' function is differentiable which is a rather strong property.
unless the OP gives a hint about what kind of functions he`s dealing with, theres no answer that works for the most generic functions (brute-force is an answer, but its hardly practical)

---

### Post by elbarto_87 on 2008-11-03
As it has already been said, it is hard to define what methods of optimization might work for your case but have you looked into linear programming?

[Linear Programing Link]("http://en.wikipedia.org/wiki/Linear_programming")

Last semester I used a program called lingo (or lindo?), I think it is commercial software but maybe there is a python module or such out there already. We mainly used to for optimizing time functions and traffic timing etc but there were a number of examples given on finding the optimal solution to profit scenariors by maximising a objective function.

Might be worth a look any way.... Especially if you eventually indent to use more than just 2 variables.

Elbarto

---

### Post by Reiger on 2008-11-03
> **Npl said:**
> That would mean your 'arbitrary' function is differentiable which is a rather strong property.
unless the OP gives a hint about what kind of functions he`s dealing with, theres no answer that works for the most generic functions (brute-force is an answer, but its hardly practical)

Well if the input is numeric you can either apply the D operator (differentiate) or the Delta one. With a few exceptions, but AFAIK these do not apply to 'boring finance' stuff.

---

### Post by CptPicard on 2008-11-03
It sounds like a combinatorial optimization problem where each pair from sets A and B have some utility value and then you need to find minimum or maximum. "Optimal subset" style problems always have a whiff of NP-completeness to me...

---

### Post by Npl on 2008-11-03
> **Reiger said:**
> Well if the input is numeric you can either apply the D operator (differentiate) or the Delta one. With a few exceptions, but AFAIK these do not apply to 'boring finance' stuff.I dont see what you gain by transforming the input in that case. Searching for points where the transformed input == 0 aint much easier than searching for the optimum directly.
searching for f`(x) == 0 is easy if you have an analytical representation. If you dont, then you can only apply numeric algorithms (which might or might not find an true optimum)

---

### Post by pp. on 2008-11-03
How can it possibly help anyone when we debate here about hypothetical functions when all we can say to OP is that his question is impossible to answer?

):P

---

