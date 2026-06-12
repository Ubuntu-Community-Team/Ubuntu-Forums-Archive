---
title: "Maximum number of threads accesing global data at the same time"
date: 2011-11-03
forum: Programming Talk
---

### Post by cotzy on 2011-11-03
Hi.
I have this simple linked list with E elements and the following structure 
struct elem {     int value;     int worker;     struct elem* next; };

[FONT=Verdana]I have to create W threads and each one of them has to modify my the values in my list according
to the value of worker. Anyhow, my problem is that maximum 3 threads can access my list at the same
time, and I can't figure it out how could I use mutex and conditional variables to do so.

Any help would be greatly appreciated.

Thanks in advance. Sorry for my poor English.
[/FONT]

---

### Post by karlson on 2011-11-03
> **cotzy said:**
> Hi.
I have this simple linked list with E elements and the following structure 
struct elem {     int value;     int worker;     struct elem* next; };

[FONT=Verdana]I have to create W threads and each one of them has to modify my the values in my list according
to the value of worker. Anyhow, my problem is that maximum 3 threads can access my list at the same
time, and I can't figure it out how could I use mutex and conditional variables to do so.

Any help would be greatly appreciated.

Thanks in advance. Sorry for my poor English.
[/FONT]

Sounds like homework.

What kind of modifications can the threads do?  Add nodes?  Remove nodes? Simply update the values?

---

### Post by cotzy on 2011-11-03
Well, the "working" threads modify the value field by replacing it with the square root of the old value, each thread updates the list according the worker value. I also have another thread that wakes up when exactly 5 elements from the list have the value less than 2 and deletes them, but I know how to implement that.
 The main program stops when my list is empty. All the "worker" threads are also running until the list gets empty, so I can't figure out how to make sure that maximum 3 threads at a time are processing my list.

---

### Post by karlson on 2011-11-03
> **cotzy said:**
> Well, the "working" threads modify the value field by replacing it with the square root of the old value, each thread updates the list according the worker value. I also have another thread that wakes up when exactly 5 elements from the list have the value less than 2 and deletes them, but I know how to implement that.


Got it.

> 
 The main program stops when my list is empty. All the "worker" threads are also running until the list gets empty, so I can't figure out how to make sure that maximum 3 threads at a time are processing my list.

At most 2 threads can access the list at the same time.

Algorithm for the updater threads would be as follows:

Thread 1 has mutex1 and condition variable 1
Thread 2 has mutex2 and condition variable 2.

Threads 1 and 2 obtain locks on their respective mutexes and start going through the list.  They update values in the elements and every time the value < 2 set a condition variable 1 or 2 to notify the list modification thread.

List modification thread simply counts the notifications and if the number of notifications in total > 5 attempts to obtain lock 1 and then lock 2 and then starts going through the list to remove the elements.

---

### Post by MadCow108 on 2011-11-03
a bit context would be good?
why do you need such a complicated, error prone, slow, non-scalable design?
I assume you should go back to the drawing board. Your program will likely be faster and simpler using an sequencial event-based or concurrent task based approach
If you are limiting yourself to three threads anyway, due to the locking it is unlikely to be faster than one thread anyway.
And if the work takes is considerably longer larger than taking a squareroot task distribution and gathering overhead won't hurt either.

---

### Post by cotzy on 2011-11-04
@MadCow108

I know this makes little sense but this is my operating systems homework.


@Karlson

So you're telling me to actually use two functions that do exactly the same thing, and use them to create my threads. For example for half of my threads to use function f1 which would use mutex variable m1 and conditional variable c1 and for the other half to use f2,m2 and c2? I don't know if I should do that, I think I should use only one function, and try some other way to synchronize, maybe semaphores? On the same order of thinking, if it says maximum 3 I guess "exactly one at a time" would be fine, as long as there aren't more than 3 threads accessing my list :).

---

### Post by Jack Brown on 2011-11-04
side note:  Don't you think your prof/instructor might see this thread?

anyway, this is interesting stuff you bring to the table. 

good answers too :popcorn:

---

### Post by gsmanners on 2011-11-04
[This stuff]("http://users.actcom.co.il/~choo/lupg/tutorials/multi-thread/multi-thread.html") is interesting, actually.

---

### Post by cotzy on 2011-11-04
> **gsmanners said:**
> [This stuff]("http://users.actcom.co.il/%7Echoo/lupg/tutorials/multi-thread/multi-thread.html") is interesting, actually.


Yes it is, but unfortunately I still can't figure out how to make sure that maximum 3 threads at a time have access to my list.

---

### Post by karlson on 2011-11-04
> **cotzy said:**
> 
I know this makes little sense but this is my operating systems homework.


You should read the homework rules of this forum for one and 2 have you talked to your Professor or TA about it?

> 
So you're telling me to actually use two functions that do exactly the same thing, and use them to create my threads.

One function by my count.

> 
For example for half of my threads to use function f1 which would use mutex variable m1 and conditional variable c1 and for the other half to use f2,m2 and c2?


Not sure which halves you're talking about but fine.

> I don't know if I should do that, I think I should use only one function, and try some other way to synchronize, maybe semaphores?


Your call here.

> On the same order of thinking, if it says maximum 3 I guess "exactly one at a time" would be fine, as long as there aren't more than 3 threads accessing my list :).

Based on what you described the number of threads that are modifying the data in the nodes can be arbitrary.  The number of threads modifying the list can be 1 at a time.

---

### Post by karlson on 2011-11-04
> **cotzy said:**
> Yes it is, but unfortunately I still can't figure out how to make sure that maximum 3 threads at a time have access to my list.

Simple.  Don't start more then 3

---

### Post by cotzy on 2011-11-04
Right now I'm stuck in with a different problem. I have this code, I want to increase the value of count using thread "f" and if the value of count is 5 I want to signal thread "g". My problem is that this only works if I add the commented line (sleep(1)), otherwise it won't synchronize. 

Here is my code:
```

#include<pthread.h>
#include<stdio.h>

pthread_mutex_t m;
pthread_cond_t c;
int count=1;

void *f(){
    int i;
    for (i=1;i<=10;i++){
        pthread_mutex_lock(&m);
        printf("i=%d\n",i);
        count++;
        if(count==5) pthread_cond_signal(&c);
        pthread_mutex_unlock(&m);
        //sleep(1);
    }
  }


void *g(){
    pthread_mutex_lock(&m);
    pthread_cond_wait(&c,&m);
    printf("Count=5\n");
    pthread_mutex_unlock(&m);
}

void main(){
    pthread_t t1,t2;
    pthread_create(&t1,NULL,g,NULL);
    pthread_create(&t2,NULL,f,NULL);
    pthread_join(t1,NULL);
    pthread_join(t2,NULL);
}
```

---

### Post by karlson on 2011-11-04
> **cotzy said:**
> Right now I'm stuck in with a different problem. I have this code, I want to increase the value of count using thread "f" and if the value of count is 5 I want to signal thread "g". My problem is that this only works if I add the commented line (sleep(1)), otherwise it won't synchronize. 

Here is my code:
```

#include<pthread.h>
#include<stdio.h>

pthread_mutex_t m;
pthread_cond_t c;
int count=1;

void *f(){
    int i;
    for (i=1;i<=10;i++){
        pthread_mutex_lock(&m);
        printf("i=%d\n",i);
        count++;
        if(count==5) pthread_cond_signal(&c);
        pthread_mutex_unlock(&m);
        //sleep(1);
    }
  }


void *g(){
    pthread_mutex_lock(&m);
    pthread_cond_wait(&c,&m);
    printf("Count=5\n");
    pthread_mutex_unlock(&m);
}

void main(){
    pthread_t t1,t2;
    pthread_create(&t1,NULL,g,NULL);
    pthread_create(&t2,NULL,f,NULL);
    pthread_join(t1,NULL);
    pthread_join(t2,NULL);
}
```

Since this is homework you now are on your own.  Suggestions we may be able to do but code no.  I suggest you look at the docs gsmanners posted.

---

