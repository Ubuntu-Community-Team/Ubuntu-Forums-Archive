---
title: "pthreads and c++"
date: 2008-08-18
forum: Programming Talk
---

### Post by serjM on 2008-08-18
Hy, I have a simple C++ program:
```

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>
#include <iostream.h>

void *print_message_function1( void *ptr );
void *print_message_function2( void *ptr );

int main()
{
     pthread_t thread1, thread2;
     char *message1 = "Thread 1";
     char *message2 = "Thread 2";
     int  iret1, iret2;

     pthread_attr_t attr;
     pthread_attr_init(&attr);
     pthread_attr_setdetachstate(&attr, PTHREAD_CREATE_DETACHED);

     iret1 = pthread_create( &thread1, &attr, print_message_function1, (void*) message1);
     iret2 = pthread_create( &thread2, &attr, print_message_function2, (void*) message2);

     pthread_attr_destroy(&attr);
     return 0;
}

void *print_message_function1( void *ptr )
{
     char *message;
     message = (char *) ptr;
     sched_yield();
     for(int i=0;i<100;i++)
    	 cout << i << endl << flush;
     pthread_exit((void *) 0);
}

void *print_message_function2( void *ptr )
{
     char *message;
     message = (char *) ptr;
     for(int i=0;i<100;i++)
    	 cout << i << endl << flush;
     pthread_exit((void *) 0);
}

```

My threads are running as two functions, their output is not mixing.
Instead of  (for example) 0 1 2 0 3 1 2 3 the program outputs 0 1 2 3 0 1 2 3.

How I can make them to run in the same time, I must change something in the scheduling method?

---

### Post by Zugzwang on 2008-08-18
The threads you are creating simply run too short, much shorter than the typical pre-emption time of the operating system scheduler. Add some "sleep" directive to the loops in your threads, for example, to see the difference.

Also note that access to the "std::cout" object might have to be synchronized.

---

### Post by dwhitney67 on 2008-08-18
Along with the suggestions from **Zugzwang**, you also need to ensure that your main-thread (i.e. the main function) does not terminate until *after* your threads have finished.

Concerning the synchronization of the cout-stream, here's one way to do it:
[PHP]#include <pthread>

pthread_mutex_t coutMutex;

void initMutex();
void outputString(const char *str);
...

int main()
{
  initMutex();
  ...
}

void initMutex()
{
  pthread_mutexattr_t attr;

  pthread_mutexattr_init(&attr);
  pthread_mutexattr_setpshared(&attr, PTHREAD_PROCESS_PRIVATE);
  pthread_mutexattr_settype(&attr, PTHREAD_MUTEX_DEFAULT);
  pthread_mutex_init(&coutMutex, &attr);
}

void outputString(const char *str)
{
  pthread_mutex_lock(&coutMutex);
  std::cout << str << std::endl << std::flush;
  pthread_mutex_unlock(&coutMutex);
}

void *print_message_function1(void *ptr)
{
  ...
  for (int i = 0; i < 100; ++i)
  {
    outputMessage(message);
    //delay here
  }
  ...
  return NULL;
}[/PHP]

---

### Post by dribeas on 2008-08-18
Good, just a small remark: in C++ the standard states that output of endl implies a buffer flush, so there is no need to flush the stream right after:
```

  27.6.2.7 Standard basic_ostream manipulators                      [lib.ostream.manip]
       namespace std {
          template <class charT, class traits>
            basic_ostream<charT,traits>& endl(basic_ostream<charT,traits>& os);
       }
  Effects: 
1 Calls os.put(os.widen(’\n’) ), then os.flush().
2 Returns: os. [300]

[300]     The effect of executing cout << endl is to insert a newline character in the output sequence controlled by cout, then synchronize it with any external file with which it might be associated.

```

---

### Post by dribeas on 2008-08-18
Good, just a small remark: in C++ the standard states that output of endl implies a buffer flush, so there is no need to flush the stream right after:
```

  27.6.2.7 Standard basic_ostream manipulators                      [lib.ostream.manip]
       namespace std {
          template <class charT, class traits>
            basic_ostream<charT,traits>& endl(basic_ostream<charT,traits>& os);
       }
  Effects: 
1 Calls os.put(os.widen(’\n’) ), then os.flush().
2 Returns: os. [300]

[300]     The effect of executing cout << endl is to insert a newline character in the output sequence controlled by cout, then synchronize it with any external file with which it might be associated.

```

---

### Post by serjM on 2008-08-19
> 
I have one more question.. if I am using...
```

pthread_join( thread1, NULL);
pthread_join( thread2, NULL);

```
...the main thread should wait for thread1 and thread 2 to complete, but it doesn't...

UPDATE: my threads where created as PTHREAD_CREATE_DETACHED, so I must make them PTHREAD_CREATE_JOINABLE if I want to join them :)


Thanks guys all your comments where useful, I worked only with C# threads before and there the difference can be seen for 200 loops, a short delay solved my problem this time.

---

