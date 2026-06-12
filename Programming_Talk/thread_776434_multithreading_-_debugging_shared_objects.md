---
title: "multithreading - debugging shared objects"
date: 2008-04-30
forum: Programming Talk
---

### Post by melopsittacus on 2008-04-30
Hi, I am writing a multi-threaded program in C++ with the libpthread library. Some objects are being accessed from more threads. I want to be able to know  from which thread a given member function is called. 

To achieve this I thought about writing a logger class, and each thread would have its own logger object which knows the thread's name, and each main step would be logged using that logger object, so that it can output the name of the thread as well.

This approach works well when logging from the thread's own function. The problem is, however, how to log from the member functions of the common objects. Is there a better solution than that of explicitely passing a pointer to each and every member?

---

### Post by scourge on 2008-04-30
I think pthread_self() is what you're looking for: [http://opengroup.org/onlinepubs/007908775/xsh/pthread_self.html](http://opengroup.org/onlinepubs/007908775/xsh/pthread_self.html)

---

### Post by dwhitney67 on 2008-04-30
> **melopsittacus said:**
> Hi, I am writing a multi-threaded program in C++ with the libpthread library. Some objects are being accessed from more threads. I want to be able to know  from which thread a given member function is called. 

To achieve this I thought about writing a logger class, and each thread would have its own logger object which knows the thread's name, and each main step would be logged using that logger object, so that it can output the name of the thread as well.

This approach works well when logging from the thread's own function. The problem is, however, how to log from the member functions of the common objects. Is there a better solution than that of explicitely passing a pointer to each and every member?
Why don't you output a diagnostic message from within your thread object just before it calls the shared object?

Also, I presume that you have Unit Tested your shared object(s) before mixing them with the multi-thread application to ensure that they are "bullet-proof".

If you are manipulating complex data in shared objects, ensure that the critical sections are guarded against concurrent access using a pthread mutex or pthread condition.

---

### Post by melopsittacus on 2008-05-04
Hi, Scourge and Dwhitney, thanks for helping me.

The pthread_self() has been quite useful: after all what I did is that I added a static member for the Logger class, whose type is std::map<int, Logger *>. When a new Logger object is created it registers itself in that map. Then whenever I have to log from an unknown thread, I log through a static function of the Logger class which queries the ID of the actual thread, and based on that retrieves the corresponding Logger object.

@Dwhitney: logging only from outside would not give too precise results, as I also wanted to map the call hierarchy of the members of the shared objects.
And I did test the objects, but alas only without synchronization, so I began to get deadlocks when I added the mutexes, that's why I ended up writing Loggers :)

---

### Post by stroyan on 2008-05-04
There are other ways to create thread-specific data.
The posix thread standard includes the functions pthread_key_create,
pthread_setspecific, and pthread_getspecific.  They can be used
to create and look up thread specific data.

Another more recent approach tries to avoid the overhead of explicit
function calls by extending compilers to know that certain global
variables are supposed to have thread-specific copies.  That is called
thread-local-storage.  A __thread attribute can be given to global
variables that are POD (plain ol' data).  That means it can be applied
to a variable of type int or a pointer to a class.  But it can't be
applied to a class variable.
```

__thread int tls_example;
class simple {
int i;
};
__thread class simple *tls_simple_example;

```

---

### Post by dwhitney67 on 2008-05-04
> **melopsittacus said:**
> 
And I did test the objects, but alas only without synchronization, so I began to get deadlocks when I added the mutexes, that's why I ended up writing Loggers :)
Without seeing your code, it is impossible to comment as to why you were getting deadlocks.  Using mutexes should be straight-forward, and if in doubt on how to implement them, you should consider using the Boost threads library for your needs.

If you want, you can try using the code below which I threw together but have not really tested thoroughly.

Mutex.h:
[PHP]#ifndef MUTEX_H
#define MUTEX_H

#include <pthread.h>

class Mutex
{
  public:
    Mutex();

    ~Mutex();

    void lock();
    void unlock();

  private:
    pthread_mutex_t m_mutex;
};

#endif[/PHP]

Mutex.cpp:
[PHP]#include "Mutex.h"
#include <stdexcept>


Mutex::Mutex()
{
  pthread_mutexattr_t attr;

  if ( pthread_mutexattr_init( &attr ) != 0 )
  {
    throw std::runtime_error( "Mutex::initMutex() -- failed to init attr." );
  }

  if ( pthread_mutexattr_setpshared( &attr, PTHREAD_PROCESS_PRIVATE ) != 0 )
  {
    throw std::runtime_error( "Mutex::initMutex() -- failed to set attr process type." );
  }

  if ( pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_DEFAULT ) != 0 )
  {
    throw std::runtime_error( "Mutex::initMutex() -- failed to set attr type." );
  }

  if ( pthread_mutex_init( &m_mutex, &attr ) != 0 )
  {
    throw std::runtime_error( "Mutex::initMutex() -- failed to init mutex attr." );
  }
}


Mutex::~Mutex()
{
  if ( pthread_mutex_destroy( &m_mutex ) != 0 )
  {
    throw std::runtime_error( "Mutex::~Mutex() -- unable to destroy the mutex." );
  }
}


void
Mutex::lock()
{
  if ( pthread_mutex_lock( &m_mutex ) != 0 )
  {
    throw std::runtime_error( "Mutex::lock() -- unable to lock the mutex." );
  }
}


void
Mutex::unlock()
{
  if ( pthread_mutex_unlock( &m_mutex ) != 0 )
  {
    throw std::runtime_error( "Mutex::unlock() -- unable to unlock the mutex." );
  }
}[/PHP]

ScopedLock.h:
[PHP]#ifndef SCOPED_LOCK_H
#define SCOPED_LOCK_H

#include "Mutex.h"


class ScopedLock
{
  public:
    ScopedLock( Mutex &mutex );

    ~ScopedLock();

  private:
    Mutex &m_mutex;
};

#endif[/PHP]

ScopedLock.cpp:
[PHP]#include "ScopedLock.h"


ScopedLock::ScopedLock( Mutex &mutex )
  : m_mutex( mutex )
{
  m_mutex.lock();
}

ScopedLock::~ScopedLock()
{
  m_mutex.unlock();
}[/PHP]

To use the code above to protect a critical section of a shared object, do something like this within the shared object definition/implementation:
[PHP]#include "Mutex.h"
#include "ScopedLock.h"

class SharedObject
{
  private:
    Mutex m_mutex;
    ...

  public:
    ...
    void function()
    {
      ScopedLock lock( m_mutex );

      // implement critical section
    }
};[/PHP]

---

### Post by melopsittacus on 2008-05-26
Hi Dwhitney67! Thanks for sharing this solution, it is much cleaner than that I had hacked together. Sorry for not replying until now, I did not have time to look at the forum recently :) Now I have tried your code and it seems to me that it works.

---

### Post by dwhitney67 on 2008-05-26
Your welcome!  Just make sure to understand that you should create only one instance of the SharedObject, and then provide a reference of it to each of the threads that plan to use it.  Creating more than one instance of the object defeats the notion of a "shared" object.

P.S.  An alternative is to implement SharedObject as a singleton.  That would guarantee that only one instance exists.

---

