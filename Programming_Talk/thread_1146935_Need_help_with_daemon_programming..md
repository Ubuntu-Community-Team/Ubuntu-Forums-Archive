---
title: "Need help with daemon programming."
date: 2009-05-03
forum: Programming Talk
---

### Post by Jiraiya_sama on 2009-05-03
I'm learning to program daemons, and everywhere I read says to use exit() when I encounter sigterm. However, this is not a clean way to close in c++. If I have allocated data in a class, the destructor is not called when the program exits. 

```

#include <unistd.h>
#include <signal.h>
#include <iostream>
#include <cstdlib>
#include "LinkedList.h"

using namespace std;

bool term = false;

void termHandle(int signal)
{
  cout << "term encountered." << endl;
  term = true;
}



int main()
{
  LinkedList<int> a;

  a.addItem(5);

  signal(SIGTERM, termHandle);

  int i = fork();
  if (i>0) 
    return 0;

  while(!term)
    ;

  return 0;
}

```

This is my very temporary solution. Problem is it relies on a global variable. Certainly there is a cleaner way to handle this than a global variable. Can anyone help?

---

### Post by Jiraiya_sama on 2009-05-03
Today I was thinking about using try/catch and throw to end the program cleanly. Is anyone here familiar with this though?

---

### Post by dwhitney67 on 2009-05-03
The way you have implemented your signal handler is one possible way of doing things; the other is to encapsulate the signal handler and the data it operates on within a class.  When performing the latter, the signal hander and the data must be declared static.

With respect to your application, it seems organized quite well.  You catch the signal, set a flag, and then terminate.  The destructor for the LinkedList object should be called.  It is up to you to properly implement that destructor to clean up any resources you may have allocated.

Back to defining the signal handler within a class; here's a crude example.
```

class MyApp
{
  public:
    MyApp()
    {
      signal(SIGTERM, MyApp::sighandler);
    }

    void start()
    {
      while (!appDone)
      {
      }
    }

  private:
    static void sighandler(int signo)
    {
      appDone = true;
    }

    static bool appDone;
};

...

bool MyApp::appDone = false;


int main()
{
  MyApp ma;
  ma.start();
}

```

P.S.  Upon re-examining the code you posted, I cannot quite figure out why you felt it necessary to call fork().

---

### Post by Jiraiya_sama on 2009-05-03
> **dwhitney67 said:**
> The way you have implemented your signal handler is one possible way of doing things; the other is to encapsulate the signal handler and the data it operates on within a class.  When performing the latter, the signal hander and the data must be declared static.

With respect to your application, it seems organized quite well.  You catch the signal, set a flag, and then terminate.  The destructor for the LinkedList object should be called.  It is up to you to properly implement that destructor to clean up any resources you may have allocated.

Back to defining the signal handler within a class; here's a crude example.
```

class MyApp
{
  public:
    MyApp()
    {
      signal(SIGTERM, MyApp::sighandler);
    }

    void start()
    {
      while (!appDone)
      {
      }
    }

  private:
    static void sighandler(int signo)
    {
      appDone = true;
    }

    static bool appDone;
};

...

bool MyApp::appDone = false;


int main()
{
  MyApp ma;
  ma.start();
}

```

P.S.  Upon re-examining the code you posted, I cannot quite figure out why you felt it necessary to call fork().


To spawn a child process that is independent of the shell or session that spawned it. Your idea looks good though, I'll work on it when I get home from work.

---

### Post by dwhitney67 on 2009-05-03
> **Jiraiya_sama said:**
> To spawn a child process that is independent of the shell or session that spawned it.

Right, I guess that's a requisite when creating a daemon.  :lolflag:

Here's some modified code:
```

#include <csignal>
#include <unistd.h>
#include <iostream>

class MyApp
{
  public:
    MyApp()
    {
      signal(SIGTERM, MyApp::sighandler);
    }

    void start()
    {
      // do something here (or within the loop)

      while (!appDone)
      {
        usleep(1000);
      }
      std::cout << "app is done!" << std::endl;
    }

  private:
    static void sighandler(int signo)
    {
      appDone = true;
    }

    static bool appDone;
};

bool MyApp::appDone = false;


int main()
{
  int pid = 0;

  if ((pid = fork()) == 0)
  {
    MyApp ma;
    ma.start();
  }
  else
  {
    std::cout << "daemon launched with PID = " << pid << std::endl;
  }
}

```

---

### Post by slavik on 2009-05-04
man atexit ... or make your own?

---

### Post by Jiraiya_sama on 2009-05-04
> **slavik said:**
> man atexit ... or make your own?

Thanks, that's very useful. However it seems to be much more suited for C than C++. DWhitney's idea of wrapping the loop in a class seems cleaner, since then I can have the compiler take care of garbage collection.

I will remember that when I start developing in C though.

---

