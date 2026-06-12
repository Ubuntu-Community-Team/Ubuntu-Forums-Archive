---
title: "Poisson distribution"
date: 2006-02-15
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-15
I am simulating an event where users come into the pool randomly starting at time T=0, i.e. For Example, 2 users came at T= 0 into the the pool,  3 users came at T= 1 into the the pool, 5 users came at T=2 ,..........,54 users came at T=45 etc. As cumulative number of users goes above 1024, we stop the process.

I want to mimic such kind of distribution using poison traffic ( a bell shaped curve). I looked into wikipedia and some other tutorials but I wasn't sure how many parameter does the above kind of distribution would require. 

Could somebody put some light on this issue.

PS:: This is not exactly a programming issue but since I was using it in one of the programs, I thought somebody might have used similar thing in past and could help. Thanks.

---

### Post by jpkotta on 2006-02-15
Poisson distributions have only one parameter, generally called lambda, which is the mean number of events per unit time.  I think I can be of some help, but I'm much more comfortable with continuous variables than discrete ones.  I think I can get an algorithm for generating Poisson events.

As stated in the Wikipedia article, the time between events has an exponential distribution.  If we could generate times with an exponential distribution (a random process), we can simply sum the times modulo the "sample times" to get the Poisson variable (the count).  Example: T1 T2 ... TN are the times between the events.  Event 1 occurred at T = T1, event 2 occurred at T = T1 + T2, event 3 occurred at T = T1 + T2 + T3, and so on.  The number of events between t = 0 and t = 1 is a Poisson variable.  In other words, if T1 + T2 + ... + Tk < 1 and T1 + T2 + ... T[k+1] > 1, then k events have occurred between time t = 0 and t = 1.

How do we get an exponentially distributed variable?  We transform one random variable that we know how to generate into the other, by means of a function T = g(U).  Take a uniform variable U on [0,1].  The CDF of U is FU(u) = u (0<u<1).  The CDF of T is FT(t) = 1-exp(-lambda t) (t>0).  Now, we need the Pr(U>=u) to be the same as Pr(g(U) >= g(u)) = Pr(T>=t) (note: g(u) must be monotonic increasing).  But these are just the CDFs, so u = 1-exp(-lambda t) -> t = g(u) =  -ln(1-u)/lambda.  So generate a bunch of uniformly distributed (and independent) u's and apply the above function to get exponentially distributed t's.

Edit: Added note about monotonicity of g(u).
Edit: Wrong definition of lambda.

---

### Post by jpkotta on 2006-02-22
For some reason, this bugged at me and I had to come back to it.  [Here]("http://www.scilab.org/doc/demos_html/node284.html") is a Scilab (Matlab) solution.  It is equivalent to mine, but more efficient, because you transform the threshold instead of transforming every event.

---

### Post by krypto_wizard on 2006-02-25
In my case there is 1 user coming to the pool on an average. As the number of users in the pool become 1024 I stop.

Starting at time T =0 to T=1024, I want number of users coming on to the pool every second.

I did not understand much from your posts. Could you explian with these parameters.



[QUOTE=jpkotta]For some reason, this bugged at me and I had to come back to it.  [Here]("http://www.scilab.org/doc/demos_html/node284.html") is a Scilab (Matlab) solution.  It is equivalent to mine, but more efficient, because you transform the threshold instead of transforming every event.[/QUOTE]

---

### Post by jpkotta on 2006-02-26
It sounds like you want the number of users per second to be a Poisson variable (note that this is not a bell curve, as that is usually how a Gaussian is described).  If you have 1 user per second on average, lambda = 1 (user/sec).  So generate a Poisson variable with lambda = 1 and simulate.

Wait...I re-read the first post.  Is the traffic accellerating?  In that case, I think you're in the realm of non-stationary random processes.  You could probably just vary lambda and make it an "instantaneous average rate".

---

