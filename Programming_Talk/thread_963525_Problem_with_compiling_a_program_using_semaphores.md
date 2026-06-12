---
title: "Problem with compiling a program using semaphores"
date: 2008-10-30
forum: Programming Talk
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

### Post by dribeas on 2008-10-30
> **vbdave78 said:**
> ```

buffer_item buffer[BUFFER_SIZE];

sem_t full;
sem_t empty;
pthread_mutex_t mutex;
int simpson = 0;

[color=red]sem_init(&full,0,0);
sem_init(&empty,0,BUFFER_SIZE);
pthread_mutex_init(&mutex, NULL);[/color]

```

You are writing instructions to be executed where they are not allowed. At that point in code only declarations are allowed and the compiler is trying to match your code against (probably) a function declaration. Character & is not part of a valid declaration. 

Move those lines inside the {} in the main function.

---

### Post by vbdave78 on 2008-10-30
Thanks a bunch!!! 
Appreciate it

---

