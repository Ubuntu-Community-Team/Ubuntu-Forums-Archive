---
title: "Pthread void *"
date: 2011-05-03
forum: Programming Talk
---

### Post by roadkillguy on 2011-05-03
If you've ever used pthreads in c++, you probably know that to start a thread, you need to typecast any arguments into a void *.  The thread I am attempting to create requires two parameters; a this pointer, and an int.  Normally it's possible to fit both arguments into a struct, and feed the pointer of the struct into pthread_create, right?  Unfortunately, my thread isn't created until the end of it's calling function, which ends up destroying the argstruct before the pthread can get ahold of it.

How do I ensure the pthread gets called before it's calling function gets destroyed?

```
function()
{
  cout << 1 << endl;
  pthread_create(&thread, NULL, function2, (void *)&data);
  cout << 3 << endl;
}
void *function2(void * _data)
{
  //TYPECAST OF _data REVEALS BOGUS DATA
  cout << 2 << endl;
}
```

This will output 1, 3, 2.
I would like it to output 1, 2, 3.

Any suggestions?

---

### Post by johnl on 2011-05-03
You don't want 'the pthread to get called before the argument gets destroyed'.  You want the argument to not be destroyed until the thread is done with it.

You can do this by allocating it dynamically in your calling function (new()) and freeing it once you're done with it in the thread function (delete()).  Or you can store it in a global variable or a global thread-specific structure.  Normally if you have a bunch of worker threads doing the same task, you might have a global registry like this:

```

struct thread_data {
    int my_data1;
    string name;
    void*  foo;
};

struct thread_data data[16];
pthread_t threads[16];

/* now when we create a thread we can just pass in
 * the index into the array of the thread's structure */
for(int i = 0; i < 16; ++i) {
    pthread_create(&threads[i], NULL, function2, (void *)i);
}

/* in our thread function: */
struct thread_data* mydata = &data[(int)arg];

```

---

### Post by dwhitney67 on 2011-05-04
> **johnl said:**
> You don't want 'the pthread to get called before the argument gets destroyed'.  You want the argument to not be destroyed until the thread is done with it.

correct.
> **johnl said:**
> 
You can do this by allocating it dynamically in your calling function (new()) and freeing it once you're done with it in the thread function (delete()).

yes, one possibility.

> **johnl said:**
> Or you can store it in a global variable or a global thread-specific structure.

Bad advice... remember, this is C++, not C.  In fact, even in C this would not be necessary.  Avoid declaring global variables.

In C++, data should be encapsulated within a class declaration.  A thread could be declared as:
```

#include <pthread.h>
#include <iostream>

class Thread
{
public:
   Thread(int data) : myData(data), myTid(0) {}

   void start()
   {
      pthread_create(&myTid, NULL, myHelper, reinterpret_cast<void*>(myData));
   }

   void join()
   {
      pthread_join(myTid, NULL);
   }

private:
   static void* myHelper(void* arg)
   {
      int data = reinterpret_cast<int>(arg);

      // note: cout is NOT thread-safe!
      //
      std::cout << "data = " << data << std::endl;

      return NULL;
   }

   int       myData;
   pthread_t myTid;
};

int main()
{
   Thread thread(10);  // instantiate thread object

   thread.start();     // start thread
   thread.join();      // wait for thread to finish before continuing

   //...
}

```
If more elaborate data needs to be defined for a thread, then yes, declare a struct or class object that the thread object can accept as a parameter.  But there should be no need to declare a global variable, even if shared amongst multiple threads.  Concurrent access to a data object may need to be regulated with the use of a mutex or semaphore.


P.S.  @ the OP -  When passing the address of an object as the arg into the pthread_create() function, the casting of said object to a void* is not necessary.  Only when passing a non-pointer object is the void* cast required.

---

### Post by roadkillguy on 2011-05-04
Hmmm... I didn't know you didn't have to void * cast...

I can't believe I didn't think of _***new***_ memory.  I'll probably implement that class.

Thanks guys!

Also, the only reason I pass in that pointer is because I want a member function to be threaded.  Is there any way to not use a global function?

---

### Post by dwhitney67 on 2011-05-04
> **roadkillguy said:**
> 
Also, the only reason I pass in that pointer is because I want a member function to be threaded.  Is there any way to not use a global function?
See the example I presented earlier.  Although the function I used is declared as static, it is nevertheless a member function of the class.

---

### Post by johnl on 2011-05-04
**dwhitney67**, good points.  I am more of a C fellow so I forget these sorts of things :)

It also might be worthwhile to look into something more C++-oriented than pthreads, like [boost::thread](http://www.boost.org/doc/libs/1_46_1/doc/html/thread.html).

---

### Post by roadkillguy on 2011-05-04
Is boost compatible with mingw?  I'm currently cross compiling my application using mingw32-msvc-g++.

---

