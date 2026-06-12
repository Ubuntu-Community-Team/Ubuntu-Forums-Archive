---
title: "Simple detached thread can not be cancled becaus of cout???"
date: 2010-03-14
forum: Programming Talk
---

### Post by gabyx on 2010-03-14
I have a hard  problem here, which I can not solve and do not find the right answer on the net:
  I have created a detached thread with a clean up routing, the problem is that on my Imac and Ubuntu 9.1 (Dual Core). I am not able to correctly cancel the detached thread in the fallowing code:


```

#include <iostream>
#include <pthread.h>
#include <sched.h>
#include <signal.h>

#include <time.h>

pthread_mutex_t mutex_t;

using namespace std;

static void cleanup(void *arg){
    pthread_mutex_lock(&mutex_t);
    cout << " doing clean up"<<endl;
    pthread_mutex_unlock(&mutex_t);
}


static void *thread(void *aArgument)
{

    pthread_setcancelstate(PTHREAD_CANCEL_ENABLE,NULL);
    pthread_setcanceltype(PTHREAD_CANCEL_DEFERRED,NULL);

    pthread_cleanup_push(&cleanup,NULL);
    int n=0;
    while(1){
        pthread_testcancel();
        sched_yield();
        n++;

        pthread_mutex_lock(&mutex_t);
        cout << " Thread 2: "<< n<<endl; // IF I remove this endl;  --> IT WORKS!!??
        pthread_mutex_unlock(&mutex_t);

    }
    pthread_cleanup_pop(0);

    return NULL;
}


int main()
{

    pthread_t thread_id;

    pthread_attr_t attr;
    pthread_attr_init(&attr);
    pthread_attr_setdetachstate(&attr,PTHREAD_CREATE_DETACHED);

    int error;

    if (pthread_mutex_init(&mutex_t,NULL) != 0) return 1;

    if (pthread_create(&thread_id, &attr, &(thread) , NULL) != 0) return 1;

    pthread_mutex_lock(&mutex_t);
    cout << "waiting 1s for thread...\n" <<endl;
    pthread_mutex_unlock(&mutex_t);

    int n =0;

    while(n<1E3){
        pthread_testcancel();
        sched_yield();
        n++;

        pthread_mutex_lock(&mutex_t);
        cout << " Thread 1: "<< n<<endl;
        pthread_mutex_unlock(&mutex_t);
    }

    pthread_mutex_lock(&mutex_t);
    cout << "canceling thread...\n" <<endl;
    pthread_mutex_unlock(&mutex_t);

    if (pthread_cancel(thread_id) == 0)
    {
        //This doesn't wait for the thread to exit
        pthread_mutex_lock(&mutex_t);
        cout << "detaching thread...\n"<<endl;
        pthread_mutex_unlock(&mutex_t);

        pthread_detach(thread_id);

        while (pthread_kill(thread_id,0)==0)
        {
                sched_yield();
        }

        pthread_mutex_lock(&mutex_t);
        cout << "thread is canceled";
        pthread_mutex_unlock(&mutex_t);

    }

    pthread_mutex_lock(&mutex_t);
    cout << "exit"<<endl;
    pthread_mutex_unlock(&mutex_t);

    return 0;
}



```
When I replace the Cout with printf() i workes to the end "exit" , but with the cout (even locked) the executable hangs after outputting "detaching thread...
  It would be very cool to know from a Pro, what the problem here is?. Why does this not work even when cout is locked by a mutex!?


I am soo confused, and I apprciate every help!!!
Thanks alot!!
Gabriel

---

### Post by MadCow108 on 2010-03-14
a blocking system call is a cancellation point.
Flushing a stream is a blocking system call.
endl flushes the stream (printf without a newline does not)

=> So you have a cancellation point inside a locked section == very bad
if the thread is canceled inside that section it calls the cleanup handler which tries to lock the same mutex => deadlock

---

### Post by dwhitney67 on 2010-03-14
> **MadCow108 said:**
> a blocking system call is a cancellation point.
Flushing a stream is a blocking system call.
endl flushes the stream (printf without a newline does not)

=> So you have a cancellation point inside a locked section == very bad
if the thread is canceled inside that section it calls the cleanup handler which tries to lock the same mutex => deadlock

This sounds very reasonable, but being that I have never played around with detachable threads (but only with those that are join-able), I decided to experiment a bit using the OP's code as a guide.

I came up with this code, but unlike the OP's, it succeeds:
```

#include <string>
#include <sstream>
#include <iostream>
#include <pthread.h>
#include <unistd.h>

template<typename T>
void display(const T& obj)
{
   static bool            firstTime = true;
   static pthread_mutex_t mutex;

   if (firstTime)
   {
      firstTime = false;
      pthread_mutex_init(&mutex, 0);
   }

   pthread_mutex_lock(&mutex);
   std::cout << obj << std::endl;
   pthread_mutex_unlock(&mutex);
}

class Thread
{
public:
   Thread()
      : myRunState(true)
   {
      pthread_attr_init(&myAttr);
      pthread_attr_setdetachstate(&myAttr, PTHREAD_CREATE_DETACHED);
      pthread_create(&myTid, &myAttr, Thread::run, this);
   }

   pthread_t getTID() const { return myTid; }

   bool isRunning() const { return myRunState; }

private:
   static void* run(void* arg)
   {
      pthread_setcancelstate(PTHREAD_CANCEL_ENABLE, 0);
      pthread_setcanceltype(PTHREAD_CANCEL_DEFERRED, 0);
      pthread_cleanup_push(Thread::cleanup, arg);

      while (1)
      {
         pthread_testcancel();

         display<std::string>("Child thread is running");

         sched_yield();
      }

      pthread_cleanup_pop(0);

      return 0;
   }

   static void cleanup(void* arg)
   {
      Thread* t = static_cast<Thread*>(arg);

      t->myRunState = false;

      display<std::string>("Child thread is cleaning up.");
   }

   bool           myRunState;
   pthread_t      myTid;
   pthread_attr_t myAttr;
};

int main()
{
   display<std::string>("This is a test");

   std::stringstream ss;
   Thread            thread;   // start the thread
   unsigned int      iter = 0;

   ss << "Main Thread: child thread is " << (thread.isRunning() ? "running." : "not running.");
   display<std::string>(ss.str());

   while (++iter < 1E3)
   {
      ss.str("");
      ss << "Main Thread: iteration #" << iter;

      display<std::string>(ss.str());

      sched_yield();
   }

   display<std::string>("Canceling child thread...");

   pthread_cancel(thread.getTID());
   sched_yield();

   display<std::string>("All done.");


   ss.str("");
   ss << "Main Thread: child thread is " << (thread.isRunning() ? "running." : "not running.");
   display<std::string>(ss.str());

   return 0;
}

```

---

### Post by MadCow108 on 2010-03-14
you have a race condition in your code.

place the sched_yield before your display instead of after it
this increases the chances that the main thread will run while the child thread is before the flush cancellation point
now main thread may cancel before the flush cancellation point has been passed by the child thread => deadlock

on a single core pc the chance of deadlock is 100%

A solution to the problem (if the lock is necessary) would be to disable cancellation for the locked section and enable it afterwards.
the pthread_cancel request will be queued until the thread cancels.
But beware pthread_cancel is asynchronous, so don't try to kill it directly after the cancel request, but wait till its ended.

---

