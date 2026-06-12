---
title: "Efficiency checking of programs"
date: 2009-07-19
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-19
how can we check the time taken by a program to execute,time taken taken by its various modules,and the memory and space analysis of each function,variable in c/c++.
Using this concept i wish to compare sorting algorithms on practical data and not theoritically.and make a program which tells a user the best algorithm for the data input and then sorts it.
How can the second part be achieved,the computer itself chooses the best sorting algo for a particular input

---

### Post by Sockerdrickan on 2009-07-19
gprof

---

### Post by jero3n on 2009-07-19
> and make a program which tells a user the best algorithm for the data input and then sorts it.
I think, an algorithm finding the best sorting algorithm for a given dataset, would be far slower than sorting with a generally good algorithm itself. :)

I like valgrind for profiling.

---

### Post by smartbei on 2009-07-19
Unless you get, as input, the type of data being sorted. For example, if I give you a file, without telling you what's in it, and tell you to sort it's lines (or buffers of length 16, etc.), you can't improve from a basic sort. If however, I give you a file, and tell you that on each line is a number between 1 and 10000, then you can sort far more efficiently.

I assume that is what the OP meant. Otherwise, you could also look at the first k pieces of data and check if they are all numbers, etc. That seems like it would be difficult.

---

### Post by nipunreddevil on 2009-07-19
suppose we know that we are dealing only with sorting numbers then is this approach fruitful if we do a lot of training?
and are there no c functions to find execution time and other program related data rather than using profilers?

---

### Post by jero3n on 2009-07-19
Actually you don't have to use profilers at all. Collect some sorting algorithms and study their logic.

All of them have to pass all the data. The question is how many times each datapoint needs to be passed and swaped and how large buffers are needed. There is usually a memory/speed trade off in each algorithm.

Choosing a "better" algorithm has to do with statistical distribution and attributes of your data. But I think it might be difficult to understand if in some distributions an algorithm behaves better than another. On the other hand, these calculations should make your program's decision slower that actual sorting.

---

### Post by MadCow108 on 2009-07-19
you could have a look at the fftw3 library.
It can do exactly what you want to do just with fast fourier transform algorithms.
[http://www.fftw.org/](http://www.fftw.org/)

Also have a look at their method for timing the algorithms and especially the Cycle Counters section of their download page for (plattform dependant) precision timing functions.

---

### Post by lisati on 2009-07-19
There's a nice on-line demo of a selection of different sorting algorithms here: [http://www.cs.ubc.ca/~harrison/Java/sorting-demo.html](http://www.cs.ubc.ca/~harrison/Java/sorting-demo.html)

---

### Post by slavik on 2009-07-19
you are entering the field of analysis of algorithms. Given a bunch of data, you cannot know 100% which out of some similar algorithms would be best for a set of data unless you analyse the data and that will probably be slower. For example, given numbers in reverse order to be sorted, quicksort will be O(n^2), while heapsort will be O(n * log n), it also depends on the size of the input (n), some algorithms behave better at smaller inputs than at large input (lots of smaller data sets to sort). Then you have something like radix  sort which does not use comparisons, hence you cannot compare it to heapsort or quicksort. Also, do you want a stable sort or is unstable sort fine as well?

---

### Post by nipunreddevil on 2009-07-19
i had this random idea of using neural nets to train for choosing the best algo for sorting a dataset
i have no information about stable and unstable sorting

---

### Post by jero3n on 2009-07-19
> i had this random idea of using neural nets to train for choosing the best algo for sorting a dataset
Interesting approach. But have you thought what would be the input of your neural net? The entire set?

---

### Post by CptPicard on 2009-07-19
A neural net is not going to be of use... the most important qualities of a dataset in this regard is whether it is almost nearly sorted (use insertion sort) or if it is already sorted (don't use naive quicksort).

After that, it's implementation requirements-dependent choices. If you really want to know what is fastest, profile and choose the best one.

---

### Post by Can+~ on 2009-07-19
[Heapsort]("http://en.wikipedia.org/wiki/Heapsort") usually has the advantage of having a constant the same worse-case and best-case performance (n·logn)

But I get the feeling that the OP is really asking on a homework, I had to do something similar a long time ago, when we were introduced to Data Structures and Algorithms.

---

### Post by nipunreddevil on 2009-07-19
> **Can+~ said:**
> [url="http://en.wikipedia.org/wiki/Heapsort"]
But I get the feeling that the OP is really asking on a homework, I had to do something similar a long time ago, when we were introduced to Data Structures and Algorithms.
Sir,
This is not for any homework
We have very easy homework out here which do not go beyond the textbook.
I asked this question out of curiosity and a will to learn more.

---

### Post by Can+~ on 2009-07-19
> **nipunreddevil said:**
> Sir,
This is not for any homework
We have very easy homework out here which do not go beyond the textbook.
I asked this question out of curiosity and a will to learn more.

Oh well, if you're interested, most Database Engines use some kind of profiling and measures the quickest way to solve a transaction.

It mostly tries to calculate what "it would take", not actually doing it. For example, if the file is sorted according to a certain column, and a query is made on said column, it knows that it can get to it multiple ways; it would take half the blocks to do a linear search; or it would take log(b) getting there with a [binary search]("http://en.wikipedia.org/wiki/Binary_search_algorithm"). It compares both log(b) < b and chooses the former.

---

### Post by slavik on 2009-07-19
> **Can+~ said:**
> [Heapsort]("http://en.wikipedia.org/wiki/Heapsort") usually has the advantage of having a constant the same worse-case and best-case performance (n·logn)

But I get the feeling that the OP is really asking on a homework, I had to do something similar a long time ago, when we were introduced to Data Structures and Algorithms.
As did I, except my homework was "implement these sorts and tell me which is best for which kind of sets" (well, there were specifications on choosing sorts and how to make data sets, but you get the idea.)

---

### Post by stroyan on 2009-07-20
The clock_gettime and clock_getres functions are good for a program to measure the elapsed time from the start to the finish of an activity.
But limited resolution of timers can be a problem.
Be aware that small activities may be too short and inconsistent in duration to be accurately and reliably timed.
There is often a trade-off between an activity that is representative and an activity that is easy to measure.
Cache effects can make repeating a small activity become faster than the first run of it.
And cache effects can mean that making a data set much bigger can increase the time for an activity by a greater than linear scaling.

---

### Post by jero3n on 2009-07-20
> **CptPicard said:**
> A neural net is not going to be of use... the most important qualities of a dataset in this regard is whether it is almost nearly sorted (use insertion sort) or if it is already sorted (don't use naive quicksort).

After that, it's implementation requirements-dependent choices. If you really want to know what is fastest, profile and choose the best one.

I am not sure if it is worth trying, but I am curious to see if a neural net could classify a vector of data to be sorted to an appropriate algorithm according to similarities with the best or the worst case. 

However it might need some magic tricks in the normalization and compression of the input vector.

---

### Post by nipunreddevil on 2009-07-21
> **jero3n said:**
> 
However it might need some magic tricks in the normalization and compression of the input vector.
I am ready to try doing out the magic tricks if there is support.

---

### Post by lisati on 2009-07-21
> **jero3n said:**
> I am not sure if it is worth trying, but I am curious to see if a neural net could classify a vector of data to be sorted to an appropriate algorithm according to similarities with the best or the worst case. 

I'm not sure if it would be worth the trouble to use neural nets on small sets of data. On larger sets, selecting a suitable subset on which to run the evaluation might be interesting.

---

### Post by nipunreddevil on 2009-07-21
can we use multiple sorting techniques in one data set
For eg in a list of  numbers,first 40 done by heap,next 30 by merge and so on.
The catch is that not we but an algo decides which sorting algo is used when

---

### Post by CptPicard on 2009-07-21
> **nipunreddevil said:**
> can we use multiple sorting techniques in one data set

It is actually quite common to optimize quicksort by sorting small enough subsets using insertion sort, as the division phase of the algorithm eventually produces sets that are amenable to that particular algorithm (they are almost-ordered).

> 
The catch is that not we but an algo decides which sorting algo is used when

That hypothetical algorithm would be slower than just straight using any reasonable sorting algorithm... besides, judging where the usage of any given algorithm is appropriate is one of those things where you really need the human programmer's input...

---

