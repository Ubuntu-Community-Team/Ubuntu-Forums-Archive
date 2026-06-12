---
title: "Segmentation Fault"
date: 2010-04-23
forum: Programming Talk
---

### Post by stiltz on 2010-04-23
Dear All,

I am a new user of ubuntu. I am trying to simulate a c program which is actually quite  large programe which runs for almost 100000 times in a for loop and at the end it caculates some probabilities. My problem is that if I run the program for 1000 times or even less than it , it calculates the results correctly and there is no problem but when I want to run it for 100000 times it gives me run time error just displaying " Segmentation Fault ".  I am not able to debug the program also because I do not know on which run this error is generated.
Can anyone give me a good advice and help ?

Thanks

---

### Post by Zugzwang on 2010-04-23
Yes. Run the program with valgrind to detect a good share of problems that only sometimes result in segmentation faults.

```

valgrind --tool=memcheck <yourprogram>

```

---

### Post by MadCow108 on 2010-04-23
a debugger may be even better suited in this particular problem
compile with -g flag
gdb yourprogram
run
... wait for crash

now you can inspect the loop counter and make a backtrace to pinpoint the position

btw which language?
if in C, are you doing something like this?
int n =10000;
double res[n]
for (0..n)

then this is a stack overflow, replace the res with a dynamic allocation (malloc/new) to make full use of the available ram

---

### Post by stiltz on 2010-04-23
Thanks for help. I will try both valgrind and debugger and will try to find  the problem and will discuss with you people. But it will take some time . Yes  my program is in C language and I am always using dynamic allocation (using malloc). I have 4GB of RAM. Could it be stack overflow ?? May be ....

---

### Post by howlingmadhowie on 2010-04-23
> **stiltz said:**
> Thanks for help. I will try both valgrind and debugger and will try to find  the problem and will discuss with you people. But it will take some time . Yes  my program is in C language and I am always using dynamic allocation (using malloc). I have 4GB of RAM. Could it be stack overflow ?? May be ....

you could always try showing us the code :)

---

