---
title: "Efficient Thread creation"
date: 2012-08-09
forum: Programming Talk
---

### Post by proggrammer on 2012-08-09
Suppose I want to create threads for a task, what if it is done by a single thread?

Is it true that multi-thread will do the same job in less time? I could never catch that argument, in what case it does, in what cases it doesn't?

What if I have 'm' cores, then what should be the optimized number of threads which will give the most efficient execution with respect of time.
What are the factors I need to think of, I need a mathematical and rational reasoning.

Does it depend on OS? for example how many should I for linux? for ubuntu? for windows xp?

If there is any conceptual technique to decide that, please help me with your knowledge or pointer to the same.

So if I decide that n number of threads will be best in terms of optimised time execution, so when should I check or decide to create another thread..
the problem is I can repeatedly check it for a constant time, or I can fire the creation only when one thread is dying. Help me it to visualize in C.
So If I prefer the second way, is there anyway in c or java when I can fire that. Any googleable term will also be helpful. Another problem is, I may not know how much the machine is loaded, will number of thread should depend on that? 

I know my language is bad, so harse, but truth is for me knowledge is love. Thanks in advance.

---

### Post by trent.josephsen on 2012-08-09
> **proggrammer said:**
> Is it true that multi-thread will do the same job in less time? I could never catch that argument, in what case it does, in what cases it doesn't?
It depends on what the "job" is. Some tasks can't be done faster by multiple cores. For example, if you have a complex formula f(y) and y is given by another complex formula g(x), then you can't calculate f(y) until you're done calculating g(x). The task itself imposes a linear order on the algorithm; you can't do multiple steps at once because step Z depends on the result of step Y, which in turn depends on the result of step X and so forth.

Other tasks can be easily parallelized to gain performance. The [travelling salesman problem](http://en.wikipedia.org/wiki/Travelling_salesman_problem) can be done in... O(n) time, I think, for massively parallel systems and comparatively small values of n (somebody correct me?). That's not to say that more parallelization never hurts things; there's various types of overhead to worry about as well, which kind of relates to your next question:

> What if I have 'm' cores, then what should be the optimized number of threads which will give the most efficient execution with respect of time.
What are the factors I need to think of, I need a mathematical and rational reasoning.

It all depends on the problem. If you're interested in these kind of questions, Computer Science is the field that tries to answer them. There's no general solution, but some things you might want to consider are the time it takes to set up the parallel algorithm and the cost of communicating between threads (when necessary).

> Does it depend on OS? for example how many should I for linux? for ubuntu? for windows xp?

Theoretically, no. In practice, there may be differences in the amount of thread overhead from one OS to another... I wouldn't worry about that though; you've got your work cut out for you already.

> If there is any conceptual technique to decide that, please help me with your knowledge or pointer to the same.

The questions you've already asked could well be the topic of a Bachelor's-level thesis in Computer Science. Maybe higher. There are plenty of good university programs that will teach you stuff like this. It will take many years. I could be here for weeks just listing everything I know about the topic, which is even less (I'm an engineer, not a programmer).

> So if I decide that n number of threads will be best in terms of optimised time execution, so when should I check or decide to create another thread..
the problem is I can repeatedly check it for a constant time, or I can fire the creation only when one thread is dying. Help me it to visualize in C.
Either I have completely misunderstood your questions so far, or you do not understand how multiprocessing works. Look up some parallel algorithms and get a feel for how parallelization typically happens.

---

