---
title: "Awkward Permutation Question"
date: 2007-03-15
forum: Programming Talk
---

### Post by kidders on 2007-03-15
Hi guys,

There are probably better places to post a question like this, but general programming issues often get great responses here, so here we go...

Excuse the silly analogy, but imagine I have many differently coloured eggs, and many differently sized baskets. I'm having terrible difficulty trying to figure out a way to calculate all possible arrangements of eggs and baskets. :confused:

For instance, if I have basket A (capacity: 2 eggs) and basket B (capacity: 3 eggs), I could arrange 8 eggs by putting { 1, 3 } in A, { 2, 4, 7 } in B, and leaving { 5, 6, 8 } behind.

Since, in practice, there will be several hundred "eggs", about 20 "baskets" of various sizes, and some fairly intensive number-crunching after each possible permutation, I'm anxious to find the most efficient way of cycling through them all.

Any suggestions would be appreciated! The eventual destination language will probably have to be PHP, but don't let that stop you posting things in/about other ones. :-)

---

### Post by WW on 2007-03-15
Awkward, indeed!

Suppose you have 200 eggs, and just three baskets, each of which can hold 3 eggs.  The number of possibilities is
> C(200,3)*C(197,3)*C(194,3) = 1974748022991744000 
 where C(N,m) is the binomial coefficient that gives the number of ways of choosing m objects from a set of size N.

If each basket can hold 5 eggs, the number of possibilities is
> C(200,5)*C(195,5)*C(190,5) = 11070898602250411147392449280 
If you have more baskets, the numbers get even bigger.

I hope you have a really fast computer. :)

---

### Post by kidders on 2007-03-15
> **WW said:**
> I hope you have a really fast computer. :)Lol... the numbers do get quite large alright! That's why I need to find a good way of enumerating all the combinations. I'm having difficulty writing an algorithm that doesn't rely on knowledge of what it has done before, to be sure it finds them all. As you showed quite nicely, I'd run out of memory almost immediately if I couldn't throw away *everything* after each iteration.

I assume there's a standard way of doing it, but I haven't been able to find one. :-(

---

### Post by WW on 2007-03-15
Do you understand just how big those numbers are?

The first one is on the order of 10^18.  Suppose you could process one possibility each nanosecond; in other words, you can process 10^9 possibilities per second (this is impossibly fast, of course).  Then it will take 10^18/10^9 = 10^9 seconds to process all the possiblities.  One year is about 10^7.5 seconds, so it will take about 10^1.5 years.  That's almost 32 years.

And the second example will take over a billion times longer than that.

That's why I put the smiley after my comment about the fast computer.

---

### Post by lloyd_b on 2007-03-15
Could you provide a bit more info as to the application?  At first glance, this appears to be a problem that would require a ludicrous amount of processing power/time.  With some idea as to the the actual application, some simplifications may become apparent.

Lloyd B.

---

### Post by yaaarrrgg on 2007-03-15
Why do you need to enumerate all the possibilities?  Or do you just need the number of possibilities?  What is your application doing that could possibly need all these permutations?  Sometimes the best solution to a difficult problem is to avoid it altogether :)

With large numbers though, I'm not sure there's a way to make something like this run in real time... or even at all.  You need to actually caculate the time this will take... There's no guarantee that it's even possible to perform anything close to these calculations with modern hardware.

If modern computers run about 57063 MIPS, how long would it take to run through a list of 20^200 possibilities?

With large amounts of data, the only way I could see this as being remotely possible would be to precompute as much as possible in advance of your application running.  Build a "database" or some structure that can be quickly referenced by a running application. The this can be built over several days, even weeks... in several passes and colllecting the unitial data could take a fairly long time. 

First write a function that tested if a particular arrangement was valid.  Then run through a list of every possible combination.  Each egg can go in one of 20 containers?  Then we can think of this as a N digits (the number of eggs), with 20 possible values (like a base 20 number).  You will need to, assuming you have a powerful enough computer, to precompute all this into, and store each results in a data structure.   Then, as a last step remove the duplicates.

---

### Post by kidders on 2007-03-15
Hi guys,

Thanks for all the replies. :-)

> **WW said:**
> Do you understand just how big those numbers are?Hehe yes. Thankfully, I can throw away trillions upon trillions of them without even considering them. The important part would be the ability to select the ones I *do* want to play around with.

Take a simpler problem for the sake of argument, and imagine I wanted to enumerate all possible lottery tickets. (Although not in the same league as my problem, it's still quite a long list.) In this case, constructing an effectively bijective function that takes a single argument and returns a corresponding group of, say, six distinct integers between 1 and 45 would be fairly trivial. In theory, I could then list all 8,000,000 possible tickets by passing 8,000,000 different (presumably sequential) values to the function, and writing down all the results.

Now imagine I was only interested in certain tickets ... say for instance the ones that included my birthday and my mother's birthday in their selections. Assuming I knew which values to pass to the ticket generator function, I could evaluate and enumerate that subset of all tickets, without having to calculate any of the others.

That describes the sort of thing I've been struggling to write for my *real* problem. If I could define a function that could _in theory_ enumerate all possible egg/basket combinations, I'd be positively ecstatic! Naturally, I'd never be interested in actually *doing* that, but imagining that I could if I wanted to was a short way of describing the idea that all integers i, where n <= i < m would map to a unique combination, and that (m - n) would be the number of possible combinations.

> **lloyd_b said:**
> With some idea as to the the actual application, some simplifications may become apparent.Unfortunately, which combinations I need to select, and many of the parameters that influence the number of possible combinations, will depend on user input at runtime ... so I don't think I'll be able to take short cuts. :-(

> **yaaarrrgg said:**
> Why do you need to enumerate all the possibilities?No, thankfully. I would just like to be *able* to, so I can always find the ones I want, and none will be missing.

The way to handle these kinds of matching scenarios is straightforward where you're pairing single elements of one group with single elements of the other. Equally, it's not so bad where single elements of one group are being grouped with multiple elements from the other. I guess I was hoping (vainly!) that producing a list of all possible collections of several elements from each group in some sort of sensible order would be a well-known complication of one of the easier ones.

I'm beginning to feel as though yaaarrrgg's advice (avoid the problem!!) might be worth taking ... but it won't stop me persevering a little bit longer. Hehe.

---

### Post by cwaldbieser on 2007-03-16
> **kidders said:**
> 
 If I could define a function that could _in theory_ enumerate all possible egg/basket combinations, I'd be positively ecstatic! 
Something like this? [http://www.daniweb.com/code/snippet553.html]("http://www.daniweb.com/code/snippet553.html")

Actually, I read too quickly.  I guess your problem is  more complex than simply permuting a sequence.

---

