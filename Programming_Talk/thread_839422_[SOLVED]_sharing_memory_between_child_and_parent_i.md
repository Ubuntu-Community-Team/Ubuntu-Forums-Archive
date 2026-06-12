---
title: "[SOLVED] sharing memory between child and parent in fork()"
date: 2008-06-24
forum: Programming Talk
---

### Post by tornado89 on 2008-06-24
How Can I Share The Same Memory Page Between A Parent
And It's Child Created Using fork();

I Know That vfork() can Do That But The Parent Must Wait
Till The Child calls exec()... Which Is NON-SENSE To Me

BTW I Am Using C++
Thanks ........

---

### Post by JupiterV2 on 2008-06-24
I am only a beginner in this particular subject but I know that in C you can use mmap() to share memory between processes.

---

### Post by PaulFr on 2008-06-24
I presume you are aware of the items inherited by the child process on fork(); if not, please see 1.1.1 in Unix Programming FAQ ([http://www.faqs.org/faqs/unix-faq/programmer/faq/](http://www.faqs.org/faqs/unix-faq/programmer/faq/))
 
If you need to share info after the fork() call - you can use shared memory, mmap, pipes, named pipes, sockets, message queues, semaphores and even signals (see [http://www.ibm.com/developerworks/aix/library/au-ipc/](http://www.ibm.com/developerworks/aix/library/au-ipc/) and [http://en.wikipedia.org/wiki/Mmap](http://en.wikipedia.org/wiki/Mmap)) for an introduction.

---

### Post by tornado89 on 2008-06-25
thanks... mmap() was what i am looking for..

---

