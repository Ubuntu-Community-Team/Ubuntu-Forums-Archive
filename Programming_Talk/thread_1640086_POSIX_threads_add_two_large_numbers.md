---
title: "POSIX threads add two large numbers"
date: 2010-12-07
forum: Programming Talk
---

### Post by Andi018 on 2010-12-07
Hello everyone!

I have to write this program for school, using POSIX threads:

Two very large numbers are given, each having a million of
digits, the numbers being represented as strings. The digits are
randomly generated. Using a given number of threads (as
parameter), sum up the two numbers. A thread will sum 2 digits,
with left carry. A thread will start the summing on a position
that can't be affected by a carry from summing the neighbor
digits by other threads. The program will dispay the sum and
also the process time.  Mutexes and/or conditional variables
will be used.

I have no idea how to do it. If anyone could help, I'd be forever grateful.

Thanks.

---

### Post by dwhitney67 on 2010-12-07
Seems like an interesting school assignment.

Unfortunately, this forum is not to be used as a homework service. In other words, you will have to do the work on your own.

---

### Post by Arndt on 2010-12-07
> **Andi018 said:**
> Hello everyone!

I have to write this program for school, using POSIX threads:

Two very large numbers are given, each having a million of
digits, the numbers being represented as strings. The digits are
randomly generated. Using a given number of threads (as
parameter), sum up the two numbers. A thread will sum 2 digits,
with left carry. A thread will start the summing on a position
that can't be affected by a carry from summing the neighbor
digits by other threads. The program will dispay the sum and
also the process time.  Mutexes and/or conditional variables
will be used.

I have no idea how to do it. If anyone could help, I'd be forever grateful.

Thanks.

1) Try it by hand, with some 10-digit numbers or so, to see what the algorithmic issues are.

2) Read up on threads, and make a program with threads that does something simpler.

3) Make a program which in one single thread does the addition.

4) Put the pieces together. Think about the mentioned mutexes. Are they needed, and if so, why? If not, why not?

If you do something, and present it here, you may get comments as to why it doesn't work, but not if you haven't even started. (And if you think it does work, we will be happy to make it break.)

---

