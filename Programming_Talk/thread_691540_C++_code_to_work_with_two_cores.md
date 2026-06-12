---
title: "C++ code to work with two cores"
date: 2008-02-08
forum: Programming Talk
---

### Post by murmel on 2008-02-08
Hello everybody! I've written a small program that just calculates prim numbers. Works fine, if you're intrested. But what I would like to know is;
How do I get it to work with both of my cores (Intel Core 2 Duo).

Hehe, thanks!
- Simon

---

### Post by killermist on 2008-02-08
The way I understand it, you need to divide the heavy processing function into a thread that can be launched simultaneously (to utilize all cores).

---

### Post by lnostdal on 2008-02-08
```
man 3 pthread_create
```

your OS fixes the rest ... :)

---

### Post by killermist on 2008-02-08
```
No manual entry for pthread_create in section 3
```

---

### Post by Acglaphotis on 2008-02-08
[PHP]
sudo aptitude install manpages-dev
[/PHP]

---

### Post by slavik on 2008-02-09
or fork :)

---

### Post by aks44 on 2008-02-09
> **slavik said:**
> or fork :)
The problem with forking is that it makes it way harder for the different forked instances to communicate together, compared to regular threads. Forking is also more resource intensive (especially at the "splitting" moment). You have to take that into account when choosing which method you'll use (fork vs threads).


> **lnostdal said:**
> ```
man 3 pthread_create
```

your OS fixes the rest ...

Now please allow me a little rant... ;)

You people just presented concurrent programming like if it was something trivial to do, without a single warning that (as of today) *_this is one of the most difficult tasks_* in software engineering. Forgetting to mention it can, IMO, easily mislead the OP.
I'm pretty sure you already know that, but **no**, the OS **won't** automagically "*fix the rest*" (especially when it comes to threads ; performance aside I admit that forking is a bit easier, but as I already stated you then have to deal with IPC, choose your poison...).

[Herb Sutter]("http://gotw.ca/"), one of the most renowned C++ gurus out there, even states that "*[concurrent] programming is hard for _experts_ to get right*" (notice the underlined part).


**@OP:** concurrent programming is best adapted for *_simultaneous **independent** tasks_*. So before hacking into the code, ask yourself: how can you modify your current algorithm in order to minimize the different parts' dependency on each other's results (ie. the "*divide and conquer*" approach)?
Too much dependencies will only lead to thread (or process) contention, which will annihilate any gain you could have made of concurrent processing.

Another thing to keep in mind is that with the current state of the art, concurrency problems require quite some specific knowledge (especially of the synchronization primitives and their various interactions), and very strong design skills:
- synchronization primitives are *_not composable_*, which means that if A and B are (independently) known to be correct, there is *no guarantee* that A+B will work as expected
- concurrency issues are very hard to debug, it is almost *_impossible to reproduce_* them at will

Again, Herb Sutter published too many [articles on this subject]("http://www.gotw.ca/publications/index.htm") for me to list them here (see also the [GotW series]("http://www.gotw.ca/gotw/index.htm")).


Ok, rant finished, we can all go back to normal activities... ;)

---

### Post by lnostdal on 2008-02-09
well, yeah -- it's hard .. many things can be hard .. i'm sure murmel will discover these things on his own without me having to warn him(#1)

what i meant by "the os will fix the rest" is of course just that .. linux does have automagically support for multiple cores when using pthreads -- so that part is easy and transparent when you already have the actual threading/coding/designing part in place

#1: not that it's "wrong" to warn him .. i don't see it as "wrong" to not warn him either .. one must do what is necessary to get things done

---

### Post by scourge on 2008-02-09
> **aks44 said:**
> The problem with forking is that it makes it way harder for the different forked instances to communicate together, compared to regular threads. Forking is also more resource intensive (especially at the "splitting" moment). You have to take that into account when choosing which method you'll use (fork vs threads).

True, and I fully recommend threads for programming Linux applications. But threads have some platform compatibility issues (i.e. different ways to report cpu time, controlling how many cpus are used), whereas fork() always works the same way. So for cross-platform development processes may be the better choice.

---

### Post by stroyan on 2008-02-09
Another approach to using multiple cores is to use language features that assist with multiprocessing.  That can make the task simpler.
The OpenMP API adds directives to tell a compiler about parallelism.
See [http://en.wikipedia.org/wiki/OpenMP](http://en.wikipedia.org/wiki/OpenMP) for a summary.
There is an example of applying OpenMP to prime number finding at [http://www.devx.com/go-parallel/Article/32724](http://www.devx.com/go-parallel/Article/32724) .

---

