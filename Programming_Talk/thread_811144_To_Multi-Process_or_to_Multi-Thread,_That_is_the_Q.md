---
title: "To Multi-Process or to Multi-Thread, That is the Question"
date: 2008-05-28
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-28
What is the best choice?

I recall reading somewhere that *nix systems were better at utilizing forked processes whereas Windows had an edge when multi-threading. To give a crappy example (and I don't recall the specifics of the article I was reading) they compared two sets of code which completed the exact same task but substituted threading and forking (that sounds naughty) and ran both on Windows and Linux. They used NO optimization to make sure neither had an edge. The comparison was something like:

Multi-Processing: Linux = 0
Multi-Processing: Windows = 8

Multi-Threading: Windows = 2
Multi-Threading: Linux = 3

Where the lower the number, the slower it was. Think of it like...number of seconds to complete the benchmark.

The conclusion I reached was that if you were going to write a *nix only program, then fork() processes, otherwise use Multi-threading since *nix is almost as good as Windows at doing it anyways.

So? What's the REAL deal? Does it matter which you choose? Have I totally missed the boat and don't know what the heck I'm talking about? (likely, LOL)

---

### Post by kknd on 2008-05-28
fork() is great, but uses more resources than multi-threading. 
For larger programs, like a server that needs to handle various clients, multi threading scales better (well, I think so =) ) than creating various process.

A good article: [http://developers.sun.com/solaris/articles/subprocess/subprocess.html](http://developers.sun.com/solaris/articles/subprocess/subprocess.html)

---

### Post by Tuna-Fish on 2008-05-28
There is a huge conceptual difference between process/thread multiprocessing. The speed issues are really irrelevant, what you should be concentrating on is how your problem maps to the models.

Processes are usually favored on linux because when you use them you have to define clear boundaries and the program becomes easier to debug, while with threads it is somewhat easier to shoot yourself in the foot with race conditions etc.

---

### Post by slavik on 2008-05-28
first, learn the difference between a thread and a process, then decide what you want to do and how you want to handle communication.

---

