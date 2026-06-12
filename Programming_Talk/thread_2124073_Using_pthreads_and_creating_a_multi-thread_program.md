---
title: "Using pthreads and creating a multi-thread program in C"
date: 2013-03-09
forum: Programming Talk
---

### Post by kqpro on 2013-03-09
I am new to multi-thread programming, are there any examples that and shows me to create 2 or more threads. Then each of these thread will do some type of job. Like if I pass a series of numbers into the program through command line, and then thread 1 will calculate the sum, other thread will calculate smallest number, and another one will find the average.. etc. At the end, the parent thread should just output these worker threads's exited values.

---

### Post by r-senior on 2013-03-10
The example [here]("http://www.amparo.net/ce155/thread-ex.html") creates two threads that each print a message but it shows how to write the function that becomes the body of the thread, how to pass data to each thread and how the main thread can wait for each worker thread to complete. That's the basis of your program.

---

