---
title: "How to determine which Monitor model runs underneath my programms."
date: 2010-11-12
forum: Programming Talk
---

### Post by NoJamNoMusic on 2010-11-12
Hello Lads and Ladies.

I have to write a program in **C **using **pthreads **(POSIX).
The programs sync has to be implemented using monitors(That is: using** condition variables,singal(),wait()** and a mutex for mutual exclusion of those calls).


Help me determine which model is being implemented(libraries + OS).
Is it

**Open / Eggshell  + Signal&continue / Signal & block ?**


So far from the manpage [http://man.yolinux.com/cgi-bin/man2html?cgi_command=pthread_cond_signal](http://man.yolinux.com/cgi-bin/man2html?cgi_command=pthread_cond_signal) 

The only useful information I gathered is
> pthread_cond_signal restarts one of the threads that are waiting on the
       condition  variable  cond.Should I assume an Open + Signal & continue model?


Where should I look for some information?

Thanks, Keep :guitar:


EDIT: OS: Ubuntu 10.04

---

