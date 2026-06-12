---
title: "Problems with POSIX semaphores."
date: 2007-06-23
forum: Programming Talk
---

### Post by volanin on 2007-06-23
Hello guys.
I am having a hard time with the behaviour of POSIX semaphores.
Please, take a look at the following code: (Error checking omitted for the sake of simplicity.)

```
#include <fcntl.h>
#include <stdio.h>
#include <stdlib.h>
#include <semaphore.h>


int main( void )
{
  sem_t *sem;

  sem = sem_open( "/MySemaphore", O_CREAT, 0666, 1 );
  for(;;)
  {
    sem_wait( sem );
    printf( "Semaphore locked!\n" );
    sleep( 5 );

    sem_post( sem );
    printf( "Semaphore unlocked!\n\n" );
    sleep( 1 );
  }

  return 0;
}
```

As you can see, this code creates a POSIX named semaphore (or connects to one if the semaphore has already been created by another process), and start to continuously lock it for 5 seconds, and then unlock it. The desired effect is that two or three instances of this program running concurrently will alternate the lock.

The problem is:
If one instance of the program dies (or is explicitly killed) while it has the lock, IT DOES NOT UNDO THE LOCK, and the other program instances will wait for the lock forever. This effectvely makes the semaphore useless, since it is locked forever and any new instances of the program will already start deadlocked. This behaviour does not happen with System V semaphores, which undo the lock automatically. Is this a limitation of POSIX semaphores, or am I doing something wrong?

Hope you can help, this has been bugging me for days.
Thank you a lot.

*(To compile this you have to link against libpthread: 'gcc code.c -lpthread')*

---

### Post by KaeseEs on 2007-06-23
It's generally good practice to release all resources explicitly when your program either dies or is killed.  As such, you want to release your semaphore after the end of your for loop.  Additionally, I would strongly suggest adding in a signal handler for SIGHUP and SIGTERM which unlocks the semaphore.

Finally, I realize that this is just test code and nothing like production, but you really want to get into the habit of checking the return values of system calls and library functions - anything that could conceivably fail.    For example:
```

const int LEN = 100;
int *array;

//BAD
array = malloc(LEN * sizeof(int) );

//GOOD
if( (array = malloc(LEN*sizeof(int)) == NULL){
        perror("malloc");
        exit(EXIT_FAILURE);
}
```

*see man 3 perror for perror() usage



If you've got more questions, I'll be glad to (try and) help.

---

### Post by volanin on 2007-06-23
Thank you for your concerns KaeseES.

> It's generally good practice to release all resources explicitly when your program either dies or is killed.  As such, you want to release your semaphore after the end of your for loop.

This for loop is infinite.


> Additionally, I would strongly suggest adding in a signal handler for SIGHUP and SIGTERM which unlocks the semaphore.

Even though, I can't trap SIGKILL.
So the semaphore won't be unlocked in the situations I described (Program dies/Explicit kill).
System V semaphores will automatically unlock even in these situations.


> Finally, I realize that this is just test code and nothing like production, but you really want to get into the habit of checking the return values of system calls and library functions - anything that could conceivably fail.

This is indeed VERY good practice.
My code is just a sample, and as I warned, I preferred to keep it simple!

Again,
Thank you a lot.

---

### Post by KaeseEs on 2007-06-23
Well, signal handlers for SIGHUP and SIGTERM will cover the common cases of Ctrl-C and kill <yourpid>, but you're correct that you're kind of SOL when it comes to SIGKILL.  My best guess would be to recheck the Pthreads semaphore documentation; there may well be a function or bit to set an auto-unlock option.  Good luck!

---

### Post by vbdave78 on 2008-10-30
Hello,

I am trying to compile a program with semaphores using pthreads. 
The program is supposed to solve the producer consumer problem. 

The following code is my code my header file 

/* Buffer.h */
typedef int buffer_item;
#define BUFFER_SIZE 5

My main program looks like this

#include "buffer.h"
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <semaphore.h>

buffer_item buffer[BUFFER_SIZE];

sem_t full;
sem_t empty;
pthread_mutex_t mutex;
int simpson = 0;

sem_init(&full,0,0);
sem_init(&empty,0,BUFFER_SIZE);
pthread_mutex_init(&mutex, NULL);

int insert_item(buffer_item item);
int remove_item(buffer_item *item);
void *producer(void *param);
void *consumer(void *param);

int main()
{
	int sleepTime = 0;
	int numProd = 0;
	int numCons = 0;
	pthread_t tid;

	printf("How long to sleep before terminating? ");
	scanf("%d",sleepTime);
	printf("How many producer threads? ");
	scanf("%d",numProd);
	printf("How many consumer threads? ");
	scanf("%d",numCons);
	
	int i = 0;
	for(i=0;i<numProd;i++)
	{
		pthread_create(&tid,NULL,producer,NULL);
		pthread_join(tid,NULL);
	}
	for(i=0;i<numCons;i++)
	{
		pthread_create(&tid,NULL,consumer,NULL);
		pthread_join(tid,NULL);
	}
	sleep(sleepTime);
	exit(1);
}

int insert_item(buffer_item item)
{
	buffer[simpson] = item;
	simpson++;
	return 0;
}
int remove_item(buffer_item *item)
{
	*item = buffer[simpson];
	buffer[simpson] = 0;
	simpson--;
	return 0;
}
void *producer(void *param)
{
	buffer_item item;
	while(1)
	{
		P(empty);
		P(mutex);
		item = rand();
		insert_item(item);
		V(mutex);
		V(full);
	}
}
void *consumer(void *param)
{
	buffer_item item;
	while(1)
	{
		P(full);
		P(mutex);
		remove_item(&item);
		V(mutex);
		V(empty);
	}
}


When i try to compile using the -lpthread and -lrt option, I get the following error

error: expected declaration specifiers or '...' before '&' token for the three lines where I have initialized the semaphore. Any help will be appreciated. Thanks

---

