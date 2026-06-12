---
title: "unexpected behavior of pthread mutexes"
date: 2009-02-09
forum: Programming Talk
---

### Post by YDre on 2009-02-09
Hi guys,
I'm trying to write a thread safe framework in C++ using the POSIX 4 API. The behavior of the mutex seems really odd, mainly with the functions pthread_mutex_trylock () and pthread_mutex_timedlock (). 

I'm using anjuta 2.4.1 over ubuntu 8.4.

In order to focus on the problem, I wrote the following test program :

[FONT="Times New Roman"]
#define _POSIX_C_SOURCE 200112L
#define _XOPEN_SOURCE 600

#include <iostream>
#include <pthread.h>
#include <time.h>
#include <errno.h>

using namespace std;

int main()
{
	pthread_mutex_t d_sem;
	struct timespec trav;
	trav.tv_sec= 10;
	trav.tv_nsec=0;
	
	std::cout << "Test pthread mutex :" << std::endl;
	if (pthread_mutex_init (&d_sem, 0) != 0)
	{
		std::cout << "Error initialising mutex\n";
		exit (1);
	}
	cout << "EBUSY=" << EBUSY << "\nETIMEDOUT=" << ETIMEDOUT << "\nEDEADLK=" << EDEADLK << "\n";
	cout << "\nLock : " << pthread_mutex_lock(&d_sem);
	cout << "\nUnlock : " << pthread_mutex_unlock(&d_sem);
	cout << "\ntrylock : " << pthread_mutex_trylock(&d_sem) << "\n2nd trylock : " << pthread_mutex_trylock(&d_sem);
	cout << "\n3rd trylock : " << pthread_mutex_trylock(&d_sem) << "\n4th trylock : " << pthread_mutex_trylock(&d_sem);
	cout << "\nUnlock : " << pthread_mutex_unlock(&d_sem);
	cout << "\nLock : " << pthread_mutex_lock(&d_sem);
	cout << "\nLock (10s) : " << pthread_mutex_timedlock(&d_sem, &trav);
	cout << "\n";
	cout << "\nUnlock : " << pthread_mutex_unlock(&d_sem);
	pthread_mutex_destroy (&d_sem);
	return 0;
}
[/FONT]

The result is :

time ./test
Test pthread mutex :
EBUSY=16
ETIMEDOUT=110
EDEADLK=35

Lock : 0
Unlock : 0
trylock : 16
2nd trylock : 0
3rd trylock : 16
4th trylock : 16
Unlock : 0
Lock : 0
Lock (10s) : 110

Unlock : 0
real	0m0.003s
user	0m0.000s
sys	0m0.004s

The problems are : 
- how comes the first call to trylock () returns EBUSY and the second OK ?
- how the timedlock could return with ETIMEDOUT (normal) but in less time than the time out ?

I use the linking flag -lpthread.
I'm interested in any hint on what I'm doing wrong ...
Thanks in advance 
YDre

---

### Post by stroyan on 2009-02-09
The key to the trylock results is not mutex behavior, but the iostream behavior.  The expressions are not evaluated from left to right.  The example below shows the same effect with addition.
```

#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    int i = 1;
    cout << "inc : " << i++ << "\ninc : " << i++ << endl;
    return 0;
}

```
reports
inc : 2
inc : 1

The ETIMEDOUT instead of EDEADLK error is probably a result of initializing with '0'.  That has a default mutex kind of PTHREAD_MUTEX_FAST_NP.  I expect you would get EDEADLK if you initialized with a mutex kind of PTHREAD_MUTEX_ERRORCHECK_NP.

---

### Post by YDre on 2009-02-10
Thanks a lot Stroyan,
I searched in an entirely wrong direction...

---

