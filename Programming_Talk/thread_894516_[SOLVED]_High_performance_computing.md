---
title: "[SOLVED] High performance computing"
date: 2008-08-19
forum: Programming Talk
---

### Post by Qtips on 2008-08-19
Hi,

I ask for advice of the people here. I'm a computational physicist. I know Maple, Mathematica and Matlab software but i want to move on for something more, on high performance computing on clusters. 

What's the main/best language to learn to be effective in this field ?

After a little search on google, the battle is between Fortran/C/C++ with a newcomer Python.

I also need to know about MPI, openMP and the like...

But i don't know where to start...why do you guys are suggesting ?

Thanks

---

### Post by kknd on 2008-08-19
Edit.: Ops, forgive my stupid old post that was here. The standard OpenMP can't deal with multiple machines, only local parallelism.

---

### Post by pmasiar on 2008-08-19
Python was designed **exactly** for people like you: scientist, who needs to glue together program from file parsing, C-libary calls, and programming in between. Who has other expertize, and being a competent in CompSci is just the mean, not the goal.

Compared to that Fortran is 50 years old, and it shows. C was designed for systems programmers, to write super-efficient kernel and system utilities, and is not very forgiving for non-experts (it's easy to blow your foot AND head off in one shot).

Python is so popular with scientist, it has own  SciPy conference, separate from more general PyCon. numpy is python binding for effective C libraries, and you can use effective typed arrays instead of generic lists of common python - but only if you need the speed! 

So with Python, you have all the flexibility of  modern dynamic language, and speed of C libraries (when you need them).

But of course take a look what other people use. Physicists used Fortran forever (and have zillion of libraries), bioscience (where I work) is luckier in sense that they get hand on computers only lately, so they don't have to deal with huge legacy code and can develop using the most current technologies.

It also depends how interested you are in computing part of the problem: If something is lacking, are interested to dive in (to C code), or you will be just fine to use same old Fortran utilities as your PI did?

I know that gurus in HPC in our university mix Python (when then can get away with it) and C (if they have to). It's almost the only place (in our uni) which advertises for Python expertize.

---

### Post by slavik on 2008-08-19
Look into Haskell and Parallel Haskell. As for OpenMP, I don't know much (yet) about it, but so far I know that it is a Shared Memory system, making programming on a cluster not simple.

As for MPI, it is ok, but I really dislike have to put code in to communicate with other nodes to report results and such.

Another thing worth considering is Mosix, unfortunately, the latest Mosix (Mosix2) does not have a distributed file system (OpenMosix which works only on 2.4 kernels does though). Mosix is good in the sense of "fork and forget", it automatically moves processes to other nodes for load balancing, but you get a hit with SysV IPC because Mosix will migrate the remote process to the mother node for the IPC.

I suggest looking into Hadoop which has it's own distributed filesystem. This is the open source competitor to Google's MapReduce (the lead developer of Haddop works at Yahoo).

---

### Post by Qtips on 2008-08-19
> **pmasiar said:**
> 
It also depends how interested you are in computing part of the problem: If something is lacking, are interested to dive in (to C code), or you will be just fine to use same old Fortran utilities as your PI did?


I really love to code mathematics, so if somebody is lacking, i want to code it, but i don't want to reinvent the wheel either :). If something works good and it's optimized for speed, i will use it.

I know that Python is a really great language to learn, but in the HP (high performance) computing discipline, it's really not the fastest language. I can gain time in developing but not really in execution...and because i have only one life (like all of us), i don't want to loose time.

In HP computing, it's always the same...we need more speed and calculation power to handle complex problems.

Is there an MPI implementation with Python too ?

Thanks

---

### Post by pmasiar on 2008-08-19
> **Qtips said:**
> I know that Python is a really great language ... really not the fastest language. I can gain time in developing but not really in execution...and because i have only one life (like all of us), i don't want to loose time.

...but not all the tasks are in the bottleneck for speed. 90% are not, so solving them quickly in Python gives you more time to optimize in C that 10% where speed can make difference. 

if numpy uses exactly the same library like your C code does, how much speed you'll gain to do everything in C? How much longer it will take to code it in C?

I am not selling you Python, I am trying to suggest questions you need to ask yourself before you can decide what fits your needs best. Do as you wish, my salary does not depend on your decision :-)

Just FYI: Even Google uses Python or orchestrate their servers.

---

### Post by kknd on 2008-08-19
> **slavik said:**
> Look into Haskell and Parallel Haskell. As for OpenMP, I don't know much (yet) about it, but so far I know that it is a Shared Memory system, making programming on a cluster not simple.

Thats true, my post was stupid (I removed it now =) ). There seems to exist a "Cluster OpenMP" by Intel (proprietary), but I agree with you.

---

### Post by slavik on 2008-08-19
your post is not stupid, OpenMP is nice, because it can unroll loops and parallelize them at runtime with a single line of a macro, instead of coding the same thing yourself.

OpenMP is great for an SMP system where you can say "this piece of code can be parallelized."

MPI on the otherhand is a bit of a beast since the most used functions (send/receive messages) have like 7 arguments.

---

### Post by Qtips on 2008-08-19
Thanks Pmasiar,

I will look forward with Python with its numpy/scipy modules. Do you know if there exist a well documented analogue of MPI/openMP for Python ?

---

### Post by pmasiar on 2008-08-19
[http://sourceforge.net/projects/pympi/](http://sourceforge.net/projects/pympi/)

I don't think situation is settled - and I don't follow it closely either.

I know there is big discussion on python-dev what would be best approach to multiprocessing and threads. Google for "Python GIL" and you get a sample :-)

Problem is, elimination of GIL slowed down single-process Python - not acceptable. And different application benefit from different approaches.

Guido IIUC suggests to use multiple processes:

> Nevertheless, you're right the GIL is not as bad as you would initially think: you just have to undo the brainwashing you got from Windows and Java proponents who seem to consider threads as the only way to approach concurrent activities.

Just because Java was once aimed at a set-top box OS that didn't support multiple address spaces, and just because process creation in Windows used to be slow as a dog, doesn't mean that multiple processes (with judicious use of IPC) aren't a much better approach to writing apps for multi-CPU boxes than threads.

Just Say No to the combined evils of locking, deadlocks, lock granularity, livelocks, nondeterminism and race conditions.

---

### Post by Lster on 2008-08-19
I would agree with slavik on this. But to compare language speed and memory usage, you might want to refer to The Computer Language Shootout:

[http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/)

For example, comparing GCC (C) and GHC (Haskell):

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=ghc](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=ghc)

And Python in comparison to GHC:

[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=ghc&lang2=python](http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=ghc&lang2=python)

You can pick the CPU architecture that you plan to run your simulations (or whatever else...) on, and compare languages on that. As for dealing with clusters, I'm afraid I can't help - I don't really know which of these languages are best for that.

---

### Post by spooner on 2008-09-11
> **pmasiar said:**
> Python was designed **exactly** for people like you: scientist, who needs to glue together program from file parsing, C-libary calls, and programming in between. Who has other expertize, and being a competent in CompSci is just the mean, not the goal.

Compared to that Fortran is 50 years old.

Well, Fortran was designed by Physicists for Physicists and I learnt it during undergrad. It is old but the tools available for optimisation/parallisation/etc are massive. Good quality Fortran (Intel or PGI) compilers are still 1000's of £ when you are deploying to a cluster. I would agree that Python is easier to learn use and deploy but it is only good for scientists who want to dabble with programming to get something done/build a trial program... if you are moving into the relm of parallisation on HPC the admins will not be happy if your code it not optimised to use the fewest processor seconds.
Basically, I would advise that you talk to the HPC guys at whatever institute you are with/going to use. They will advsise you what they have and what they recommend.

---

### Post by Paul Miller on 2008-09-11
I know this is marked [SOLVED] already, but I have another data point to inject into the discussion. 

To the OP: You mentioned some expertise in *Mathematica* programming.  You might want to look into *gridMathematica*, in that case.

While I know proprietary solutions tend not to be popular here because it's a Linux forum, I really think *gridMathematica* might be investigating.  I've used *Mathematica* myself, and I've found it to be one of the highest-quality mathematical packages available.  I haven't used *gridMathematica* specifically, but I suspect it's pretty good just based on the fact that it's based on *Mathematica*.  I'd definitely at least look into pricing and see if it's reasonable for you.

---

### Post by samjh on 2008-09-11
> **pmasiar said:**
> ...but not all the tasks are in the bottleneck for speed. 90% are not, so solving them quickly in Python gives you more time to optimize in C that 10% where speed can make difference. 

if numpy uses exactly the same library like your C code does, how much speed you'll gain to do everything in C? How much longer it will take to code it in C?In practice, you won't recover the speed lost in Python so simply.

For example, in Slavik's matrices multiplication challenge, the implementation written in Python + Numpy (Tamoneya's submission) = 18.644s.  Implementation using C++ (Nova's submission) = 11.634s.  Assembly implementation (Qikink's one) = 2.188s.  All are single-threaded.

The difference is very significant if you're doing large-scale number-crunching.  If a set of simulations takes 3 days to perform in Python + Numpy, and 2 days to perform in C++, I'd go for C++.

But then, I'm far from being an expert in Python. :)

> I am not selling you Python, I am trying to suggest questions you need to ask yourself before you can decide what fits your needs best. Do as you wish, my salary does not depend on your decision :-)
Well, you might not think so, but you ARE sounding like a very good Python salesman.  I work (or used to, until I got laid off) in marketing, and can pick out a marketer or salesperson pretty well. ;)

---

### Post by PeterBBB on 2008-09-14
> i want to move on for something more, on high performance computing on clusters. 

One more suggestion, take a look at the open source 'Cactus'.
_[http://www.cactuscode.org/About](http://www.cactuscode.org/About)_
_[http://www.cactuscode.org](http://www.cactuscode.org)_

*Cactus provides computational scientists and engineers with a collaborative, modular and portable programming environment for parallel high performance computing*

---

### Post by drubin on 2008-09-14
I suggest you take a look at erlang. It is designed for high performance clustering.

---

### Post by Wybiral on 2008-09-14
> **samjh said:**
> In practice, you won't recover the speed lost in Python so simply.

Why not? If you write your matrix multiplication function in C and use it in your Python program, you can benefit from the C speed but with a higher level interface and design.

---

### Post by Alberto_Coglin on 2010-01-07
Actually when i was very blank and blindly searching for what does computing process is about, i came to know about a concern named    [cloudslam09]("http://cloudslam09.com")  who are really good enough in computing jobs and helped me out with a high performance computing. I think this information or their site might be useful for anyone else too.

---

### Post by Ryan05 on 2010-03-05
I had heard a lot about HPC. Its excellent. I am very much interested about computing. I use to attend many conferences, since it would help to develop my career. Recently I attended a cloud computing conference and gathered a lot information. Its a             [COLOR=#000000]**[2nd Annual Virtual Conference]("http://cloudslam10.com")**. It was hosted [/COLOR]online March 23-25, 2009 by **cloudslam team.**
[COLOR=#000000]



[/COLOR]                                  

 





                                                                   [COLOR=#000000]
[/COLOR]

---

