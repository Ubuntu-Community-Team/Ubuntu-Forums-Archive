---
title: "Project Euler, 190"
date: 2008-04-19
forum: Programming Talk
---

### Post by Lster on 2008-04-19
Hi.

I was looking forwards to Problem 190 on Project Euler, but to put it bluntly, I don't understand it! (Or I thought I did, but I suppose I don't! ;)) The links here, for reference:

[http://projecteuler.net/index.php?section=problems&id=190](http://projecteuler.net/index.php?section=problems&id=190)

EDIT: It suffices to say I was being quite stupid! :)

Thank you,
Lster

---

### Post by nvteighen on 2008-04-19
You're adding x1 + x2^2... The problem states it should be multiplied x1 * x2^2 * ... But I get [P10] = 0...

---

### Post by Lster on 2008-04-19
Thanks! :) That was _so_ stupid of me. :oops:

---

### Post by nvteighen on 2008-04-19
> **Lster said:**
> Thanks! :) That was _so_ stupid of me. :oops:

I make it 3.8941611811810745401e-36 (but this isn't the answer).
Yes, but [3.8941611811810745401e-36] = 0, so you're getting the same as me.

At least to me the language of the problem is absolutely ambiguous and unclear.

---

### Post by Lster on 2008-04-19
I'm pretty sure I understand it now. That point was all that was confusing me - thanks again for that. I'm not sure how to attempt this, though. Calculus doesn't seem possible (at least not at the level I know).

I'll post back if I achieve anything. :)

---

### Post by Lster on 2008-04-19
As we only need from Pm for m is 2 to 15, inclusive, I'll try to brute-forcing it!

---

### Post by nvteighen on 2008-04-19
Sincerely, I don't see what factorization pattern did you follow there.

An no, calculus seem useless here: Yes, you can find extrema by derivating and equating to zero, but there are no functions here! (or maybe a domain-target test may reveal that Pm is a function??).

(Curious, I'm a Philology student... I'm remembering some things I learned in a Engineering-targeted math course).

---

### Post by Lster on 2008-04-19
Sorry about that - it was badly wrong! I am so very careless it seems today! :)

---

### Post by nvteighen on 2008-04-19
> **Lster said:**
> Sorry about that - it was badly wrong! I am so very careless it seems today! :)
Well, it did make sense to me at first... Maybe I'm also careless today! :p

I'm struggling with the logical relationship stated between Sm and Pm. What does that "for which" stands for? Is it a replication (a <-- b, which is what we're assuming here) or an implication (a --> b). Why can't they write things in standard mathematical notation? (or possibly I'm just confusing myself and you too!)

---

### Post by Lster on 2008-04-19
I have been working with my brute-force solution. It gives approximates so I have to manually fine tune it to get it to give the exact values. My list so far, though, doesn't sum to the right answer. I'm going to work from the top to the bottom, finding improvements and eventually I should get the right answer. My prediction is that:

As is obvious, this is not elegant! :)

---

### Post by nvteighen on 2008-04-19
Really interesting, I managed to get P2 mathematically. Actually easy (wow... I didn't realize I could remember these sort of things!):

(P_2 = P<sub>2)
```

P_2 = x_1 * (x_2)^2 (per hypothesis) (1)
m = x_1 + x_2 = 2 (per hypothesis) (2)

x_1 = 2 - x_2 (per (2)) (3)

P_2 = x_1 * (2 - x_1)^2 (substituting (3) in (1)) (4)
P_2 = 4*x_1 - 4*(x_1)^2 + (x_1)^3 (Expanding and distributing) (5)

d(P_2)/d(x_1) = 0 (extrema are defined as the points where slope are equal to zero...) (6)
4 - 8*x_1 + 3*(x_1)^2 = 0 (a straight simple quadratic equation!) (7)

x_1 = (8 +/- sqrt(12))/6 (8)

```

You get two solutions for x_1 and x_2... And you just must choose which gives the greatest P_2...

But of course, with P_3 you get three variables and a cubic equation! (thus, one solution will be a complex number)...

---

### Post by Sinkingships7 on 2008-04-19
for the love of all things holy...

are you all math majors?!

---

### Post by nvteighen on 2008-04-19
> **Sinkingships7 said:**
> for the love of all things holy...

are you all math majors?!
No! Philology student here! :p 

But had a really great math teacher and a good friend that's studying engineering. He has the fault on my interest on programming and math, as he asked me to help him in a robot that was QBasic-driven (oh yes... we used LPT1 and a Win3.1 box).

---

### Post by Lster on 2008-04-19
Hi

I also solved P[2] algebraically. But can't solve any higher P. I _think_ I am close to a solution. We'll see in time! ;)

[QUOTE=Sinkingships7]for the love of all things holy...

are you all math majors?![/QUOTE]

I'm doing Maths and Further Maths at AS level right now.

---

### Post by Lster on 2008-04-19
I've solved it! My trial and improvement solution wasn't actually too slow! nvteighen, if you would like I'd be very happy to PM the answer to you. Thanks again for your help! :)

---

### Post by nvteighen on 2008-04-20
> **Lster said:**
> I've solved it! My trial and improvement solution wasn't actually too slow! nvteighen, if you would like I'd be very happy to PM the answer to you. Thanks again for your help! :)
Just PM it! I want to see this!

---

### Post by Lster on 2008-04-20
OK! :) I forgot to mention that anyone else is also welcome. But really, it is more fun doing than watching!

---

### Post by Lux Perpetua on 2008-04-20
> **Lster said:**
> I've solved it! My trial and improvement solution wasn't actually too slow! nvteighen, if you would like I'd be very happy to PM the answer to you. Thanks again for your help! :)So did you end up finding a closed form expression for P[m]?

---

### Post by Lster on 2008-04-20
No, not yet at least. I'll be looking into it, though. Have you got any ideas?

---

### Post by Lux Perpetua on 2008-04-20
Sure, here are a couple hints:

1. Suppose you know P[m], which is the maximum value of (x1)^1 * ... * (xm)^m given x1 + ... + xm = m. How does the answer change if you replace that condition by x1 + ... + xm = y, where y is an arbitrary positive real? 

2. Suppose you want P[m+1], which maximizes (x1)^1 * ... * (x(m+1))^(m+1) given x1 + ... + x(m+1) = m+1. Given the value of x(m+1), how would you choose the other m numbers x1, ..., xm to maximize the expression?

That's the elementary route, and the way I originally worked it out. If you're familiar with Lagrange multipliers, though, then you can basically get the answer in one shot. Lagrange multipliers are usually taught as part of introductory multivariable calculus.

---

### Post by Lster on 2008-06-08
Going through the Project Euler problems I've completed this far, I remembered this one. I also made a note find an algebraic solution to it and am very intrigued because I can't see how to go about it.

All the terms in x seem to form an arithmetic sequence. The total of which would be ½m(m+1)k and would equal m. Therefore it appears:

k = 2m / (m² + m)

Which *appears* to work!

So from that, any x[i] in a tuple of length m equals 2im / (m² + m). And of course that gives an O(n) algorithm. I just can't explain this with algebra...

---

### Post by Lster on 2008-06-09
*Bump*

---

### Post by descendency on 2008-06-09
> **nvteighen said:**
> An no, calculus seem useless here: Yes, you can find extrema by derivating and equating to zero, but there are no functions here!.

Pm and m are functions. However, they are not functions of single variables, making the calculus of them very complicated.

---

### Post by Lux Perpetua on 2008-06-10
> **Lster said:**
> Going through the Project Euler problems I've completed this far, I remembered this one. I also made a note find an algebraic solution to it and am very intrigued because I can't see how to go about it.

All the terms in x seem to form an arithmetic sequence. The total of which would be ½m(m+1)k and would equal m. Therefore it appears:

k = 2m / (m² + m)

Which *appears* to work!

So from that, any x[i] in a tuple of length m equals 2im / (m² + m). And of course that gives an O(n) algorithm. I just can't explain this with algebra...This is right, according to my quick mental calculation. Did you try any of what I said in my last post?

If it seems confusing, think of it as a way to reduce this m-dimensional constrained optimization problem to a one-dimensional problem plus an (m-1)-dimensional problem. Here's the strategy: pick one of the variables,  say x_m, and fix it at an arbitrary constant. Now optimize your function in the other (m-1) variables, assuming x_m is this fixed value. The optimum value will generally be an expression (hopefully simple) depending on x_m. Now, allow x_m to vary and choose x_m to optimize this expression. This will solve the original m-dimensional problem.

But how do you "optimize your function in the other (m-1) variables, assuming x_m is this fixed value"? Why not apply the same strategy? It is naturally recursive, and the closer the (m-1)-dimensional problem is to the original m-dimensional problem, the more effective recursion will be. 

In this problem, the (m-1)-dimensional problem is essentially just to find P[m-1], except x_1 + ... + x_(m-1) is constrained to be a fixed number that's not necessarily m-1 (but how does changing the constraint this way affect the problem?). Thus, you should expect a recursive formula for P[m] in terms of P[m-1], which you can solve to obtain your explicit solution.

---

### Post by descendency on 2008-06-11
> **nvteighen said:**
> Really interesting, I managed to get P2 mathematically. Actually easy (wow... I didn't realize I could remember these sort of things!):

(P_2 = P<sub>2)
```

P_2 = x_1 * (x_2)^2 (per hypothesis) (1)
m = x_1 + x_2 = 2 (per hypothesis) (2)

x_1 = 2 - x_2 (per (2)) (3)

P_2 = x_1 * (2 - x_1)^2 (substituting (3) in (1)) (4)
P_2 = 4*x_1 - 4*(x_1)^2 + (x_1)^3 (Expanding and distributing) (5)

d(P_2)/d(x_1) = 0 (extrema are defined as the points where slope are equal to zero...) (6)
4 - 8*x_1 + 3*(x_1)^2 = 0 (a straight simple quadratic equation!) (7)

x_1 = (8 +/- sqrt(12))/6 (8)

```

You get two solutions for x_1 and x_2... And you just must choose which gives the greatest P_2...

But of course, with P_3 you get three variables and a cubic equation! (thus, one solution will be a complex number)...
x_2 = 2-x_1

x_2 = 12/6 - (8 +/- sqrt(12))/6
    = (4 -/+ sqrt(12))/6
either, 
x_1 = (8 + sqrt(12))/6
x_2 = (4 - sqrt(12))/6

or 

x_1 = (8 - sqrt(12))/6
x_2 = (4 + sqrt(12))/6


The first yields P_2 = 0.015242 and the second yields P_2 = 1.16994

given the values x_1 = 2/3 and x_2 = 4/3, P_2 = 1.18519

granted [P_2] = 1, but it would seem there is a flaw in your logic.

I'm not sure if I did it right, but using Lagrange multipliers (I had a mediocre/terrible Mutli-variable Calculus teacher) I got 2/3 and 4/3.

---

### Post by Lster on 2008-06-11
The error is in this line:

> x_1 = (8 +/- sqrt(12))/6

That should be x[1] = [8 ± &#8730;16] / 6
Which gives x[1] = 2/3 and x[2] = 4/3 and the answer 32/7.

---

### Post by Lster on 2008-06-11
[QUOTE=Lster]...[/QUOTE]

Which fits in with my hypothesis above. k = 2m / (m² + m) would give k = 2*2 / (4 + 2) = 2/3. x[1] = k = 2/3 and x[2] = 2k = 4/3...

---

