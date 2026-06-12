---
title: "Farming Python Script"
date: 2011-12-05
forum: Programming Talk
---

### Post by Glenn Jones on 2011-12-05
Dear All,

I'm just dipping my toes with parallel programming and I would like your advice for the best strategy for optimising the process.

I have python/fortran code which processes data and takes approximately 20 s per event. Unfortunately I have  15,000+ of these events which ends up taking hour/days to process. Currently the code just loops over these events. I have a multi-core machine and I would like use all of the cores as opposed to the single core being used. My idea is to split the code up into chunks and distribute in to the cores. 

My question is what is the best way of achieving this? and which packages should I be looking at using?

---

### Post by cgroza on 2011-12-05
Regarding Python, I think you should take a look at : [http://wiki.python.org/moin/ParallelProcessing](http://wiki.python.org/moin/ParallelProcessing)

Also, Haskell and functional languages in general are really good with parallel programming and actually make it easier to realize it.
In Haskell, all you need to do is flip a compiler switch.

---

### Post by ofnuts on 2011-12-06
> **Glenn Jones said:**
> Dear All,

I'm just dipping my toes with parallel programming and I would like your advice for the best strategy for optimising the process.

I have python/fortran code which processes data and takes approximately 20 s per event. Unfortunately I have  15,000+ of these events which ends up taking hour/days to process. Currently the code just loops over these events. I have a multi-core machine and I would like use all of the cores as opposed to the single core being used. My idea is to split the code up into chunks and distribute in to the cores. 

My question is what is the best way of achieving this? and which packages should I be looking at using?If your data comes from files and you don't have any dependency on the whole file to process one piece of data, then chunk your data in multiple files and run several processes in parallel to process them. Each or you cores will then be busy running a process.

You can also investigate usingthe SSE instructions of the x86 architecture, or look into specialized libraries that may be more efficient than your code  (because they use SSE) (or in the long term, at OpenCL to tap the computing power of your graphics card).

---

### Post by lukeiamyourfather on 2011-12-06
Long story short you would want a process (or thread) to handle each event and a queue to manage the tasks. When one process (or thread) finishes the next item on the queue starts.

[http://docs.python.org/library/queue.html](http://docs.python.org/library/queue.html)
[http://docs.python.org/library/multiprocessing.html](http://docs.python.org/library/multiprocessing.html)

I created a script when faced with a similar situation as you are now. I'm not a developer but you can see how I did it here.

[http://whenpicsfly.com/wordpress/?p=17](http://whenpicsfly.com/wordpress/?p=17)
[http://whenpicsfly.com/wordpress/?p=81](http://whenpicsfly.com/wordpress/?p=81)

---

### Post by thaelim on 2011-12-09
One major caveat with threads in Python - they aren't truly parallel. That is to say, only one thread executes at a time, even on a multi-core machine. The multiprocessing module gets around this problem. Just don't want you to waste time implementing a computationally intensive task in Python using threads...

---

