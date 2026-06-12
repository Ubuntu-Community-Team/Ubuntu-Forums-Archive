---
title: "Creating threads in C++"
date: 2010-02-24
forum: Programming Talk
---

### Post by primenu on 2010-02-24
I want to have my two methods of an object in c++ run concurrently. And while doing this if these two concurrent methods work on the instances of other class created within this object, how do I maintain the consistency. I am having trouble with a queue being modified unethically one removes the queue while the other is trying to read from it, I assume this is whats happening, and I get segmentation faults, trying to access a invalid field.
DO I need to create mutex lock if so how do i do it, and with creating threads in c++, can the threads be defined as properties of the class, and be called upon using the object of that class to run its two methods concurrently.

---

### Post by dwhitney67 on 2010-02-24
Are you using Boost or the pthread library?

In either case, yes a mutex is required; STL containers are not thread safe, and most likely if you have a home-made one, the same applies.

If you opt to use a POSIX Message Queue, then you would be ok without the mutex.  But they operate slower than the STL queue paired with a mutex (well, at least from what was discovered on a project I worked on under Solaris).

Let me know which library you are using; I have examples I can show you for each.

---

### Post by radeon21 on 2010-02-24
I can dig up some example code if you are using QThreads.

---

### Post by primenu on 2010-02-24
I am using the pthread library.

---

### Post by dwhitney67 on 2010-02-24
Something like this could (and should) work:
```

#include <queue>
#include <pthread.h>

template <typename T>
class Queue
{
public:
   Queue() {}

   void push(T* item)
   {
      ScopedLock scoped(mutex);

      queue.push(item);
   }

   T* pop()
   {
      ScopedLock scoped(mutex);

      T* item = 0;

      if (queue.size() > 0)
      {
         item = queue.front();
         queue.pop();
      }

      return item;
   }

private:
   class ScopedLock
   {
   public:
      ScopedLock(pthread_mutex_t& m)
         : mutex(m)
      {
         pthread_mutex_lock(&mutex);
      }

      ~ScopedLock()
      {
         pthread_mutex_unlock(&mutex);
      }

   private:
      pthread_mutex_t& mutex;
   };

   std::queue<T*>  queue;
   pthread_mutex_t mutex;
};

```

The class above represents a thread-safe queue that you can either instantiate and pass by reference to your two threads, or you can embed (encapsulate) it within the consumer thread and of course provide the interface for the producer to use it.


P.S.  I did not include any error checking for the pthread library calls.  Add these if you feel it is necessary.

---

### Post by primenu on 2010-02-24
thanks for the help :)

---

