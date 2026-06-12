---
title: "A good tutorial how to create C++ bindings for C code?"
date: 2012-08-22
forum: Programming Talk
---

### Post by t1497f35 on 2012-08-22
I googled, but basically found nothing.

I'd like to try creating C++ bindings for the [app indicator API]("http://developer.ubuntu.com/resources/technologies/application-indicators/") which is written in C.

---

### Post by ofnuts on 2012-08-22
> **t1497f35 said:**
> I googled, but basically found nothing.

I'd like to try creating C++ bindings for the [app indicator API]("http://developer.ubuntu.com/resources/technologies/application-indicators/") which is written in C.
You mean beyond bracketing the C API declarations with 'extern "C" {}' which is likely already done?

---

### Post by t1497f35 on 2012-08-22
> **ofnuts said:**
> You mean beyond bracketing the C API declarations with 'extern "C" {}' which is likely already done?

I mean like what gtkmm is to gtk, with classes you can extend the C++ way etc, etc.
A very simple example:

```

//PLAIN C CODE
indicator = app_indicator_new("example-simple-client",
        "indicator-messages",
        APP_INDICATOR_CATEGORY_APPLICATION_STATUS);

//PSEUDO TRANSFORMED INTO C++ LIKE CODE
indicator = new AppIndicator("example-simple-client",
        AppIndicator::TYPE_MESSAGES, AppIndicator::CATEGORY_APPLICATION_STATUS);

```

---

### Post by ofnuts on 2012-08-23
For this I don't think a "tutorial" will be enough (assuming there is only one way to do it....). Each API is somehow a special case, some lend themselves better to objectification than others.

Typically all the data you have to keep on your side of the API and have to pass as parameters in API calls  (at least the identifier of the object created) are good candidates to become attributes in your C++ class. 

But the mapping between object methods and API calls depends on your needs; If you want to preserve all the flexibility of the original API you will end up with pretty close to a one-to-one mapping, but if you are really after ease of programing for your own needs you can define a reduced set of your own methods that will call several API functions... In an ideal world you do the complete thing and then subclass for convenience.

---

### Post by dwhitney67 on 2012-08-23
> **t1497f35 said:**
> I googled, but basically found nothing.

I'd like to try creating C++ bindings for the [app indicator API]("http://developer.ubuntu.com/resources/technologies/application-indicators/") which is written in C.

In lieu of the word "bindings", I use the word "wrapper".  As Ofnuts indicated, you should consider wrapping only the functionality that you require, unless of course you are on a mission to offer the world a C++ version of App Indicator.

Here's a simple example (which I haven't compiled) of wrapping the pthread library for threads:
```

#ifndef THREAD_H
#define THREAD_H

#include <pthread.h>


class Thread
{
public:
    enum ThreadType { JOINABLE, DETACHABLE };

    Thread(ThreadType type = JOINABLE);

    void start()
    {
        pthread_create(&tid, 0, helper, this);
    }

    void join()
    {
        pthread_join(tid, 0);
    }

protected:
    virtual void run() = 0;

private:
    static void* helper(void* arg)
    {
        Thread* t = static_cast<Thread*>(arg);
        t->run();

        if (t->type == DETACHABLE)
        {
            pthread_exit(0);
        }

        return 0;
    }

    ThreadType type;
    pthread_t  tid;
};

#endif

```
In application code:
```

#include "Thread.h"

class MyThread : public Thread
{
public:
    MyThread(int iters) : myIters(iters) {}

protected:
    void run()
    {
        for (int i = 0; i < myIters; ++i)
        {
            // do something
        }
    }

private:
    int myIters;
};

int main()
{
    MyThread thrd(10);

    thrd.start();

    thrd.join();
}

```


P.S.  Here's another example, slightly more advanced, wrapping the thread library.  Here I tried to model the boost library's thread class (for Linux only).
```

/*
# Copyright (C) 2008 David M. Whitney (aka "dwhitney67")
#
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
#this program. If not, see <http://www.gnu.org/licenses/>.
*/

#ifndef LITE_BOOST_THREAD_H
#define LITE_BOOST_THREAD_H

#include <liteboost/function.hpp>
#include <pthread.h>
#include <stdexcept>
#include <vector>


namespace liteboost
{

class thread
{
  public:
    template< typename F >
    thread(F& functor, const int policy = SCHED_OTHER)
      : m_functor(new function0<F>(functor)),
        m_attr(new pthread_attr_t),
        m_policy(policy)
    {
    }

    virtual ~thread()
    {
      delete m_functor;
      delete m_attr;
    }

    void run()
    {
      if (m_policy != SCHED_OTHER && getuid() != 0)
      {
        throw std::runtime_error("Warning:  You are only privileged to setup scheduling"
                                 " for SCHED_OTHER.");
      }

      if (pthread_attr_setschedpolicy(m_attr, m_policy) != 0)
      {
        throw std::runtime_error("Error: Failed to set scheduling for thread.");
      }

      if (pthread_create(&m_tid, m_attr, thread::helper, this) != 0)
      {
        throw std::runtime_error("Error: Failed to start thread.");
      }
    }

    pthread_t get_thread_id() const
    {
      return m_tid;
    }

  private:
    static void* helper(void* arg)
    {
      thread* t = static_cast<thread*>(arg);

      (t->m_functor)->operator()();

      int status = 0;

      pthread_exit((void*) status);

      return NULL;
    }

    // Member Data
    function_base*  m_functor;
    pthread_t       m_tid;
    pthread_attr_t* m_attr;
    int             m_policy;
};


class thread_group
{
  private:
    typedef std::vector<thread*> Group;

  public:
    thread_group() {}

    ~thread_group()
    {
      for (Group::iterator it = m_group.begin(); it != m_group.end(); ++it)
      {
        delete *it;
      }
    }

    void add_thread(thread* thread)
    {
      m_group.push_back(thread);
    }

    void join_all()
    {
      for (Group::iterator it = m_group.begin(); it != m_group.end(); ++it)
      {
        static_cast<thread*>(*it)->run();
      }
      for (Group::iterator it = m_group.begin(); it != m_group.end(); ++it)
      {
        int *status = 0;
        pthread_join(static_cast<thread*>(*it)->get_thread_id(), (void**)&status);
      }
    }

  private:
    Group m_group;
};

}  // end namespace

#endif

```

---

### Post by t1497f35 on 2012-08-23
Thanks to all,
apparently it's too much of a learning curve and work so I should just call the C API from my gtkmm (C++) app directly and forget about the fancy stuff that a C++ binding/wrapper would give.
So I tried and it seems to work: the direct C calls from my C++ app work fine (so far), though I feel a bit weird :)

---

### Post by durdenstationer on 2012-08-23
> **t1497f35 said:**
> So I tried and it seems to work: the direct C calls from my C++ app work fine (so far), though I feel a bit weird :)

Of course it works, why wouldn't it? One if the fundamental design goals of C++ was the fact that you can easily call into C code. Also, what is weird about? Using C++ does not imply using OOP in every single place. C++ is not a purist langauge of any sort and is multiparadigm for a reason.

---

### Post by t1497f35 on 2012-08-23
> **durdenstationer said:**
> Of course it works, why wouldn't it? One if the fundamental design goals of C++ was the fact that you can easily call into C code. Also, what is weird about? Using C++ does not imply using OOP in every single place. C++ is not a purist langauge of any sort and is multiparadigm for a reason.
Before this I was a Java guy, so that explains it, i.e. I really dislike this style:
gtk_window_set_title(GTK_WINDOW(window), "title");
in favor of common sense like this:
window->set_title("title");

another example: extending a class in C++ is a cake, in C you have to put a bunch of weird code.

so it's not just about calling c from c++, but the fact that I now have to use a little of this grotesque, lower level, verbose C API, while not gaining anything (not even speed). Not a rant, just explaining.

---

