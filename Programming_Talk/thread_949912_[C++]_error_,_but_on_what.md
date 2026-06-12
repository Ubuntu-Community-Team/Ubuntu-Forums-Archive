---
title: "[C++] error , but on what?"
date: 2008-10-16
forum: Programming Talk
---

### Post by StOoZ on 2008-10-16
check this out : 
[PHP]#ifndef _NTHREAD_HPP
#define	_NTHREAD_HPP
#include<pthread.h>
#include<iostream>
namespace nThread {
    
    //declare thread attributes GLOBALS
    enum {
        JOINABLE,
        DETACHABLE
    };
    
  class Thread {

    private :
        pthread_t thread_handle;
        void *_thread_fun_skelton(void* args);

    public :
        explicit Thread(void);
        virtual short OnInit(void) {}
        void run(void);


  };

    void *Thread::_thread_fun_skelton(void* args) {
        OnInit();
    }

    Thread::Thread() {
        
    }

    void Thread::run() {
        pthread_create(&thread_handle , NULL , _thread_fun_skelton , NULL );
    }

}

#endif	/* _NTHREAD_HPP */


//keep getting this error:
nThread.hpp:43: error: argument of type ‘void* (nThread::Thread::)(void*)’ does not match ‘void* (*)(void*)’
[/PHP]

---

### Post by snova on 2008-10-16
Try this:

[PHP]
#include <pthread.h>
#include <iostream>

namespace nThread
{
    //declare thread attributes GLOBALS
    enum
    {
        JOINABLE,
        DETACHABLE
    };

    class Thread
    {
        private:
            pthread_t thread_handle;
            static void* _thread_fun_skeleton( void* );

        public :
            explicit Thread() {}
            virtual short OnInit() {}
            void run();
    };

    void* Thread::_thread_fun_skeleton( void* tmp )
    {
        ( ( Thread* )tmp )->OnInit();
    }

    void Thread::run()
    {
        pthread_create( &thread_handle, NULL,
                        ( void* (*)(void*) )( &nThread::Thread::_thread_fun_skeleton ),
                        ( void* )this );
    }
}
[/PHP]

It's a bit of a hack, but it works. Or it compiles, anyway.

---

### Post by StOoZ on 2008-10-16
I guess we cant use pointers to member functions.... :(

---

### Post by snova on 2008-10-16
Sorry for any confusion. I edited my post at least three times while testing. First I thought it was possible, then I realized it was impossible, then I found a way to do it.

The reason it doesn't work is that member functions take an invisible first parameter to the class object. So _thread_fun_skelton actually took *two* parameters- which didn't work in conjunction with the pthread library.

The solution is to make it static, so that it doesn't take a parameter- and then give it a parameter anyway. Basically, I faked the "this" pointer.

A little messy, but I'm 99% certain that it will work.

---

### Post by dwhitney67 on 2008-10-17
> **snova said:**
> ...

A little messy, but I'm 99% certain that it will work.

It'll work.  I've done something similar in the past.  I defined a Thread class in which the processing function was a pure-virtual (that had to be implemented by subclasses), however the method used to start the thread was declared static.  The reference to the thread object was passed as the parameter to the static method.

[PHP]class Thread
{
  public:
    Thread( ... );
    void start();
    virtual int run(void) = 0;

  protected:
    // member data (if any)

  private:
    static void* helper(void* arg);
};

void Thread::start()
{
  ...
  pthread_create(&tid, attr, Thread::helper, this);
}

void* Thread::helper(void* arg)
{
  Thread* thread = static_cast<Thread*>(arg);

  const int status = thread->run();

  pthread_exit((void*)status);

  return NULL;
}[/PHP]

Nowadays, I rarely use pthreads when programming in C++.  I rely on the Boost libraries, because they obfuscate all of the complexities that come with the pthread library.  Actually, if I recall, Boost doesn't even use pthread at all; it has its own little way of doing things.

---

