---
title: "find a minmax in prolog program"
date: 2010-10-12
forum: Programming Talk
---

### Post by IUViet on 2010-10-12
could someone help me?

Program?

[HTML]minmax(L,Min,Max) :- minlist(L, Min), maxlist(L, Max).[/HTML]

Test?


- minmax([1,2,3], Min, Max).
ERROR: minmax/3: Undefined procedure: minlist/2
?- minmax([1,2,3], Min, Max).
ERROR: minmax/3: Undefined procedure: minlist/2
?- minmax([9], Min, Max).
ERROR: minmax/3: Undefined procedure: minlist/2

---

### Post by NovaAesa on 2010-10-12
Well you don't have minlist and maxlist defined yet... This is absolutely screaming "homework".

I would suggest getting to know the language with some very basic examples before getting into a more complex algorithm such as minmax.

---

### Post by hardmath on 2010-10-15
The term minmax in mathematics or computer science often means a kind of optimization problem in which the objective is minimizing the maximum value of a function (by optimal setting of parameters).  For example you might want the polynomial on [0,pi] whose maximum error in approximating sin(x) is least.

But that doesn't seem to be the question here, which has to do (judging by the snippet of "test" code) with finding both the minimum and maximum items in a list.

Several issues come to mind.  What type of items are we dealing with?  Integers?  Floating point numbers?  Something more exotic?

Also, even assuming we are just comparing integers, what kind of result should an empty list produce?

It's not so much a complicated problem as a poorly defined one.  Probably the OP knows from the context but I'm left to guess at these details.

Here's a way to do **minlist/2** without any extra arguments or auxiliary predicates:

```
minlist([H],H).
minlist([H|T],Min) :-
    minlist(T,Mum),
    ( H < Mum -> Min = H ; Min = Mum ).

```

This code is not "tail-recursive" (for those who know about such things), and a better implementation would use an extra argument and an auxiliary predicate for the sake of efficiency.  That perhaps qualifies it as making the problem complicated.

Of course a similar approach to the one above could implement **maxlist/2**, and one might tie all the loose threads of efficiency together with code that finds both minimum and maximum items in a list in a tail-recursive way.

Bonus Question:  What happens if the predicate above is called on the empty list?

regards, hardmath

---

