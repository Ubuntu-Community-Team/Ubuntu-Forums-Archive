---
title: "Trouble using pthread for a prime# finder"
date: 2008-03-08
forum: Programming Talk
---

### Post by wozzinator on 2008-03-08
I'm writing a prime number checking program just to play around with simulatenous thread processing and i'll get a Seg Fault (core dump) error randomly. I apologize for the indenting. C+P for some reason won't read the tab indentation.

My code is:

> /* Prime Number Checker
 * 3/5/2008
 * A Just-For-Fun program that will implement threads to
 * have core0 check if "i" is prime and core1 will check
 * if "i+2" is prime. */
#include <stdio.h>
#include <time.h>
#include <pthread.h>
#include <stdbool.h>

void *Prime(int x);
bool isPrime(int x);

int main(void)
{
       long int Start = clock();
       int x=1;
       pthread_t pth0=0,pth1=0;

       printf("The prime number check is starting at %d and ending at 2147483647\n", x);

       for (x=1; x > 0; x+=4)
       {
              pthread_create(&pth0, NULL, Prime(x), NULL);
              pthread_create(&pth1, NULL, Prime(x+2), NULL);
       }

       long int Stop = clock();
       long int TotalTime = Stop - Start;

       printf("The time it took to check every number between 1 and 2147483647 was %.2f seconds.\n", (double) TotalTime/1000000);
}

void *Prime(int x)
{
       long int begin = clock();
	
       if (isPrime(x) == true)
       {
              long int end = clock();
              long int TimePerCheck = end - begin;
              printf("%10d is a prime number and the check took %.2f seconds\n", x, (double)TimePerCheck/1000000);
       }

       return NULL;
}

bool isPrime(int x)
{
       for (int i = 2; i < (x/2); i++)
              for (int j = i; j < (x/2); j++)
                     if ((i * j) == x)
                            return false;

       return true;
}

I am compiling with gcc using the flags:

> gcc -std=c99 -lpthread -W -O2 threaded-prime.c

Sample output:

> 
The prime number check is starting at 1 and ending at 2147483647
         1 is a prime number and the check took 0.00 seconds
         3 is a prime number and the check took 0.00 seconds
         5 is a prime number and the check took 0.00 seconds
         7 is a prime number and the check took 0.00 seconds
       ...
       241 is a prime number and the check took 0.00 seconds
       251 is a prime number and the check took 0.00 seconds
       257 is a prime number and the check took 0.00 seconds
Segmentation fault (core dumped)

Sometimes it will get to around 900 other times anywhere between 3 and 500.

I've browsed around for pthreads on the forums and i've gotten from it not compiling to having it get this far, so any help would be appreciated.

---

### Post by [h2o] on 2008-03-08
If I remember pthreads correctly (only used it once) your pthread_create call is wrong.
Right now you are passing it a value while you really should be passing it a function pointer and function arguments.

Thus it should be something like:
pthread_create(&pth0, Prime, (void*) x);
Also, I am quite certain your Prime function must be declared as
void * Prime(void * arg)
and then you will have to typecast your void argument to something meaningful afterwards by lets say int x = (int) arg.

Another thing that strikes me as odd is that you are creating _a lot_ of threads, but you never exit them. Or wait for them to finish. The last one I think might be your error.
I would rewrite the program to use a number of threads but instead of using one thread per number, pass them partitions of the calculation space so that they calculate 10 or more numbers at a time.

---

### Post by wozzinator on 2008-03-08
I tried exiting the pthread like so:
>         for (x=1; x > 0; x+=4)
        {
                pthread_create(&pth0, NULL, Prime(x), NULL);
                pthread_create(&pth1, NULL, Prime(x+2), NULL);
                pthread_exit(&pth0);
                pthread_exit(&pth1);
        }


And it will check 1 and 3 and then immediately core dump. It never gets farther than x=3.

I'll look into the stuff before that, but when I look thru pthread.h I can't find any wait functions.

---

### Post by [h2o] on 2008-03-08
> **wozzinator said:**
> I tried exiting the pthread like so:


And it will check 1 and 3 and then immediately core dump. It never gets farther than x=3.

I'll look into the stuff before that, but when I look thru pthread.h I can't find any wait functions.

I think pthread_exit() should be called from within the thread. The problem is not that the thread is not exited (they exit automatically on function exit) but that you create so many threads.

There are a lot of ways to perform synchronization in pthreads. Instead of looking through the headers I suggest googling for a tutorial/documentation.

---

### Post by wozzinator on 2008-03-08
* deleted *

---

