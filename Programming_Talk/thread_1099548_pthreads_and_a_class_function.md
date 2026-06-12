---
title: "pthreads and a class function"
date: 2009-03-18
forum: Programming Talk
---

### Post by cybo on 2009-03-18
i have just started learning pthreads in c++. i need to create a thread which will run a class function. but for some reason i'm getting an error.

here is what i'm doing:

MyClass.h file
```

class MyClass {
  public:
    void my_method(int d);
}

```

main.cpp file
```

#include <pthreads.h>
#include "MyClass.h"
#define THREAD_COUNT 3

int main (int argc, char** argv) {
  pthread_t thread[THREAD_COUNT];
  MyClass object;
  for (int i = 0; i < THREAD_COUNT; i++)
    pthread_create(&thread[i],
      NULL,
      (void*)object.my_method,
      (void*)&i);

  for (int i = 0; i < THREAD_COUNT; i++) {
    pthread_join(thread[i], NULL);
  }

  return 0;
}

```

after compilation i get the following error:
main.cpp: In function ‘int main(int, char**)’:
main.cpp:14: error: invalid use of member (did you forget the ‘&’ ?)

line 14 is (void*)object.my_method

does anyone know what i'm doing wrong and how to fix it?

---

### Post by geirha on 2009-03-18
pthread_create takes a pointer to a function, but you are giving it a function, so the guess in the error message is correct, you forgot the address of (&) operator.
Try with:
```
      (void*)&(object.my_method),
```

EDIT: But testing myself, it seems you are not allowed to do that in c++. Does make sense though, since the method is dependant on the other members of the class.

---

### Post by dwhitney67 on 2009-03-18
Consider using Boost threads.  It's much easier.
```

class MyThread
{
  public:
    MyThread() {}

    void operator()()
    {
       // do whatever you thread requires
    }
};

int main()
{
  using namespace boost;

  MyThread t1;
  MyThread t2;

  thread_group threads;
  threads.add_thread(new thread(t1));
  threads.add_thread(new thread(t2));

  threads.join_all();   // start the threads
}

```

If you do not want to commit yourself to Boost, then try using the "Lite-Boost" library (see attachment) I created, which has a similar interface to Boost.

If you still want to do it your way, please understand that for a C-library to call a function, that function must be a free-floating function; it cannot be within a class object.

This free-floating function can be used however, to summon your class object if you pass an object instantiation of your class as the parameter to the thread's start routine.

So, something like:
```

void* helper(void* arg);

class MyThread
{
  public:
    MyThread() {}

    void run()
    {
       // do something
    }
};

int main()
{
  MyThread* mt = new MyThread;

  pthread_create(&tid, 0, helper, mt);
  ...
};

void* helper(void* arg)
{
  MyThread* mt = reinterpret_cast<MyThread*>(arg);
  mt->run();
  return NULL;
}

```

If your thread class requires any special information, then pass this info via the class constructor.  This data will be available to the run() method.

---

### Post by cybo on 2009-03-18
dwhitney67, thanks for the help.

---

### Post by hendrixj on 2009-03-20
Only static member functions can be passed as the start point for pthreads. A typical approach is the following:
```

class Thread
{
public:
    
    /**
     * This method is used to launch the thread.
     */
    void start() {
       int status = ::pthread_create(&thread_id, 
                                     &attributes, // or defaults 
                                     entry, 
                                     this);
        if (status != 0) {
        // report error
        }
    }
    
    /**
     * Run method for the thread.
     */
    virtual void run() {}
    

private:
    static void* entry(void* thread) {
            (Thread*)(thread)->run();
            return NULL;
    }
    
    pthread_t thread_id;
};


```

You see that start() invokes pthread_create handing in the this pointer of the object. Now entry can invoke the run method of the object.
Now derive specific thread classes from Thread, overloading the run() method for your specific application.
class DerivedThread : public Thread { ... }
Then, 
DerivedThread dthread;
dthread.start();

There are a lot of possibilities from here.

---

### Post by cybo on 2009-03-22
hendrixj, thank you for the advice

---

### Post by cybo on 2009-03-22
hendrixj,

i don't have much experience with c++. how would i implement a pthread_joing using a Thread class?

---

### Post by dwhitney67 on 2009-03-22
The example provided by hendrixj, encapsulates the functionality of the pthread_create() function to start a thread.  You should be able to do the same with the pthread_join() function.

A common practice is to define an abstract base Thread class that is used to define your other threads.  Here's a sample:

```

class Thread
{
  public:
    Thread();
    virtual ~Thread();

    virtual int run() = 0;

    void* join();
    void* joinAny();

  private:
    static void* entry(void* arg);

    pthread_t       m_tid;
    pthread_attr_t* m_attr;
};

class MyThread : public Thread
{
  public:
    MyThread();
    ~MyThread();

    virtual int run();
};

```

The Thread::join() would be something like:
```

void*
Thread::join()
{
  void* status = 0;

  if (pthread_join(m_tid, &status) != 0)
  {
    // error
  }

  return status;
}

```

The Thread::entry(), as hendrixj indicated, should be something like:
```

void*
Thread::entry(void* arg)
{
  Thread* t = static_cast<Thread*>(arg);

  int status = t->run();

  pthread_exit((void*) status);

  return NULL;
}

```

The Thread::joinAny() is a method that requires a little extra effort.  I will not provide a solution here, but basically it would allow the main thread to join with any terminating child-thread, not just a specific one as required when dealing with pthread_join().

---

### Post by cybo on 2009-03-27
thank you, dwhitney67

---

