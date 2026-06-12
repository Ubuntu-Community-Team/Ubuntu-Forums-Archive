---
title: "C++ Allowing Command Line Input"
date: 2009-05-16
forum: Programming Talk
---

### Post by terets on 2009-05-16
I am writing a C++ command line program that will do financial market programmed trading constantly until the user quits the program.  Due to the nature of the program, I want it to have no delay in retrieving information from the market data server.  So I want it to constantly do this until the user presses 'q' for quit or something like that.

How can I have a command line program accept input even while it is constantly running?  I guess I would need the program to periodically check the input stream to see if there is any input waiting and, if so, act based on that input.  How can I do that?  Or if that is not the right solution, what is the right solution?

---

### Post by dwhitney67 on 2009-05-16
Since it appears that you want to perform concurrent operations within a single application, consider using threads.

You can either define your threads using the pthread library, or you can use Boost threads (thus making the application more portable).

If you go with the threading approach, you undoubtedly will need something (a data container or something similar) to convey information from one thread to another.  Writing and reading from this data container will need to be thread-safe, to avoid concurrent access.  For this, you can use a mutex to safe-guard critical sections of the code.

Here's something I threw together using the pthread library functions; it would much easier if done with Boost.
```

#include <pthread.h>
#include <iostream>
#include <unistd.h>
#include <sys/types.h>
#include <cstdio>

class Data
{
public:
  Data() {
    pthread_mutexattr_t attr;
    pthread_mutex_init(&m_mutex, &attr);
  }

  ~Data() {
    pthread_mutex_destroy(&m_mutex);
  }

  bool doContinue() {
    bool c = true;
    pthread_mutex_lock(&m_mutex);
    c = m_continue;
    pthread_mutex_unlock(&m_mutex);
    return c;
  }

  void doContinue(bool cont) {
    pthread_mutex_lock(&m_mutex);
    m_continue = cont;
    pthread_mutex_unlock(&m_mutex);
  }

private:
  bool            m_continue;
  pthread_mutex_t m_mutex;
};

class Thread
{
public:
  void start() {
    pthread_create(&m_tid, 0, helper, this);
  }

protected:
  Thread() {}
  virtual ~Thread() {}

  pthread_t m_tid;

private:
  virtual void run() = 0;

  static void* helper(void* arg) {
    Thread* t = static_cast<Thread*>(arg);
    t->run();
    pthread_exit(0);
    return 0;
  }
};

class InputHandler : public Thread
{
public:
  InputHandler(Data& data) : m_data(data) {}

  virtual ~InputHandler() {}

  void waitTillDone() {
    pthread_join(m_tid, 0);
  }

private:
  void run() {
    std::cout << "InputHandler is running." << std::endl;  // this is not thread-safe!

    while (m_data.doContinue()) {
      fd_set readfds;
      FD_ZERO(&readfds);
      FD_SET(fileno(stdin), &readfds);

      int sel = select(fileno(stdin) + 1, &readfds, 0, 0, 0);

      if (sel > 0 && FD_ISSET(fileno(stdin), &readfds)) {
        char buf[80] = {0};

        fgets(buf, sizeof(buf), stdin);

        if (buf[0] == 'q' && buf[1] == '\n') {
          m_data.doContinue(false);
        }
      }
    }
    std::cout << "InputHandler is done." << std::endl;  // this is not thread-safe!
  }

  Data& m_data;
};

class DoSomething : public Thread
{
public:
  DoSomething(Data& data) : m_data(data) {}

  virtual ~DoSomething() {}

private:
  void run() {
    std::cout << "DoSomething is running." << std::endl;  // this is not thread-safe!

    while (m_data.doContinue()) {
      usleep(10000);
    }
    std::cout << "DoSomething is done." << std::endl;  // this is not thread-safe!
  }

  Data& m_data;
};


int main()
{
  Data         data;
  DoSomething  ds(data);
  InputHandler ih(data);

  ds.start();   // you may want to consider starting this after ih?
  ih.start();

  // never let the main thread exit until the other threads are done.
  ih.waitTillDone();
  usleep(10000);
  std::cout << "all done." << std::endl;
}

```

To build/test:
```

g++ financial.cpp -lpthread -o financial
./financial

```
Type a 'q' (plus enter key) to terminate the app.

---

### Post by weresheep on 2009-05-16
Hello,

On linux there is a system call called poll()* that allows you to wait for activity on a file descriptor. Standard input happens to be a file descriptor so it is possible to use poll() to wait for data to be available on it. You can specify a timeout value to poll such that it doesn't 'wait' but just checks to see if there is anything to be read at that moment.

This means it is possible to have a loop in your program that continually checks standard input for activity. So in (very) pseudo code...

```

loop (FOREVER)
    if (poll(stdin, NO_WAIT) == ACTIVITY)
        if (read(stdin) == 'q')
            break
        endif
    endif

    // do one iteration of main work here
endloop

```

The poll (and similar) system calls are quite complex though and it may be there are libraries that would allow you to do something similar more easily. It would probably be worth checking out the ncurses library as a starting point.

Hope that helps.

-weresheep

* there are also the select() and epoll() system calls that do similar things

---

### Post by terets on 2009-05-17
Thanks guys for the answers.  I knew about threads, but was hoping I would not have to deal with those as I am not that good of a programmer and every time I have looked at threads I have gotten a headache!  I have heard of boost and know of it's advantages, so will probably use that.  As for the other solution presented, I have never heard of that but will look into it.  It is good to have a few possible solutions, that way I can pick the one that is best for my needs.  Thanks again guys for all the help!

---

