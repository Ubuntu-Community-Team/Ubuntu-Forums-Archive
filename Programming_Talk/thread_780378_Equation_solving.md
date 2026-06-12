---
title: "Equation solving"
date: 2008-05-03
forum: Programming Talk
---

### Post by CptPicard on 2008-05-03
A question for math geeks better than me...

For a long, long time I've been working on a solution to a certain problem that you can check out here:

[http://forum.sbrforum.com/handicapper-think-tank/72062-multiple-exclusive-outcome-kelly-stake.html](http://forum.sbrforum.com/handicapper-think-tank/72062-multiple-exclusive-outcome-kelly-stake.html)

The post of interest is [#11]("http://forum.sbrforum.com/handicapper-think-tank/72062-multiple-exclusive-outcome-kelly-stake.html#post720889").

It is claimed that the second equation turns into an nth degree polynomial, but frankly, I haven't quite been able to see how. I fail to see where the degrees come from considering that there isn't obvious multiplication of x with itself, and the sum just keeps x at first degree.

So... I need to solve for x. Probably can't be done in closed form, but a numerical way to do it would be great :)

(pi, wi are constants and i ranges from 1 to n).

---

### Post by WW on 2008-05-03
Multiply both sides of the equation by (1-x)*(1+x*w1)*(1+x*w2)*...*(1+x*wn). (This is the product of all the denominators.)  The result is a polynomial equation for x.

---

### Post by CptPicard on 2008-05-03
LOL, insightful thing to do really (and dumb of me not to get it). Thanks :) You have no idea how much work has gone into the underlying problem here -- now I'll be able to get a lot of interesting numbers :)

---

### Post by nvteighen on 2008-05-03
> **WW said:**
> Multiply both sides of the equation by (1-x)*(1+x*w1)*(1+x*w2)*...*(1+x*wn). (This is the product of all the denominators.)  The result is a polynomial equation for x.

What if one factor gets zero (e.g. x = 1 -> 1-x = 0)? Wouldn't that imply a division-by-zero at the original equation?

I have the vague idea this should be done with interval analysis... But not sure and I may be confusing myself with polynomial inequalities.

---

### Post by CptPicard on 2008-05-03
We'll see what comes of it. I'm working out the coefficients of the resulting polynomial atm so that I can actually put it into some kind of a solver. Then again, it's division by zero that is undefined, not multiplication by potentially zero, no? You can solve 4/x = 2 just fine by multiplying by x and then dividing by 2 :)

---

### Post by nvteighen on 2008-05-03
> **CptPicard said:**
> We'll see what comes of it. I'm working out the coefficients of the resulting polynomial atm so that I can actually put it into some kind of a solver. Then again, it's division by zero that is undefined, not multiplication by potentially zero, no? You can solve 4/x = 2 just fine by multiplying by x and then dividing by 2 :)

Forget what I wrote. I went to my algebra books and saw I was messing everything up... Sorry.

Anyway, I get an n-th degree polynomial, not (n-1)-th...

---

### Post by CptPicard on 2008-05-03
I'm still working through a small example to see whether there are some sort of patterns in the structure that lets me simplify what the coefficients look like... it looks as though the coefficients are sort of combinatorially bothersome to compute.

---

### Post by Jessehk on 2008-05-03
You posted this in **Programming Talk** because...?

---

### Post by CptPicard on 2008-05-03
Because there is no Mathematics Talk and because the most math-capable geeks hang out in this section :p -- and because finding a numerical solution by some method approaches programming.

---

### Post by Can+~ on 2008-05-03
> **CptPicard said:**
> Because there is no Mathematics Talk and because the most math-capable geeks hang out in this section :p -- and because finding a numerical solution by some method approaches programming.

Sometimes I wish there were LaTeX equations on this forum :(.

---

### Post by CptPicard on 2008-05-03
Allright, the coefficients of the polynomial have this nice habit of having sums with 1.3e1000 terms in my real-world example (polynomials of degree around 3500 or so), and I don't think it's getting any prettier by mangling the math, as esp. in the nominator on the RHS you get these sorts of very long multiplications of different wi which just refuse to cancel or anything with stuff on the LHS.

So now this really turns into a programming/approximation problem... I suspect there is no fast enough method for finding the root of the equation, but I'm listening to suggestions here.. ;)

---

### Post by Dancingwllamas on 2008-05-03
Depending on what your definition of "fast enough" is, [Newton's Method](http://en.wikipedia.org/wiki/Newton%27s_Method) may work. Just be careful of your error when taking the numerical derivatives (don't make your offset h too close to the machine epsilon, or your error gets very large).

---

### Post by evymetal on 2008-05-04
Ah, game theory ...

If you're trying to find the roots for a one-off then I'd suggest using scipy in python - they've got a huge range of optimisation techniques for scalar polynomials.

I'd also try plotting it to check for any unusual behaviour.


Re: Newton-raphson optimisation - remember that this will only find **local **minimisers of the function!

If it's for something important (which game theory normally is) then you'd probably want to divide the region you want to optimise up into segments and check them manually. Obviously you have to choose your sections carefully - that's up to you. You only have a probabilistic chance of finding the global minimiser, though. 

So far as I know there isn't a deterministic algorithm to find the global minimiser (someone tell me if there is).

(but if you check the case of placing a bet of 0 then you'll always avoid losing utility - assuming that it's a single round game and you don't lose utility by not placing a bet)

- I normally use golden section optimisation for linear functions.

---

### Post by Dancingwllamas on 2008-05-04
I don't believe there is a known deterministic algorithm for finding a global min. with a non-linear function. In the non-linear realm, you have to take what you get (or iterate over a bunch of starting points and hope to hit the global min.). :/

Feel free to correct me if I'm wrong, as I've really only been learning this stuff in the past semester (I don't have years of experience with it).

---

### Post by CptPicard on 2008-05-04
Actually, Newton's at least *initially looking* seems to work. I get a nice convergence in just 6-7 iterations. I had actually already disregarded Newton's as "too simple" when I figured out how difficult the polynomial is... seemed to sort of mis-remember that it was just for polynomials ;) The derivative of the function is, fortunately, easy.

Also, one should remember that if you look at the problem that I'm doing, it is obvious that there is *one* optimal way to stake your bankroll for max growth. So therefore, there is just one optimal x between 0 and 1. I would be very very surprised if there were local optima such that, say,  it wouldn't hold that global optimum is betting 5% of your bankroll and it's just monotonously worse in both directions.. would make sense no?

---

### Post by Dancingwllamas on 2008-05-04
Glad the Newton Iteration is working so well. :)

I think I understand what you are asking:

There is going to be (at least) one global optimum (the "optimal solution") that is better than all the others, but it's not guaranteed that Newton's Method will find it first. Every local min is an "optimal" point (so, there are probably many "optimal" points for an n-degree polynomial of decently sized n), so you can't guarantee that a specific optimal point is globally optimal. The only thing you can say is that one optimal point has a better value than another optimal point.

---

### Post by CptPicard on 2008-05-04
Yes I know, in the general case, but if this equation I'm working on is supposedly representing anything reasonable, as it should, then by all means it does not make any sense that any other possible assignment of x could *be* a local optimum without being the global one. :) I mean.. if the equation is right, it would be crazy to assume that there are various values for x that are (only) in their local neighbourhood optimal. Either you are a global optimal value or then you're over-betting or under-betting, and in both cases the only remedy is to move towards the optimum, which is the one and only.

The numbers I'm getting are looking great so far, so it's all good. The only worry is that theoretically in bets where expectancy is under 1, Kelly should (I think) return a negative, and this is not the case (although these are nearly undefined cases to begin with). But that is a minor issue for the time being, and I'm working on it... the general method seems very satisfactory.

EDIT: Of course I may be wrong in my reasoning, please correct me if I'm wrong. But if the equation states that the x that produces zero is *the* optimum and I'm getting arbitrarily close to zero, I have trouble believing there are multiple optimal points... and that it would be impossible to distinguish which is better, anyway.

---

### Post by evymetal on 2008-05-05
> **CptPicard said:**
> But if the equation states that the x that produces zero is *the* optimum and I'm getting arbitrarily close to zero, I have trouble believing there are multiple optimal points... and that it would be impossible to distinguish which is better...

Having plotted a range of expectation graphs I agree that they always seem to only have one point where the derivative is 0 - it must be because of the logarithm.

---

### Post by Mickeysofine1972 on 2008-05-06
> **CptPicard said:**
> 
It is claimed that the second equation turns into an nth degree polynomial


Wash your mouth out with soap! Disgraceful speech! LMAO

(Wish I knew what the hell that was !)

Mike

---

### Post by CptPicard on 2008-05-06
> **evymetal said:**
> Having plotted a range of expectation graphs I agree that they always seem to only have one point where the derivative is 0 - it must be because of the logarithm.

Yes, and even more interestingly, the derivative of the expectation of the utility does have a nasty discontinuity that approaches zero from the negative side of the x axis as optimal stake approaches 1 (the game gets better), but if you start your Newton for discovering the zero of the derivative from somewhere around 0+, you'll never have the zero on the other side of the discontinuity of the derivative... you should always be with the zero along a well-behaved curve.

---

### Post by Mickeysofine1972 on 2008-05-06
Hey, on a serious note, I dont think I've ever come across a tutorial on how to interpret equations into code.

Would anyone like to make a howto or at least contribute to one?

Mike

---

### Post by Dancingwllamas on 2008-05-06
That makes a lot more sense. It appears you would be correct. Sorry I misunderstood your question (most of the time I see that question, people misunderstand the general case).

Glad it seems to work out. :)

---

### Post by CptPicard on 2008-05-07
> **Mickeysofine1972 said:**
> Hey, on a serious note, I dont think I've ever come across a tutorial on how to interpret equations into code.

Well, most of the time you just "interpret" them by typing the math up ;p

I'm not quite sure I understand the question.. :)

Now, if you want to actually solve them, you need various numerical methods, of which Newton's method is probably the simplest (although prone to breakage, which we've been discussing here).


> **Dancingwllamas said:**
> Sorry I misunderstood your question


Np, I appreciate all the scepticism I'm getting. This kind of stuff always bites you when you least expect it, and I don't want to be bitten, although this special case seems to be benign :)

---

