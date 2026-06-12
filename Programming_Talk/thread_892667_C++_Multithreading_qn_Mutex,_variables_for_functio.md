---
title: "C++ Multithreading qn Mutex, variables for function"
date: 2008-08-17
forum: Programming Talk
---

### Post by Ristar on 2008-08-17
hi...

i wanna ask 2 things...

1) i notice that i cant pass in a "complex" data type, like string, or classes into pthread_create(). so, im limited to passing only one variable into the function aFunc(). is there a way to pass more than one variable and/or data types like string and classes?


2) how do i mutex lock aFunc()? and where do i trylock() it? can u kindly write the code that's mutex related onto the code below? including the initialisation and stuff.
that'll really help, coz i have totally no idea, and searches on google proved futile.


```

...

int main(){
    char aVar [] = "Yo!";
    ...
    pthread_t thread;
    int retVal = pthread_create(&thread, NULL, aFunc, (void *) aVar);
    ...
    pthread_join(&thread,NULL);
    ...
}

void *aFunc(void * aVarPtr){
    char *aVar = (char * ) aVarPtr;
    ...
}

```


thanks.

---

### Post by kpatz on 2008-08-17
> **Ristar said:**
> 1) i notice that i cant pass in a "complex" data type, like string, or classes into pthread_create(). so, im limited to passing only one variable into the function aFunc(). is there a way to pass more than one variable and/or data types like string and classes?That "one" variable you pass is a void pointer, which can "point to" (and be cast to) anything.  So, pass a pointer to a struct or class containing the data you want to pass to your threaded function.> 2) how do i mutex lock aFunc()? and where do i trylock() it? can u kindly write the code that's mutex related onto the code below? including the initialisation and stuff.


```

...
// Create initialized mutex variable.
pthread_mutex_t mut = PTHREAD_MUTEX_INITIALIZER;

int main(){

    char aVar [] = "Yo!";
    ...
    pthread_t thread;
    int retVal = pthread_create(&thread, NULL, aFunc, (void *) aVar);

//  This code is critical and needs to be mutex locked, so aFunc's critical section doesn't execute
// at the same time as this critical code.
    pthread_mutex_lock(&mut);
    ... critical code goes here...
    pthread_mutex_unlock(&mut);

    ...
    pthread_join(&thread,NULL);
    ...
}

void *aFunc(void * aVarPtr){
    char *aVar = (char * ) aVarPtr;
    ...
//  This code is critical and needs to be mutex locked
    pthread_mutex_lock(&mut);
    ... critical code goes here...
    pthread_mutex_unlock(&mut);
}

```

pthread_mutex_lock() will block (suspend execution) while the mutex is locked, then will continue when it is unlocked.  pthread_mutex_trylock() doesn't block, instead it returns an error if the mutex is locked.

---

### Post by dwhitney67 on 2008-08-17
Kpatz's answers are correct, however the OP should consider using the Boost libraries.

When using Boost, a thread object can be defined as follows:
[PHP]
#include <boost/thread/thread.hpp>

class MyThread
{
  public:
    MyThread() {}

    void operator()(void) { /* do thread work here... */ }
};

int main()
{
  // Instantiate a MyThread object...
  //
  MyThread myThread;

  // Create thread from MyThread object...
  //
  boost::thread *t = new boost::thread( myThread );

  // Setup a thread group...
  //
  boost::thread_group threads;
  threads.add_thread( t );

  // Run the thread(s)...
  //
  threads.join_all();

  return 0;
}[/PHP]
If the thread object, and in the case above MyThread, requires any special data, the data can be supplied via its constructor, just like one would do with any other type of class object.

In the case mutexes, one can use the Boost mutex and the Boost scoped_lock.  Below is a simple example of an object that presumably needs to be thread-safe:
[PHP]#include <boost/thread/mutex.hpp>

class ThreadSafeObject
{
  public:
    ThreadSafeObject() {}

    void someMethod()
    {
      boost::mutex::scoped_lock scoped( m_mutex );

      // do critical section here...
    }

  private:
    boost::mutex m_mutex;
};[/PHP]
In reference to passing objects to your threads, the ThreadSafeObject could be passed to MyThread such as:
[PHP]//...

class MyThread
{
  public:
    MyThread( ThreadSafeObject &tso )
      : m_tso( tso )
    {
    }

    // ...

  private:
    ThreadSafeObject & m_tso;
}

int main()
{
  ThreadSafeObject tso;

  MyThread myThread( tso );

  // ...
}[/PHP]
In conclusion, the Boost libraries enable one to simplify their code and also to make it portable to other platforms (e.g. the dreadful Windoze).

I still recommend that you learn the fundamentals of using the C-library pthread functions, however once you understand those, you should consider migrating to using boost.

P.S.  If you find yourself creating multiple threads and repeatedly using the C-library pthread calls, you should consider writing a wrapper-class around them.  At a minimum, the wrapper-class for pthread_create() should have a constructor, a start() method, and a pure-virtual run() method.  Let me know if you would like further details on how to implement this.

---

### Post by Ristar on 2008-08-17
thanks for your replies guys.



dwhitney67...

i'd love to use the Boost libs... but, there arent any during the exams. :P

thanks for all that, anyway.

---

