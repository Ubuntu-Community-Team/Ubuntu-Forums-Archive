---
title: "Multiprocessor programing c++"
date: 2009-09-14
forum: Programming Talk
---

### Post by Benzaa on 2009-09-14
Hi,

Does anyone have a link to a good tutorial or something to learn how to do programing with multiprocessors in c++??

---

### Post by NoReflex on 2009-09-14
I don't have any experience with it but you could take a look at the OpenMP API.

NoReflex

---

### Post by MadCow108 on 2009-09-14
the by far easiest way I know is openMP
[http://openmp.org/wp/](http://openmp.org/wp/)
It is included in gcc since ~4.2 (+-1)
but its limited to shared memory systems.

you can also use pThreads. More flexible but also (comparably) harder to write correct code.

if you have a complex network/memory topology an MPI (message passing interface) implementation is probably the simplest way to go.

---

### Post by Wistful on 2009-09-14
[http://www.amazon.com/Parallel-Scientific-Computing-MPI-Implementation/dp/0521520800](http://www.amazon.com/Parallel-Scientific-Computing-MPI-Implementation/dp/0521520800)

[http://www.amazon.com/Using-OpenMP-Programming-Engineering-Computation/dp/0262533022/ref=pd_sim_b_2](http://www.amazon.com/Using-OpenMP-Programming-Engineering-Computation/dp/0262533022/ref=pd_sim_b_2)

Look at the "Customers Who Bought This Item Also Bought" there are dozens other books.

---

### Post by zo3adams on 2009-09-14
Above links are great.  

A free solution to get you started could be to work through some available University coursework (see the openMP labs, just completed, recommend):

[http://www.cecs.csulb.edu/~jpark/cecs570/](http://www.cecs.csulb.edu/~jpark/cecs570/)

---

### Post by Benzaa on 2009-09-16
Thanks for the suggestions. I was playing with my code and didnt have time to check the answers before.

Actually I had a look at OpenMP, it looks a bit complicated but I'll spend some time trying to find some tutorials for the API.


I was wondering if someone has worked with 2 processors for numerical analysis??

---

### Post by dwhitney67 on 2009-09-16
Benzaa,

I would suggest you attempt to get your application up/running as a single-threaded app, then after, if necessary, attempt to migrate it to work as a multi-threaded application.

I have never used openMP myself, and I agree, from the looks of it, the syntax/concepts look a little weird.

Most threading applications can be done with the basic C pthread library functions.  Since you are programming in C++, you could also consider using Boost's thread library.  IMO, the Boost thread library is easy to use.

---

### Post by MadCow108 on 2009-09-16
it looks weird as it uses compiler directives instead of code to archive parallelism but for certain cases its extremely easy:
```

#pragma omp parallel for
for (i=0; i < N; i++)
	//do simple stuff

// easiest synchronization construct:
int result=0;
#pragma omp parallel for reduction(+:result) 
for (i=0; i < N; i++) {
	result += i;
}

```
now just specify your number of threads (e.g. by a export OMP_NUM_THREADS=x in shell)
and your finished.
of course the code inside your loop should be suitable for multithreading.

it gets more complicated when you need synchronization, but thats the case with other techniques too.

---

### Post by dwhitney67 on 2009-09-16
Sorry Madcow... the code still looks weird; almost a language onto itself.  My bias perhaps stems from the fact that I hate macros (compiler directives).

---

### Post by TheBuzzSaw on 2009-09-16
Just learn how to use threads.

---

### Post by Benzaa on 2009-09-17
> **TheBuzzSaw said:**
> Just learn how to use threads.

Where can I get a tutorial for threads?

---

### Post by matthew.ball on 2009-09-17
[https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)

---

### Post by dwhitney67 on 2009-09-17
Or here:  [http://www.boost.org/doc/libs/1_37_0/doc/html/thread.html](http://www.boost.org/doc/libs/1_37_0/doc/html/thread.html)

---

### Post by Benzaa on 2009-09-17
> **matthew.ball said:**
> [https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/)


> Or here: [http://www.boost.org/doc/libs/1_37_0...ml/thread.htm](http://www.boost.org/doc/libs/1_37_0...ml/thread.htm)

Thanks, thats what I was looking for

---

### Post by TheBuzzSaw on 2009-09-17
Out of curiosity... what are you planning on using threads for? They're tricky little beasts. You have to know how to properly divide up labor and address synchronization issues. I hope you have a big job for those threads because oftentimes, single core processors are adequate.

---

