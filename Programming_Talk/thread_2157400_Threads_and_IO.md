---
title: "Threads and I/O"
date: 2013-06-25
forum: Programming Talk
---

### Post by Dirich on 2013-06-25
Hello,

when I learned about threads either I thought (or I read, I can't remember which) that they would be good to handle I/O. I mean, if I have to write stuff in 3 files and I want to keep processing, I can make 4 threads, 1 will be doing the processing work, and the other 3 will be dedicated to write in one file each. In this way I can keep computing all the time while the "writer threads" wait for I/O operations to carry out.
Recently though, someone told me that he wrote a program that had a lot of I/O operations, and for such reason threads were so bad he actually had to disable them.

I am curious, who is wrong?

Mind that his program uses MPI, so I guess he can use some processes to do the I/O while others carry out computations. So maybe, if the answer to the previous question is "depends", a better question could be:

Is it really better, performance wise (time and memory), to handle I/O via processes and MPI instead of threads?

---

### Post by nidzo732 on 2013-06-25
Threads are bad when they all read or write to the same source. If all four threads were writing to the same file the written text would get mixed up and you would get a lot of gibberish in that file. But that happens only when multiple threads use the same file, I don't see any problem with your design, all threads have separate outputs so it should work fine.
Performance-wise, there shouldn't be any problems, MPI might add some overhead but it won't be too big.
About the processes vs. threads, some languages (most notably Python and Ruby) have a Global Interpreter Lock (GIL) that prevents threaded programs from reaching maximum performance on a multi core processors.If your language has GIL and you need the performance of multiple cores, you should consider multiprocessing. If you don't have to worry about GIL then use threads, they are much more lightweight and have less overhead than processes.

---

