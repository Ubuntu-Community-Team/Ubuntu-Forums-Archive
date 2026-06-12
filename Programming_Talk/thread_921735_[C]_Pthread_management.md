---
title: "[C] Pthread management"
date: 2008-09-16
forum: Programming Talk
---

### Post by British0zzy on 2008-09-16
I'm trying to write a program that will need to process 1000 items, but I only want five threads working at once. Each thread can work on one item. I have a very limited understanding of pthreads, and the only way I can think to implement this is to pthread_join all threads. This means that I have to wait for ALL five threads to finish before assigning five new threads.
Is their a way to check if one thread has finished and assign a new thread?

---

### Post by PC-XT on 2008-09-16
I usually have a syncronized list of items, so that each thread operates on it seperately, and iterate it to load each thread, which, when finished, iterates the list again to get the next item. If there are no more items, the thread stops. If all other threads are stopped, it can return to the main thread if it was stopped, or exit the program.

---

### Post by monkeyking on 2008-09-16
There are some different way you can do this.

I would do a job queue structure,
that a thread can pool jobs from.

That is,

As soon as a thread is finished fetch a new job,
and continue until job queue is empty.

The easyiest is to kill the thread and start a new one,

A more resourcefriendly is to keep the same threads alive,
and load the data on job change.


This is called boss/worker or master/slave
Do a google if you need more info,
[http://www.zdv.uni-mainz.de/cms-extern/DUS/progtool/dce31unx/develop/appdev/Appde155.htm](http://www.zdv.uni-mainz.de/cms-extern/DUS/progtool/dce31unx/develop/appdev/Appde155.htm)

Good luck

---

### Post by British0zzy on 2008-09-16
How can I get a thread to "fetch" a new job??
Is there a good example of boss/worker threading anywhere? I'm trying to google it, but nothing has helped much.
Thanks.

---

### Post by monkeyking on 2008-09-16
It depends very much on your problem. And the resources that they need. If they share datastructures you should be carefull to put a mutex around them.

If your threads don't generate new jobs, like no recursionstyle or similar.
Then you can prepare a job-list in a linked list fashion.
Then each thread should do a while loop, where it gets the resources it needs from the job list. If the job list is empty then the thread should of cause exit.

In very pseudocode that would be something like

[PHP]
typedef struct{
variabels need for a thread to calculate
...
}aJob

typedef struct{
aJob *job
listElem *next;
}listElem

static void aThread()
while LINKEDLIST->next != NULL
  calculate
}

int main(){
listElem *head = malloc(sizeof(listElem))
//generate joblist using head as the first element.

start threads in a while loop, wait for them to finish with join
}

[/PHP]

This should give you the general idea,
I haven't done pthread for years, but rememeber that if you need to pass alot of stuff to your thread you should pass a struct,
and not alot af pass by vals.

good luck

EDIT:
btw you should most definitely put a mutex around the job fetching part, and you should also make the head pointer point to ->next, so that the next thread will take the next element.

---

### Post by dwhitney67 on 2008-09-16
> **British0zzy said:**
> How can I get a thread to "fetch" a new job??
Is there a good example of boss/worker threading anywhere? I'm trying to google it, but nothing has helped much.
Thanks.
Have you read the posts from PC-XT and Monkeyking?  Use a structure (e.g. a queue) that each thread can access to pop the next available "job" (or whatever).

This structure will need to be made thread-safe, so that only one thread at a time can have access to it.  The "main-thread" (or your main-function) needs to prime this structure with the "jobs".

The boss/worker is not a widely used term; try producer/consumer.

P.S.  To answer one of the questions from your OP, no, there isn't a "join any" function available with pthreads.  You will need to implement your own if you wish for something that mimics it.

---

### Post by British0zzy on 2008-09-16
Thanks, I didn't know a global structure was the correct way of managing jobs. So the general idea is to have a global structure with all the information pertaining to jobs that need to be done, and let the threads manage themselves based on this data?
I will try this implementation and see if everything works out.

---

### Post by slavik on 2008-09-16
> **British0zzy said:**
> Thanks, I didn't know a global structure was the correct way of managing jobs. So the general idea is to have a global structure with all the information pertaining to jobs that need to be done, and let the threads manage themselves based on this data?
I will try this implementation and see if everything works out.
this is more efficient that killing a thread and starting a new one. (I have done both in the past), at some point, you will waste more time killing/creating threads than actually processing the items.

---

### Post by monkeyking on 2008-09-16
> **British0zzy said:**
> Thanks, I didn't know a global structure was the correct way of managing jobs. So the general idea is to have a global structure with all the information pertaining to jobs that need to be done, and let the threads manage themselves based on this data?
I will try this implementation and see if everything works out.

Yes, the key trick with threading is to have as little communication and dependencies between threads.

If each of your 1000 jobs, are independent of the others,
then 1 simple mutex around each pop'ing of the list should suffice.

Also remember that bug finding can be real pain in these threaded programs.
If you just use puts(), you'll have no idea which thread is talking.
So make your own printf and always remember to add the threadid, to your printf's. And depending on what you're doing, you should also tjeck for memory leaks and memory faults more rigrously.
For the memcheck I can recommend valgrind.

Start with your nonparallel program, and when this is working,
then make a very simple pthread program that basicly just says hello from thread1, hello from thread2, and so on.

The documentation is quite bad, and sometimes faulty.
So remember to check return vals from your threads.

good luck

---

