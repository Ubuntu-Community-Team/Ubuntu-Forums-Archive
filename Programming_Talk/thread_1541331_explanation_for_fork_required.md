---
title: "explanation for fork required"
date: 2010-07-29
forum: Programming Talk
---

### Post by piyush.neo on 2010-07-29
[COLOR=#ff0000]**Please note that Unix will make an exact copy of the parent's address space and give it to the child.   Therefore, the parent and child processes have  separate address spaces**[/COLOR].
i have read this statement on 
[http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html](http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html)
i am not able to understand that if both child and parents have exact copy of address space i.e
a variable have same address in  parent process and child process, then how changing the value in of a variable in one process doesn't effect its value in other as they have same address.
How OS identify and manage it?

---

### Post by Some Penguin on 2010-07-29
The kernel maps *virtual* address spaces, which are normally separate for each process, to physical addresses.

---

### Post by vikas.sood on 2010-07-29
> **piyush.neo said:**
> [COLOR=#ff0000]**Please note that Unix will make an exact copy of the parent's address space and give it to the child.   Therefore, the parent and child processes have  separate address spaces**[/COLOR].
i have read this statement on 
[http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html](http://www.csl.mtu.edu/cs4411/www/NOTES/process/fork/create.html)
i am not able to understand that if both child and parents have exact copy of address space i.e
a variable have same address in  parent process and child process, then how changing the value in of a variable in one process doesn't effect its value in other as they have same address.
How OS identify and manage it?

After fork() child gets a copy of the parents's address space, but its not the same address space. its a different process what you have got after all.

---

### Post by piyush.neo on 2010-07-29
Thanks:D

---

### Post by vikas.sood on 2010-07-29
> **piyush.neo said:**
> Thanks:D

And trust me, if the address space was same, you wouldnt need all the IPCs fifos pipes.. dont even think further on this [-X  and mark the thread solved :)

---

### Post by worseisworser on 2010-07-29
> **piyush.neo said:**
> 
i am not able to understand that if both child and parents have exact copy of address space i.e
a variable have same address in  parent process and child process, then how changing the value in of a variable in one process doesn't effect its value in other as they have same address.

By the way -- if you'd like for the different processes to share data you'd want to use (p)threads:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html)
[http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html)


..and/or you've got things like shared memory:
[http://www.kernel.org/doc/man-pages/online/pages/man2/shmget.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/shmget.2.html)

---

### Post by vikas.sood on 2010-07-29
> **worseisworser said:**
> By the way -- if you'd like for the different processes to share data you'd want to use (p)threads:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html)
[http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html](http://www.kernel.org/doc/man-pages/online/pages/man7/pthreads.7.html)


..and/or you've got things like shared memory:
[http://www.kernel.org/doc/man-pages/online/pages/man2/shmget.2.html](http://www.kernel.org/doc/man-pages/online/pages/man2/shmget.2.html)

worseisworser, POSIX pthread library allows you to write multi threaded applications and provides primitives for creating and synchronizing among threads. Since, threads all run in the parent process's address space it needs synchronization so that your threads dont run into race conditions. Threads and processes are two different concepts.

---

### Post by worseisworser on 2010-07-29
> **vikas.sood said:**
> worseisworser, POSIX pthread library allows you to write multi threaded applications and provides primitives for creating and synchronizing among threads.

I'm not sure why you're telling me this, but since you seem to have at least some misunderstanding of what the difference means, in practice, I'll add something to this.


> **vikas.sood said:**
> Since threads all run in the parent process's address space it needs synchronization so that your threads dont run into race conditions.

You seem to imply that when using processes for concurrency, the need for synchronization disappears? This is not true; it is certainly not what makes them distinct concepts!

E.g., have you noticed how PostgreSQL uses one process pr. connection, but still uses and/or requires transactions, shared memory, locking, semaphores and has a *ton* potential concurrency problems one will need to think about, understand and deal with both as a developer of PostgreSQL and user?

( [http://www.postgresql.org/docs/8.4/static/connect-estab.html](http://www.postgresql.org/docs/8.4/static/connect-estab.html) )

The need for synchronization actually arises as a result of *shared access to data*; *not* as a result of usage of threads in particular!

Also, if one where to speak of threads and processes in general, without some particular context; the distinction with regards to what terminology is used for what turns out to be very blurry in several areas.

---

### Post by vikas.sood on 2010-07-30
> You seem to imply that when using processes for concurrency, the need for synchronization disappears? This is not true; it is certainly not what makes them distinct concepts!

Never said that. I talked about pthread.

---

