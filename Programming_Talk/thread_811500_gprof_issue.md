---
title: "gprof issue"
date: 2008-05-29
forum: Programming Talk
---

### Post by me_himanshu on 2008-05-29
hi all,
            I have written a code and used some libraries...now when i run gprof, everything goes fine except the fact that every next time i run gprof over the same process, the total number of calls to a function (say func()) vary and  the variation being unpredictable...and it's not a single function whose total number of calls vary in different profiles but there are many functions of the same category........i just wanna ask that is there any issue with gprof that results in variable number of calls to the same function when each time  the gprof is applied to same process??

---

### Post by Zugzwang on 2008-05-29
Which functions? This behaviour might be totally normal for functions called by some system functions whose execution depends on the global state of the system (perhaps "malloc" or so).

Also, if your execution somehow uses random numbers *or* communicated with some other system stuff whose reply is again dependent on the the global state of the system, this can happen as well.

---

### Post by Bichromat on 2008-05-29
Every time you run your code, a new gmon.out is created, with the stats of the last run. If you get different results each time, *without* running your program, then you have to worry.

---

### Post by me_himanshu on 2008-05-30
We have two processes communicating through message queues(IPC). Everytime we send equal number of messages from one process to another, say x and get same number of replies i.e. x from the other process. We have a function func() in process 1 which processes a message everytime it receives a reply. But once in about 5 times, gprof flat profile shows that func() is called x-1 times, normal behaviour is x times. Also subroutines of func() get affected and they are also called x-1 times. So can gprof miss function calls sometimes?

---

### Post by Bichromat on 2008-05-30
gprof just processes the gmon.out file created by your code when using the -pg flag. If indeed there is a bug, it is more likely to be somewhere else. Try another tool, e.g. Valgrind (with callgrind), to see if you get the same results.

---

