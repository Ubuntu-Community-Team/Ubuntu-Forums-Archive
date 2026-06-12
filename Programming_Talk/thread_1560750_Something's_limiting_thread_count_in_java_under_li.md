---
title: "Something's limiting thread count in java under linux"
date: 2010-08-25
forum: Programming Talk
---

### Post by spupy on 2010-08-25
For whatever reasons I'm trying to measure how many/how fast threads can be created by java with different CPUs and different OSs.
Under 64bit windows (7 or vista, not sure), the program has no problem creating over 80000 threads, at which point I can't monitor it anymore until/unless it dies.
On 64bit Linux, however, it goes a bit over 32000 and then the program dies with no error messages.
What could cause this limit under linux? I tried increasing max process count, max thread count, PID wrap-around number, with sysctl, but nothing helps.
Any ideas?

---

### Post by LightningCrash on 2010-08-25
check 
```
ulimit -a
```
on the user account running the java


I know on some distributions the ulimit -u is limited to 16K or 32K

---

### Post by spupy on 2010-08-25
> **LightningCrash said:**
> check 
```
ulimit -a
```
on the user account running the java


I know on some distributions the ulimit -u is limited to 16K or 32K

Is this max memory size? It says unlimited. I also check stack size, but it is bigger than java, so that wouldn't be a problem.
Looking at ulimit now, I have to check if the "open files" limit is causing the problem (it's only 1024).

---

### Post by dwhitney67 on 2010-08-25
I Googled for "Linux Maximum Number Threads".

The first result:  [http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux](http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux)

---

### Post by spupy on 2010-08-25
> **dwhitney67 said:**
> I Googled for "Linux Maximum Number Threads".

The first result:  [http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux](http://stackoverflow.com/questions/344203/maximum-number-of-threads-per-process-in-linux)

I already tried this and other options with sysctl (it's the same as /proc/sys) (see first post).

Perhaps I should rephrase my question. Not **how**, as I'v already tried various options, but rather **why** are threads limited, and why don't these options have any effect.

---

### Post by Zugzwang on 2010-08-25
> **spupy said:**
> Perhaps I should rephrase my question. Not **how**, as I'v already tried various options, but rather **why** are threads limited, and why don't these options have any effect.

There's a comment in the link that dwhitney67 posted which is concerned with the stack space that every thread needs. So, as an example, if you only have 32 kB per thread, you would already consume ~960MB of memory for this. In practice, the stack space per thread may be much larger.

---

### Post by spupy on 2010-08-25
> **Zugzwang said:**
> There's a comment in the link that dwhitney67 posted which is concerned with the stack space that every thread needs. So, as an example, if you only have 32 kB per thread, you would already consume ~960MB of memory for this. In practice, the stack space per thread may be much larger.

A reasonable thread stack size (JVM option Xss) is 64KB at least.
I'm also experimenting with different stack sizes (Xss) and different allocated memory to the JVM (Xms/Xmx). Unexpectedly, these options have no influence on the number of threads created before the program dies - ~32000 threads.

---

### Post by LightningCrash on 2010-08-25
> **spupy said:**
> Is this max memory size? It says unlimited. I also check stack size, but it is bigger than java, so that wouldn't be a problem.
Looking at ulimit now, I have to check if the "open files" limit is causing the problem (it's only 1024).

it's all the user limits. i was specifically concerned with ulimit -u
-u is the limit on user processes.

---

