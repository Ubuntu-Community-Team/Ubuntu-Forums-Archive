---
title: "optimization algorithm requries gradient function"
date: 2008-09-01
forum: Programming Talk
---

### Post by monkeyking on 2008-09-01
Hi,
I need a general advise on maximization and minimization algorithms.

I have a function in multiple parameters, that I need to maximize.
Almost all methods I've seen(except nelder-mead), requires a gradient function.

Does anyone have a clue on how to maximize my function when I don't have a gradient.

thanks in advance

---

### Post by CptPicard on 2008-09-01
Are you sure you don't have a gradient? It can actually often be very general in nature ... for example in simulated annealing it is sufficient to have some kind of idea of "neighbours" in parameter space and how the value of the function behaves at those neighbours.

If the value space of the function is really so non-smooth and noisy that local information is not meaningful in guiding search towards extrema, you might be able to try some sort of genetic algorithm search, but even that makes the assumption that two good solutions generally can be combined into a reasonably good or better other solution...

---

### Post by kknd on 2008-09-01
I would recommend genetic algoritms as **CptPicard** did.

Checkout galib, a library in C++ for GAs. Theres also galib-ide, a GUI that ease the use of galib (made by a student that studies on the same university that I study). Its hosted on sourceforge.

---

### Post by Zugzwang on 2008-09-02
Lets get a little bit more general:

It heavily depends on the type of function you have. The case of a combinatorial function is not covered here.

Since you didn't mention the type explicitely, it can be assumed that you mean more or less continuous functions. If they aren't, then the methods you mentioned cannot be applied in a reasonable way anyway.

It might be best if you try Maxima (mathematics framework for symbolic computation) or a similar tool in order to get the partial derivations more or less automatically.

If that turns out to work, use it. If not, there are some tools made by operations research people to perform optimization. They are non-free, however. As already suggested, [evolutionary computation]("http://en.wikipedia.org/wiki/Evolutionary_computation") might be an idea to follow. Note that the mentioned genetic algorithms are just *one* variant of these and depending on your application not necessarily the best one. For example, [evolution strategies]("http://en.wikipedia.org/wiki/Evolution_strategy") are often better (at least for more-or-less not-so-hard problems) because of so-called self-adaptation which is uncommon in genetic algorithms for historical reasons.

Speaking of "best" methods: Note that if you have multiple local maxima in your function, then *none* of the above methods will actually guarantee you to find the global maximum. This is worst for evolutionary computation - They have so many parameters that need to be set correctly in order to get a more-or-less good result. If your function is quite simple to optimize, you are however quite safe.

---

### Post by hod139 on 2008-09-02
> **Zugzwang said:**
>  
Speaking of "best" methods: Note that if you have multiple local maxima in your function, then *none* of the above methods will actually guarantee you to find the global maximum. This is worst for evolutionary computation - They have so many parameters that need to be set correctly in order to get a more-or-less good result. If your function is quite simple to optimize, you are however quite safe.
Simulated annealing and many generic algorithms are a global optimization algorithms.  They tend to be exponential in the number of parameters though, so fail for all but the smallest problems.

Nelder-Mead is the only other optimization algorithm that I know of that does not require gradient information.  It will converge to a local minimum though.  The GNU Scientific library has many of these algorithms implemented.

---

### Post by Zugzwang on 2008-09-02
> **hod139 said:**
> Simulated annealing and many generic algorithms are a global optimization algorithms.  They tend to be exponential in the number of parameters though, so fail for all but the smallest problems.


Do you really mean "generic" instead of "genetic"? Although these two techniques are technically global, they give no *guarantee* of finding the optimum except for the following cases:
[LIST]
[*]Simulating annealing (for some classes of problems) with the right cooling scheme which makes it in fact worse than a brute-force approach.
[*]Genetic algorithms if you *know* the optimum. This is a nice trick that researchers in that area often use in order to generate the illusion of practical applicability. However, how do you know that you've reached the optimum if you didn't construct a toy example for which it is clear? And it's the average case that is exponential, not the worst case which is normally taken into account.
[/LIST]

I wonder where you got that information from ("They tend to be exponential in the number of parameters though") - Normally one sets the parameters in a way that optimization aborts quite early (compared to brute force) and then just takes the best-so-far result. :-)

---

### Post by hod139 on 2008-09-02
> **Zugzwang said:**
> Do you really mean "generic" instead of "genetic"? Although these two techniques are technically global, they give no *guarantee* of finding the optimum except for the following cases: <snip>

Sorry, I wrote too quickly, I did mean genetic.  And I also agree with your points.

> 
I wonder where you got that information from ("They tend to be exponential in the number of parameters though") - Normally one sets the parameters in a way that optimization aborts quite early (compared to brute force) and then just takes the best-so-far result. :-)
Brute force methods are obviously exponential in the size (number of parameters) of the problem.  I shouldn't have said anything about simulated annealing though.  Sorry bout that.  Thanks for keeping me honest.

---

