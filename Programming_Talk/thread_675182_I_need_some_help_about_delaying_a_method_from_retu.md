---
title: "I need some help about delaying a method from returning the answer."
date: 2008-01-22
forum: Programming Talk
---

### Post by legolas_w on 2008-01-22
Hi
Thank you for reading my post.
I have an interface which has two  method with several parameters and I should implement this method to complete a task, eg: calculating a series.

The tester program will load my "dynamic shared library" and call initialize method for calibration. then It create several threads to call the worker method named calcSeries(......) . each thread may call the method several times.

for example following 4 calls need to be  issued by one of the above threads.

1-calcSeries(1,5,7,2)
2-calcSeries(3,9,2,1)
3-calcSeries(3,7,9,2)
4-calcSeries(5,4,8,6)

Is it possible to return the result asynchronously ?
for example I get all calls and then return the result when I complete them?
Maybe 4th call complete before other ones.


Thanks.

---

### Post by melopsittacus on 2008-01-22
Hello,

I think you should use an approach like the producer-consumer: the threads that perform the calculations put their results into an array, or stack, and the thread that uses the results, checks this array to see if there are any results.

---

### Post by Jmccaffrey on 2008-01-22
[http://en.wikipedia.org/wiki/Observer_pattern](http://en.wikipedia.org/wiki/Observer_pattern)

---

### Post by legolas_w on 2008-01-23
Thank you for your replys.
Unfortunately I have no control over the application that wll call my method.
I only have control over how to develop the dynamic shared library.



thanks.

---

