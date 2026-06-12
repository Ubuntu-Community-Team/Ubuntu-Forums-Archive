---
title: "POSIX threads"
date: 2010-05-17
forum: Programming Talk
---

### Post by youralibaba on 2010-05-17
In c++ POSIX thread programming.

#include<pthread.h>
void *function(void *parameter);

void main(){
int input;
pthread_create(thread ID, NULL, function, (void *) input);

}

The question is why there is (void *) input in the argument of pthread_create ? Shouldn't the argument be &input ? The function is void *function(void *). It should be given &input in the argument. Why is input casted to void * ?

---

### Post by tbastian on 2010-05-17
> **youralibaba said:**
> In c++ POSIX thread programming.

#include<pthread.h>
void *function(void *parameter);

void main(){
int input;
pthread_create(thread ID, NULL, function, (void *) input);

}

The question is why there is (void *) input in the argument of pthread_create ? Shouldn't the argument be &input ? The function is void *function(void *). It should be given &input in the argument. Why is input casted to void * ?

It should be ```
(void*) &input
``` You are casting an into into a pointer, which works, but its not casted to the pointer of that int.
eg.```
int intPtr = 123456;
void * ptr = (void*)intPtr;
```

in this example ptr points to the memory location 123456, not the location of intPtr

---

### Post by MadCow108 on 2010-05-17
this trick is often used to easily pass an integer number into the function. The reason is that it gets copied to the function.
if you would pass the pointer to the integer the pointer goes bad when the integer pointed to goes out of scope. e.g.:
```

{
int a = 3;
pthrea_create(..., &a);
}
// a gets deleted but thread may still access it !!!

```
by passing by value this cannot happen.

but the portability of this is a little bit dubious, as integers and pointers may not have the same size ( at least use long or intptr_t)
a better approach is to allocate it dynamically or make sure it does not go out of scope (e.g. a pthread_join before that happens).

---

### Post by dwhitney67 on 2010-05-17
> **youralibaba said:**
> In c++ POSIX thread programming.


In C++, a cleaner/clearer way to develop a Posix thread is to define the class that actually performs the task.  For example:

```

#include <pthread.h>


class MyThread
{
public:
   MyThread(const int value) : myValue(value) {}

   void start()
   {
      pthread_create(&myTID, NULL, run, this);
   }

   pthread_t getTID() const { return myTID; }

private:
   static void* run(void* arg)
   {
      MyThread* mt = static_cast<MyThread*>(arg);

      // access to myValue is now available via the mt pointer

      return 0;
   }

   // data members
   int       myValue;
   pthread_t myTID;
};


int main()
{
   MyThread thread(12345);
   thread.start();

   int* status;
   pthread_join(thread.getTID(), (void**) &status);
}

```
Of course, another alternative is to use Boost, but then you would have an additional dependency that may not be desirable.

---

### Post by slavik on 2010-05-17
since C does memcpy for structs, you can pass those ;) (I know, this is about C++).

---

### Post by Andi018 on 2010-12-07
I have to write this program for school, using POSIX threads:

Two very large numbers are given, each having a million of
digits, the numbers being represented as strings. The digits are
randomly generated. Using a given number of threads (as
parameter), sum up the two numbers. A thread will sum 2 digits,
with left carry. A thread will start the summing on a position
that can't be affected by a carry from summing the neighbor
digits by other threads. The program will dispay the sum and
also the process time.  Mutexes and/or conditional variables
will be used.

I have no idea how to do it. If anyone could help, I'd be forever grateful.

---

### Post by dwhitney67 on 2010-12-07
Seems like an interesting school assignment.

Unfortunately, this forum is not to be used as a homework service.  In other words, you will have to do the work on your own.

---

