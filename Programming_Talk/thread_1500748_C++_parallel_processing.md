---
title: "C++ parallel processing"
date: 2010-06-03
forum: Programming Talk
---

### Post by Zorgoth on 2010-06-03
I have some numerical analysis that I might want to port to C++ and run on a multicore CPU (Linux) (actually 2 of those, one with 2 cores and one with lots).  How can I do that?  I know of the existence of POSIX threads but I don't know how to use them and all the tutorials I find are confusing.  The extent of what I want to do is basically to be able to run parts of the analysis like matrix operations in parallel threads.  I basically need enough control to create threads with access to the main data, make threads run at the same time, and kill them and have the primary thread know when they are done.

---

### Post by MadCow108 on 2010-06-03
for very easy very fast parallelization on shared memory systems, have a look at openmp.
If the problem and data is suitable, its just a matter of adding a handful of code lines.

generally C++ has no threading support (yet). But there are libraries which provide it.
One example would be boost::threads ([http://www.boost.org/doc/libs/1_43_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_43_0/doc/html/thread.html))
I'm sure there are many others too.

You could also fall back to the posix thread C implementation. See man 7 pthreads.
This is not recommended for C++, but may be useful to get an overview of the base.

For more complex problems especially for distributed computing check out MPI.

---

### Post by soltanis on 2010-06-03
+1 for OpenMP. It works well for parallelizing things such as loops. In its simplest form, you can take a for loop and execute it simultaneously over multiple processors by just doing:

```

#pragma omp parallel for
for (i = 0; i < big_num; i++) {
...
}

```

It also has plenty of constructs for thread synchronization, locking, and that sort of thing.

---

### Post by dwhitney67 on 2010-06-03
> **MadCow108 said:**
> 
generally C++ has no threading support (yet).

You've stated this before in another thread; I still do not understand what you mean by it.  There's pthreads and boost; what more do you want?

> **MadCow108 said:**
> 
You could also fall back to the posix thread C implementation. See man 7 pthreads.
This is not recommended for C++...

Why is this so?  I've used pthreads in C++ applications dating back to the late '90s.  I've never had a problem.

---

### Post by MadCow108 on 2010-06-04
> **dwhitney67 said:**
> You've stated this before in another thread; I still do not understand what you mean by it.  There's pthreads and boost; what more do you want?

no standardized threading support I meant. You need extra dependencies to use threads.
C++0x will standardize threading. It will be very similar to boosts implementation.

> Why is this so?  I've used pthreads in C++ applications dating back to the late '90s.  I've never had a problem.
this is my personal preference. It is of course no problem, just a matter of style.
I do not recommend it, as C++ threading implementations are easier to handle (e.g. scoped locks, futures, atomics etc.) and fit better into the language than raw pthread's.

---

### Post by dwhitney67 on 2010-06-04
> **MadCow108 said:**
> no standardized threading support I meant. You need extra dependencies to use threads.
C++0x will standardize threading. It will be very similar to boosts implementation.

It will be nice when C++0x is released; but one should not hold their breath till then and delay their development.

> **MadCow108 said:**
> 
I do not recommend it, as C++ threading implementations are easier to handle (e.g. scoped locks, futures, atomics etc.) and fit better into the language than raw pthread's.
If you think carefully about it, when utilizing Boost under *nix systems, it is merely a wrapper around the pthread library.  Prior to the advent of Boost, developers wrote their own wrapper (classes) around the pthread library.  I have done such a thing.

A scoped mutex is easy to implement in C++.  First develop the wrapper around the pthread_mutex_t, then develop a separate class for the scoped mutex.  It's fairly trivial.

Nevertheless, it will be nice if these features were built into the C++ library, thus mitigating the need to rely on the C library and of course, a home-made library that serves as a wrapper around the C library.

---

