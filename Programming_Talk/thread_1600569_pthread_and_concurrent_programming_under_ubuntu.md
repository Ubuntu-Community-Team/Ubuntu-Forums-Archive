---
title: "pthread and concurrent programming under ubuntu"
date: 2010-10-19
forum: Programming Talk
---

### Post by balteo on 2010-10-19
Hello,

I would like to know what is the best way to develop concurrent applications in C++ under linux. I don't know whether to go for the Boost library of directly code using the Pthread C API.

Can anyone please kindly give their advice? 

Is  Boost the standard wrapper around Pthreads?

Thanks in advance,

Julien.

---

### Post by dwhitney67 on 2010-10-19
Boost does wrap the pthreads for Unix/Linux, and does something similar for Windoze using M$ proprietary API.  Boost is not recognized as a standard for anything; it is merely an extension to C++.

Soon, hopefully in my lifetime, parts of Boost will be incorporated in the C++0x standard.

Personally, I think you should learn to use the pthread library before using Boost.

---

### Post by balteo on 2010-10-19
> **dwhitney67 said:**
> Boost does wrap the pthreads for Unix/Linux, and does something similar for Windoze using M$ proprietary API.  Boost is not recognized as a standard for anything; it is merely an extension to C++.

Soon, hopefully in my lifetime, parts of Boost will be incorporated in the C++0x standard.

Personally, I think you should learn to use the pthread library before using Boost.

Thanks for your reply. The only problem I find with pthread is that it is in C and not C++. What I am going to try and do is learn both.

---

### Post by dwhitney67 on 2010-10-19
> **balteo said:**
> Thanks for your reply. The only problem I find with pthread is that it is in C and not C++. What I am going to try and do is learn both.

Nonsense; pthreads can be used with C++.  Want to see...

```

#include <pthread.h>
#include <iostream>

class MyThread
{
public:
   MyThread(int iters = 5)
      : iterations(iters)
   {
   }

   void start()
   {
      pthread_create(&tid, 0, helper, this);
   }

   pthread_t getThreadID() const
   {
      return tid;
   }

private:
   static void* helper(void* arg)
   {
      MyThread* t = reinterpret_cast<MyThread*>(arg);

      for (int i = 0; i < t->iterations; ++i)
      {
         std::cout << "The thread is running." << std::endl;
      }

      return 0;
   }

   int       iterations;
   pthread_t tid;
};


int main()
{
   MyThread thread;

   thread.start();

   int* status = 0;

   pthread_join(thread.getThreadID(), (void**) &status);

   return 0;
}

```
Of course, the code above is not completely OO-ish, but it demonstrates the fundamentals.

---

### Post by balteo on 2010-10-19
Ok... 
Thanks.
J.

---

