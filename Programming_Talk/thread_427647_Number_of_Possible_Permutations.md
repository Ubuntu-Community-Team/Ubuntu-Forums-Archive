---
title: "Number of Possible Permutations"
date: 2007-04-29
forum: Programming Talk
---

### Post by smartbei on 2007-04-29
Given a certain multiset ({a,a,a,a,a,a,a,a,a,a,b,b,b,b,b,b,b,b,b,b} for example) how do I find the **number** of possible permutations using all of the multiset's members?

I have read through the wikipedia articles on the matter (permutations, combinatorics, etc.) and am still somewhat lost. It is possible to actually find all the possible permutations, bu this is prohibitavely expenisve time-wise, one you go beyond 10-15 characters.

An equation, and/or an explanation will suffice.

Thanks for all replies!

---

### Post by yabbadabbadont on 2007-04-29
Do your own homework...   :D

---

### Post by cwaldbieser on 2007-04-29
> **smartbei said:**
> Given a certain multiset ({a,a,a,a,a,a,a,a,a,a,b,b,b,b,b,b,b,b,b,b} for example) how do I find the **number** of possible permutations using all of the multiset's members?

I have read through the wikipedia articles on the matter (permutations, combinatorics, etc.) and am still somewhat lost. It is possible to actually find all the possible permutations, bu this is prohibitavely expenisve time-wise, one you go beyond 10-15 characters.

An equation, and/or an explanation will suffice.

Thanks for all replies!

I think there would be 20!/(10! x 10!) permutations.  That would be 184,756 if my arithmetic is correct.
I started with a simple case, and elaborated on it:
{a,b,c}
I know there are 6 permutations.  I can write them all out or compute them as 3!.
{a,a,b}
I substitute a's for all the c's, and then cross out the duplicates.  There are only 3 permutations.  That makes sense to me, because where in the first example I could create more permutations by moving around the third element, I only have half as many elements now.

It looks like when there are duplicate elements, the number of permutations will be reduced.  I was not sure what the divisor would be, but I am thinking it should be some function of the number of duplicates.  I know with 4 distinct elements, there are 4! or 24 permutations.
With {a,a,a,b} there are only four permutations I can write out.  This seems to fit 4!/(3! x 1!).
With {a,a,b,b} there are 6 permutations.  This also fits 4!/(2! x 2!).

It is really just guesswork and trying to find a pattern rather than a more reasoned approach, but that is how I'd do it.

---

### Post by smartbei on 2007-04-29
Heh - this isn't homework. I was intersted and couldn't find an amswer. :D

Thanks for the prompt response cwaldbieser!

---

### Post by Rumo on 2007-04-29
20!/(10!*10!) is correct!

Here's a simple approach:
Suppose you have to pick 10 values out of 20 possible values. Each picked value now represents the position of an a (or b) in the succession of a's and b's.

You probably already noticed that this is equivalent to a simple lottery problem (with the solution n!/(k!*(n-k)!).

---

### Post by Ramses de Norre on 2007-04-30
If you want a more precise explanation you might want to look for combinations and binomial coefficients, because that's what the n!/(k!*(n-k)!) is.

---

### Post by Ayman on 2007-04-30
Actually, this is a [multinomial coefficient](http://en.wikipedia.org/wiki/Multinomial_coefficient). [Binomial coefficients](http://en.wikipedia.org/wiki/Binomial_coefficient) are used to calculate the number of distinct subsets that have k elements out of an n set, whereas multinomial coefficients represent the number of ways to permute n elements with k1 elements of type 1, k2 elements of type 2, ... etc

---

### Post by antiemptyv on 2007-07-20
true.  the multinomial theorem is a generalization of the binomial theorem.

---

### Post by Paul Miller on 2007-07-24
Others have given you the answer and a pointer to the multinomial theorem, but here's an explanation of *why* it works.

Lets consider first the simpler case of a set of 20 distinct items.  To determine the number of permutations of items in this set, we note that there are 20 choices for the first item, 19 for the second, and so on, for a total of 20!.  If we were dealing with the set {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20}, we would be done.

Now, let's say that 1-10 represent the letter 'a' and 11-20 represent the letter 'b', which is the example you gave.  Let's start by labeling the a's and b's as follows:

```

\{ a_0, a_1, a_2, a_3, a_4, a_5, a_6, a_7, a_8, a_9,
   b_0, b_1, b_2, b_3, b_4, b_5, b_6, b_7, b_8, b_9 \}

```

(The above is LaTeX formatting; the \'s are necessary to escape the curly brackets and the _1, _2, etc, denote subscripts.)

Now that we've attached subscripts to our a's and b's, we can distinguish them, so there are 20! arrangements as per previous logic.  For the sake of simplicity, assume that the permutation we're looking at is the one in the code box above.

Now, if we take away the subscripts on the a's, what we have is this:
```

\{ a, a, a, a, a, a, a, a, a, a,
   b_0, b_1, b_2, b_3, b_4, b_5, b_6, b_7, b_8, b_9 \}

```

The thing is, once we've removed the subscripts, we can't tell if the permutation we started with was our original one, or, say, this one

```

\{
a_9, a_8, a_7, a_6, a_5, a_4, a_3, a_2, a_1, a_0,
b_0, b_1, b_2, b_3, b_4, b_5, b_6, b_7, b_8, b_9 \}

```

It should be clear that once we remove the subscripts from the a's, we can't tell if we started with the first permutation of the subscripted letters or the second.  In fact, we can't tell what order the a's were in at all, and there are 10! ways of putting them in order.  Similarly, once we take the subscripts off the b's, there are 10! possible subscripted permutations we could have started with initially.  Since the order of the a's and b's is independent, we multiply 10! x 10! to get the total number of unsubscripted permutations per subscripted permutation.

Thus, we end up with the result previously mentioned, that there are 20! / (10! x 10!) permutations of the 10 letter a's and 10 letter b's.  This argument, in slightly more generality, is exactly the proof of the multinomial theorem.

---

