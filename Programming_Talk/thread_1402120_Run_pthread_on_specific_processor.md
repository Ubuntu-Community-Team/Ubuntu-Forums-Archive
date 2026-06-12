---
title: "Run pthread on specific processor"
date: 2010-02-08
forum: Programming Talk
---

### Post by DBQ on 2010-02-08
Hi everybody. Is there a way I can run a pthread on a specific processor? I.e. suppose my system has 4 processors, and I want to have 4 pthreads. I want to assign a thread to each processor, and from time to to time move them between processors. Is this possible?  If so, how could I accomplish this. An example would be nice.

---

### Post by dwhitney67 on 2010-02-08
I do not think the pthread library will offer you the level of control you seek.  Here's a link to the thread attributes you may control:  [http://sourceware.org/pthreads-win32/manual/pthread_attr_init.html](http://sourceware.org/pthreads-win32/manual/pthread_attr_init.html)

OpenMP, may, on the other hand assist your with your endeavor.  Read about it here:  [http://openmp.org/wp/](http://openmp.org/wp/)


P.S.  A thing to note/remember, is that a pthread is an LWP (Light Weight Process) that shares its program space with its parent thread.  If the parent thread is running one processor, it's a sure bet so are it's child-LWPs.

---

