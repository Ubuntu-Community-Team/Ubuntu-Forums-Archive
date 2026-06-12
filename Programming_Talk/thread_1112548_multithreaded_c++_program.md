---
title: "multithreaded c++ program"
date: 2009-03-31
forum: Programming Talk
---

### Post by piratebill on 2009-03-31
Hi, I am trying to use threads, and not having any luck.  I have read many tutorials (here [http://blog.emptycrate.com/node/270](http://blog.emptycrate.com/node/270), [https://computing.llnl.gov/tutorials/pthreads/](https://computing.llnl.gov/tutorials/pthreads/) and a few others).  As far as I can tell I am following the instructions to the letter (but that cant be the case, because I somehow am screwing this up).  Anyway, enough ranting, here is my code

[PHP]
void mkthread(int total)
{

        //create thread objects
        pthread_t thread[total];
        int status=pthread_create(&thread[1],NULL,dummy_function,NULL);
        pthread_exit(NULL);
}

void dummy_function()
{

}
[/PHP]

I just want to get the thing to compile, even if it doesn't do anything (because it will later).  The error I am getting is ```
invalid conversion from ‘void (*)()’ to ‘void* (*)(void*)’
```.  With one tutorial I copied and pasted the code given and still got the same error.  Would someone mind telling me what I am doing wrong?

---

### Post by Peasantoid on 2009-03-31
In the call to pthread_create(), try replacing "dummy_function" with "&dummy_function". This is generally how C function pointers are written.

---

### Post by piratebill on 2009-03-31
just tried it.  Same error.

---

### Post by dwhitney67 on 2009-03-31
It appears that you want to start an array of threads, when it is obvious that you do not even know how to start one.  I suggest that you take things in small steps, and once you understand what you are doing, then you proceed to experiment with adding additional threads.

Since you have chosen to implement code in C++, you have two choices available to create threads:  you can use the Boost library or you can use the C library.

Here are examples of each...

Using Boost:
```

#include <boost/thread/thread.hpp>
#include <iostream>
#include <unistd.h>

class MyThread
{
  public:
    MyThread() {}

    void operator()()
    {
      for (;;)
      {
        std::cout << "thread is running..." << std::endl;
        sleep(1);
      }
    }
};

int main()
{
  MyThread mt;

  boost::thread_group threads;

  threads.add(new thread(mt));

  threads.join_all();
}

```

Using C library:
```

#include <pthread.h>
#include <iostream>
#include <unistd.h>

class MyThread
{
  public:
    MyThread()
    {
      pthread_create(&m_tid, 0, thread_helper, this);
    }

    ~MyThread()
    {
    }

    pthread_t getId() const
    {
      return m_tid;
    }

  private:
    void operator()()
    {
      for (;;)
      {
        std::cout << "thread is running..." << std::endl;
        sleep(1);
      }
    }

    static void* thread_helper(void* arg)
    {
      MyThread* t = static_cast<MyThread*>(arg);

      (*t)();  // call operator()()

      pthread_exit(0);
      return 0;
    }

    pthread_t m_tid;
};

int main()
{
  MyThread mt;

  void* status = 0;

  pthread_join(mt.getId(), &status);
}

```

---

### Post by piratebill on 2009-03-31
I would use boost, but this is a school project and I have to use pthreads.  Let me make sure I understand how this works

```
MyThread()
    {
      pthread_create(&m_tid, 0, thread_helper, this);
    }

```

the &m_tid is the name of the thread to create
the 0 is an attribute you can give the thread
thread_helper is the name of the function to execute once created
this I think gets passed to the function.


Is that right?

---

### Post by dwhitney67 on 2009-03-31
> **Peasantoid said:**
> In the call to pthread_create(), try replacing "dummy_function" with "&dummy_function". This is generally how C function pointers are written.
No they are not!

When you pass a function, you are in essence passing the address of it.  There is no need to pre-qualify the function name with an &.  What is needed is a better declaration for the thread start-routine.  It should have the format:
```

void* start_routine(void* arg);

```

---

### Post by dwhitney67 on 2009-03-31
> **piratebill said:**
> ...
the &m_tid is the name of the thread to create
the 0 is an attribute you can give the thread
thread_helper is the name of the function to execute once created
this I think gets passed to the function.


Is that right?

You scored 3 out of 4, or 75%... and that is being lenient!

The m_tid is the thread ID; it is not a name.  You do not provide an ID, but instead pthread_create() returns one to you.  You use this ID when accessing other pthread functions such as pthread_join(), pthread_detach(), etc.

The second arg to pthread_create() is used for specifying the thread attributes; if none are specified (0 is passed), then the system default settings for threads is used.  This is described in the man-page for pthread_create().

---

### Post by piratebill on 2009-03-31
Ok, am I using the thread ID part correctly then?  If I am, what is causing the error?

> What is needed is a better declaration for the thread start-routine

So you are saying to recode void mkthread(int); into void* mkthread(void* arg, int);?

I have been reading for hours trying to figure this out, and I just don't know what is I am doing wrong.

---

### Post by dwhitney67 on 2009-03-31
> **piratebill said:**
> ...
So you are saying to recode void mkthread(int); into void* mkthread(void* arg, int);?
....
pthread_create() requires that you pass a function that is declared as void* mkthread(void* arg).  You cannot pass any other args to it, and if coding in C++, you don't need to because any ancillary data you wish to use in your thread can be passed to your object's constructor, and then accessed within the operator()() method.

In C, it's a different story; one needs to create a structure with all the data required by the thread, and then pass that structure via the arg parameter of mkthread().  For C++, you just pass the "this" of the class object as the arg.

If you wish to write your C++ code in C-style (which it seems so many newbie C++ programmers tend to do), then define a structure to hold your data.

```

struct Data
{
  int value1;
  int value2;
};

...
Data data = { 10, 20 };
pthread_create(&tid, 0, mk_thread, &data);
...

void* mk_thread(void* arg)
{
  Data* d = static_cast<Data*>(arg);

  std::cout << "thread is running...\n"
            << "data value1 = " << d->value1 << '\n'
            << "data value2 = " << d->value2
            << std::endl;

  ...
}

```

---

### Post by piratebill on 2009-03-31
> **dwhitney67 said:**
> 

If you wish to write your C++ code in C-style (which it seems so many newbie C++ programmers tend to do), then define a structure to hold your data.



I don't want to write c style code, but unless you know of another way to use pthreads I am kind of stuck doing so.  As for renaming the function passed to pthread_create, it now looks like this:


[PHP]void mkthread(int total)
{

        //create thread objects
        pthread_t thread[total];
        int status=pthread_create(&thread[1],0,dummy_function,NULL);
        //socket call
        pthread_exit(NULL);
}

**void* dummy_function(void*)**
{

}[/PHP]

Now it tells me ```
undefined reference to `pthread_create'|
```.

Btw, thanks for the struct example.

---

### Post by dwhitney67 on 2009-03-31
> **piratebill said:**
> I don't want to write c style code, but unless you know of another way to use pthreads I am kind of stuck doing so. ...

I provided two C++ examples in the first post I issued in this thread; one that uses Boost, and another that uses pthread_create().  I understood that you needed to use the latter.

There is no need to develop a C-style application.  If you require an integer value for your thread, then pass this value to the MyThread constructor.

```

class MyThread
{
  public:
    MyThread(int value) : m_value(value)
    {
       ...
    }

    void operator()()
    {
      for (int i = 0; i < m_value; ++i)
      {
        std::cout << "thread is running..." << std::endl;
      }
    }

    ...

  private:
    ...
    int m_value;
};

int main()
{
  MyThread mt(10);
  ...
}

```

Anyhow, look carefully at the second example in my previous post, and incorporate what is shown above.

Btw, when you link your application, do not forget to link with the pthread library.
```

g++ MyApp.cpp -lpthread

```

---

