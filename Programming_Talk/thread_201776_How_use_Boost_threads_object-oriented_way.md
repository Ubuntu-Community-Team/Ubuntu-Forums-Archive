---
title: "How use Boost threads object-oriented way?"
date: 2006-06-22
forum: Programming Talk
---

### Post by Laterix on 2006-06-22
I need to use multiple threads in my C++ application and I planed to use Boost threads, because it should be portable thread class for C++, right? Anyway, I can't figure out how could I use it object-oriented way so that one of my Object's methods would run in seperated thread (compare to Java's run() and Thread class inheritance). Boost thread seems to me just a wrapper around POSIX threads without real object-oriented touch. I must be missing something here?

I know how to create a thread of the function, but I can't give a pointer to function owned by some spesific object for example this->myThread();

Threads tutorial on Boost site is quite poor, I think.

---

### Post by LordHunter317 on 2006-06-22
[QUOTE=Laterix]I need to use multiple threads in my C++ application and I planed to use Boost threads, because it should be portable thread class for C++, right?[/quote]For what little features it provides, sure.

> Anyway, I can't figure out how could I use it object-oriented way so that one of my Object's methods would run in seperated thread (compare to Java's run() and Thread class inheritance). Boost thread seems to me just a wrapper around POSIX threads without real object-oriented touch. I must be missing something here?Well yes, because pthreads are the bare minimum.

> I know how to create a thread of the function, but I can't give a pointer to function owned by some spesific object for example this->myThread();No, you cannot.  You'll have to write a function adapter that meets the requirements of boost::threads but takes a pointer-to-member function of what you want to call.

---

### Post by fleeb on 2008-03-25
There's an okay example of how to do it here:

[http://www-eleves-isia.cma.fr/documentation/BoostDoc/boost_1_29_0/libs/thread/doc/thread.html](http://www-eleves-isia.cma.fr/documentation/BoostDoc/boost_1_29_0/libs/thread/doc/thread.html)

The libs/thread/example/thread.cpp example is the better one for what you probably want to do.

In my own work with boost's thread library, I created a functor that is instantiated with a class with a 'run()' function for the thread I wish to run.  The operator()() function then simply calls my instance's run() function.  Not so hard, really, and is relatively OO.

You have to create your own mechanisms for stopping the thread (perhaps with a stop() function), and handle your own policies regarding resource management across the threads, although the library does provide some tools for helping you with that.

I actually kind of like the stark simplicity of boost::thread.  It's very focused on just providing the bare necessities.  You can probably build whatever you need from it, provided you don't want to do anything terribly event-oriented.

---

### Post by dribeas on 2008-07-15
> **Laterix said:**
> I can't figure out how could I use it object-oriented way so that one of my Object's methods would run in seperated thread (compare to Java's run() and Thread class inheritance). Boost thread seems to me just a wrapper around POSIX threads without real object-oriented touch. I must be missing something here?

I know how to create a thread of the function, but I can't give a pointer to function owned by some spesific object for example this->myThread();

Threads tutorial on Boost site is quite poor, I think.

First things first: Calling an specific method from a class:

```

class X {
public: 
   void run();
   void complexOperation( int limit );
};
...
X x;
boost::thread thr1( boost::bind( &X::run, &x ) );
boost::thread thr2( boost::bind( &X::complexOperation, &x, 30 ) );
boost::thread thr3( boost::bind( &X::complexOperation, &x, 100 ) );
... // while threads work in background
thr1.join();
thr2.join();
thr3.join();
```

In the sample code above an X object is created, and then three threads  are created, one of them calling a run() method (java equivalent) and the other two calling a method with a complete different signature: complexOperation(int).

As you see it is quite simple to call an specific method, and as it is (and combined with boost::bind library) much more generic than Java solution.

I have not followed the design of boost:thread, but from my experience (both Java and C++) if the working code and the thread are both in the same class (or class hierarchy) it is tempting and easy to fall into a common pitfall: creating a hierarchy where a class takes care of the common thread code: starting the thread during construction (and in C++ destroying/stopping/joining the thread during destruction), then deriving worker classes to inherit the behaviour.

```
// C++ syntax
class BaseThread { ... }; 
   // creates thread in constructor
   // joins thread in destructor

class Worker : public BaseThread { ... };
   // implements real work in a inherited virtual method (run()?)
```

Now the problem (in the worst case) is that during construction of a Worker object, BaseThread is constructed first, which starts the thread before Worker object has yet been created yielding strange behaviour. In C++ if the run method is pure virtual then a 'pure virtual method called' error is raised and the program terminates. If the method has a default implementation in BaseThread, then that implementation is called instead of the implementation in Worker class. In Java the same problem occours with a different result: the method is correctly called in the derived class, but all member data in Worker will be uninitialized during the call.

The 'worst case' happens when the processor is yielded to the newly created thread before Worker construction is completed in the creating thread. That makes it an even worse problem as you can run the program many times without any problem and get random crashes or unexpected behaviour each so often, making it quite hard to diagnose and debug.

Of course, as long as you don't call startThread (Java), activate (C++ with ACE) or create the thread object (Boost::Thread) until complete creation of the real worker object then it is a no-problem, but beware.

David Rodríguez Ibeas

---

### Post by KaenGuru on 2010-07-22
Actually the boost::bind(...) ain't necessary. Here's an basic example:

**main.cpp file**
```
[COLOR=Purple]#include <boost/thread.hpp>
#include "ThreadClass.h"[/COLOR]

[COLOR=SeaGreen]int[/COLOR] main([COLOR=SeaGreen]int[/COLOR] argc, [COLOR=SeaGreen]char[/COLOR]* argv[]) {
    ThreadClass [COLOR=Navy]tc[/COLOR];
    boost::thread thread(&[COLOR=Navy]ThreadClass::Run[/COLOR], &[COLOR=Navy]tc[/COLOR]);
    thread.join();

    return 0;
}

```**ThreadClass.cpp file**
```
[COLOR=Purple]#include "ThreadClass.h"[/COLOR]

ThreadClass::ThreadClass() { } [COLOR=Gray]// Constructor[/COLOR]
ThreadClass::~ThreadClass() { } [COLOR=Gray]// Destructor[/COLOR]

[COLOR=SeaGreen]void[/COLOR] [COLOR=Navy]ThreadClass::Run()[/COLOR] {
    [COLOR=Red]// Thread execution stuff goes here[/COLOR]
}

```**ThreadClass.h file**
```
[COLOR=Purple]#ifndef THREADCLASS_H_
#define THREADCLASS_H_[/COLOR]

class ThreadClass {
    public:
        ThreadClass(); [COLOR=Gray]// Constructor[/COLOR]
        ~ThreadClass(); [COLOR=Gray]// Destructor[/COLOR]
        [COLOR=SeaGreen]void[/COLOR] [COLOR=Navy]Run()[/COLOR];
};

[COLOR=Purple]#endif[/COLOR]
```

---

### Post by cs.lev on 2011-02-01
> **cs.lev said:**
> I tried both of your, and nothing worked:-?! by the first the compiler said:
error: ‘bind’ is not a member of ‘boost’. The second one didn't work neither.

g++ -lboost_thread-mt  main.cpp ThreadClass.cpp -o 1

main.cpp: In function ‘int main(int, char**)’:
main.cpp:7: error: no matching function for call to ‘boost::thread::thread(void (ThreadClass::*)(), ThreadClass*)’
/usr/include/boost/thread/pthread/thread.hpp:160: note: candidates are: boost::thread::thread(boost::detail::thread_move_t<boost::thread>)
/usr/include/boost/thread/pthread/thread.hpp:144: note:                 boost::thread::thread()
/usr/include/boost/thread/pthread/thread.hpp:139: note:                 boost::thread::thread(boost::detail::thread_data_ptr)
/usr/include/boost/thread/pthread/thread.hpp:112: note:                 boost::thread::thread(boost::thread&)

any idea???](*,)

#include <boost/bind.hpp> solved the first one, but the second example is still not working...

---

