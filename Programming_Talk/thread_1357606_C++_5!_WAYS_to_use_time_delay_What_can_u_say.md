---
title: "C++ 5! WAYS to use time delay: What can u say?"
date: 2009-12-17
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-17
**1 way:** using _*nanosleep*_

```

#include <iostream> 
 
using namespace std; 
 
int msleep(unsigned long milisec)   
{   
    struct timespec req={0};   
    time_t sec=(int)(milisec/1000);   
    milisec=milisec-(sec*1000);   
    req.tv_sec=sec;   
    req.tv_nsec=milisec*1000000L;   
    while(nanosleep(&req,&req)==-1)   
        continue;   
    return 1;   
}   
 
int main() 
{ 
    cout << "Testing nanosleep: waiting 5 secs\n"; 
    msleep(5000); 
    cout << "That is it"; 
} 

```**2 way:** using _*usleep:*_

```

#include <iostream> 
#include <time.h>  
 
using namespace std; 
 
void Sleep(float s) 
{ 
    int sec = int(s*1000000); 
    usleep(sec); 
} 
 
int main () 
{ 
    cout << "Waiting 5 secs\n"; 
    Sleep(5); 
    printf ("FIRE!!!\n"); 
  return 0; 
}

```**3 way:** using _*CLOCKS_PER_SEC**:*_

```

#include <iostream> 
#include <time.h>  
 
void wait ( int seconds ) 
{ 
  clock_t endwait; 
  endwait = clock () + seconds * CLOCKS_PER_SEC ; 
  while (clock() < endwait) {} 
} 
 
int main () 
{ 
  int n; 
  printf ("Starting countdown...\n"); 
  for (n=10; n>0; n--) 
  { 
    printf ("%d\n",n); 
    wait (1); 
  } 
  printf ("FIRE!!!\n"); 
  return 0; 
}

```**4 way:** using _*sleep**:*_

```

#include <iostream> 
#include <time.h> 
 
using namespace std; 
 
int main() 
{ 
    cout << "SomeAction\n"; 
    cout << endl; 
    sleep(1);                // seconds 
    cout << "NextAction\n"; 
    return 0; 
}

```**5 way:** using _*sleep**:*_

```

#include <iostream> 
#include <time.h> 
 
using namespace std; 
 
int main() 
{ 
    cout << "SomeAction\n"; 
    cout.flush(); 
    sleep(1);                // seconds 
    cout << "NextAction\n"; 
    return 0; 
}

```The question: Can someone say, which is (the most accurate)?

---

### Post by dwhitney67 on 2009-12-17
Wow... you really are into delays.  One very infrequently ever uses delays in an application.

Anyhow, to answer your question, I'm sure all are equally good delays, however each is interruptable by a signal.  nanosleep(), if used properly, offers the best if you truly want to sleep for the specified delay.

Also, look into select().

---

### Post by benj1 on 2009-12-17
whats the difference between 4 and 5, is it a fiendish hack where flushing stdout makes sleep more accurate?

---

### Post by Can+~ on 2009-12-17
And why specifically do you want to create a delay?

I'm usually more inclined with the event-driven system, in which case, if you're waiting for a resource/action, you append the process to a wait queue and be signaled when the resource is available/action can be performed. (This is how Monitors handle threads)

---

### Post by dribeas on 2009-12-17
They are not really equivalent, and there might be a penalty there. In cases 4 and 5, the only difference is wheter you write a newline and then flush or just flush the stream. Those are the same from the 'waiting' point of view.

Option 3 is an active wait, and as such you are hogging the cpu and spending processing cycles in just waiting.

The different sleep options leave a chance for the system to interrupt your process and let other processes perform some work (and you will be saving electricity as well). Note that the sleep family of functions will wait for a given period of time. And as the period gets shorter you will be spending more CPU in just calling the OS. Also note that if the result is -1 then it means that it was interrupted, and that if you request a further sleep, the complete process will take more than you expected (say you request 2s sleep in method 1, and you get interrupted after 1s, you are calling the same nanosleep again, so you will actually wait for 3 complete seconds there). In the other two versions you are ignoring the result (which could also be a potential problem with precision).

You could also consider other options, like using the operating system alarm() method and SIGALRM signal that are 'guaranteed' to happen at a given time. But then again I would use a higher level library for all those purposes (unless, of course, what you want is learning the low level constructs)

---

### Post by jpkotta on 2009-12-18
sleep() or usleep() if they are sufficient; nanosleep() if you need it (e.g. you need SIGALRM).  Busy waiting is almost *never* the correct solution.

You ask about "the most [accurate]("http://en.wikipedia.org/wiki/Accuracy")".  In that case you should use a timer, e.g. something that waits (and during the wait is sleeping) until a future absolute time has passed.  You can't expect something like repeatedly calling sleep() not to drift.  This is something I use in Python occasionally:

```

from time import sleep, time as gettimeofday

delta = 1e-3
delay = 3
stop_time = gettimeofday() + delay
while gettimeofday() < stop_time:
    sleep(delta)

```

gettimeofday() is available in C (but it's a bit harder to use there).  C.f. clock_nanosleep().  If you want accuracy, you need to get the system time and compare against that.

---

### Post by nvteighen on 2009-12-18
5! = 120 :p

Ugh... Never knew there were so many delays. Nice to know.

---

