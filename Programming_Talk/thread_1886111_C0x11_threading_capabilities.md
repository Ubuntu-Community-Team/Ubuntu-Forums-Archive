---
title: "C0x11: threading capabilities"
date: 2011-11-24
forum: Programming Talk
---

### Post by erotavlas on 2011-11-24
Hi,

I have read that the new C++ standard C0x11 has a support for threading programming. I have understood that the support is only to core level and the library will be released soon. If I'm wrong, please correct me. So at the moment, can I use the embedded C++ capabilities for threading programming? I have read some times ago, that with high probability the threading library of the C0x11 it should be the same of boost library? It's true?

Thank you

---

### Post by ehmicky on 2011-11-24
You're right.
If you want to use it, you'll still have to use a compiler that has implemented it (g++ did), or you can use boost::thread which is almost the same.

---

### Post by erotavlas on 2011-11-25
> **ehmicky said:**
> You're right.
If you want to use it, you'll still have to use a compiler that has implemented it (g++ did), or you can use boost::thread which is almost the same.

Thank you for your fast reply. At the moment GCC supports only a small subset of threading programming features [http://wiki.apache.org/stdcxx/C++0xCompilerSupport](http://wiki.apache.org/stdcxx/C++0xCompilerSupport).
So it is the best to use the boost library...
Another question: what about the OpenMP directives? How they are different in terms power and flexibility for the parallel programming task?

Thank you

---

### Post by MadCow108 on 2011-11-25
openmp is mostly for quick and easy parallelism
you have a loop which you want to parallize but don't want to bother about herding a pool of threads, distributing and gathering work and joining your threads? then openmp is perfect put a couple of pragmas in and your done.

but the simplicity is also its problem, its very limited in what it can do and it does not scale beyond your local machine.
If you have complex task interactions between the threads you will want more control over each threads, boost threads provides that but its a lot more work and a lot more can go wrong.
If you want to go distributed you may want to use something higher level, like MPI, zeromq or spread which have the advantage that they scale nicely from local machines to distributed clusters.

---

### Post by erotavlas on 2011-11-28
> **MadCow108 said:**
> openmp is mostly for quick and easy parallelism
you have a loop which you want to parallize but don't want to bother about herding a pool of threads, distributing and gathering work and joining your threads? then openmp is perfect put a couple of pragmas in and your done.

but the simplicity is also its problem, its very limited in what it can do and it does not scale beyond your local machine.
If you have complex task interactions between the threads you will want more control over each threads, boost threads provides that but its a lot more work and a lot more can go wrong.
If you want to go distributed you may want to use something higher level, like MPI, zeromq or spread which have the advantage that they scale nicely from local machines to distributed clusters.

Thank you for your clear explanation. So, at the moment, the only choice is the boost library beacuse I'm only interested to parallelize the code inside a single machine not a cluster.

Another question: In the current version of my code I'm using GDB and gconf as debugger and profiler tools. To develop my new parallel code I need a parallel debugger and parallel profiler. Can you advise a good tools (open source or free)?

Thank you

---

### Post by ehmicky on 2011-11-28
Actually GDB does have [multithreaded applications debugging facilities](http://www.delorie.com/gnu/docs/gdb/gdb_25.html), but I don't know if there's better on GNU/Linux.

---

### Post by gateway67 on 2011-11-28
> **erotavlas said:**
> So, at the moment, the only choice is the boost library beacuse I'm only interested to parallelize the code inside a single machine not a cluster.

You can always fall back to use the C pthread library.  It's not portable, but conceptually it is similar to Boost threading library.

A simple example in C++ would be:
```

#include <pthread.h>
#include <iostream>

class MyThread
{
public:
   MyThread()
   {
      pthread_create(&m_tid, NULL, starter, this);
   }

   void run()
   {
      std::cout << "The thread is running." << std::endl;
   }

   void join()
   {
      pthread_join(m_tid, NULL);
   }

private:
   void* starter(void* arg)
   {
      MyThread* thread = reinterpret_cast<MyThread*>(arg);
      thread->run();
      return 0;
   }

   pthread_t m_tid;
};

int main()
{
   MyThread mt;
   mt.join();
}

```

---

### Post by MadCow108 on 2011-11-28
> **gateway67 said:**
> You can always fall back to use the C pthread library.  It's not portable, but conceptually it is similar to Boost threading library.

I'd not go for pthread when using c++ unless you have a good reason, pthread is pretty much the lowest level you can reasonably go
boost thread is on the verge of being standard (c++11) meaning it will be much more portable than pthreads in near future. It is much higher level while retaining almost all of the control pthread offers.


concerning debuggers and profilers, gdb can debug multithreaded applications but it can get tricky (as almost everything involving threads is).
valgrind offers a few tools which can help, namely helgrind and dtd which can detect some stuff like race conditions and excessivly long held locks, but with rather high false positives.
for profiling oprofile is quite good, as it basically profiles the kernel you have access to all information you would ever need.

---

### Post by erotavlas on 2011-11-29
> **gateway67 said:**
> You can always fall back to use the C pthread library.  It's not portable, but conceptually it is similar to Boost threading library.

A simple example in C++ would be:
```

#include <pthread.h>
#include <iostream>

class MyThread
{
public:
   MyThread()
   {
      pthread_create(&m_tid, NULL, starter, this);
   }

   void run()
   {
      std::cout << "The thread is running." << std::endl;
   }

   void join()
   {
      pthread_join(m_tid, NULL);
   }

private:
   void* starter(void* arg)
   {
      MyThread* thread = reinterpret_cast<MyThread*>(arg);
      thread->run();
      return 0;
   }

   pthread_t m_tid;
};

int main()
{
   MyThread mt;
   mt.join();
}

```

Thank you, but I have discarded this option a due to its drawbacks.

---

### Post by erotavlas on 2011-12-01
> **MadCow108 said:**
> I'd not go for pthread when using c++ unless you have a good reason, pthread is pretty much the lowest level you can reasonably go
boost thread is on the verge of being standard (c++11) meaning it will be much more portable than pthreads in near future. It is much higher level while retaining almost all of the control pthread offers.


concerning debuggers and profilers, gdb can debug multithreaded applications but it can get tricky (as almost everything involving threads is).
valgrind offers a few tools which can help, namely helgrind and dtd which can detect some stuff like race conditions and excessivly long held locks, but with rather high false positives.
for profiling oprofile is quite good, as it basically profiles the kernel you have access to all information you would ever need.

I have tried valgrind but it is to slow. What are the differencies between the oprofile and gprof?
If I'm not wrong both can profile a parallel code.
Thank

---

