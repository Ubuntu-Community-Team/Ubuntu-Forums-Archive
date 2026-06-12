---
title: "Regarding pthreads!!!"
date: 2009-05-30
forum: Programming Talk
---

### Post by abhishek2301 on 2009-05-30
Hello,

I have some doubt regarding pthread implementation. I have a C++ class which contains a priority queue and some other methods and functionalities. I create 10 objects of that class and continuously call one method of each method in a loop. 
In different iterations, some objects push values into the priority queue of other objects. Now I want to use multi-threading so that my program runs faster. I want to use 2 threads and run 5 objects in one thread and 5 in the other. 
My question is whether will there be any synchronization issues in multithreading in my case.
I was thinking that there may be concurrent push operations to the priority queue of one object from objects in different threads. 
How should I handle this situation???
Will "mutex" will serve my purpose or I need some other functionalities???

Your help is highly appreciated.

---

### Post by slavik on 2009-05-30
"mutex" is what you are looking for :)

---

### Post by abhishek2301 on 2009-05-30
Thanks for the reply!!!
Will I wrap up the priority push operations with mutex lock and unlock instructions??
Will there be any deadlock issues when many objects are trying to access the same priority queue concurrently!!!

---

### Post by slavik on 2009-05-30
> **abhishek2301 said:**
> Thanks for the reply!!!
Will I wrap up the priority push operations with mutex lock and unlock instructions??
Will there be any deadlock issues when many objects are trying to access the same priority queue concurrently!!!
1. Can't tell what you will do, but yes, you should do that.
2. Only if your design is sane.

---

### Post by stroyan on 2009-05-30
You need to use a mutex to protect both push and pop operations.
In general you need to protect any data structures that may be read or modified by multiple threads.

Deadlock can be avoided by assuring that there will be no loop of threads waiting for other threads holding locks.  A loop can never happen with a single lock.  But multiple locks can allow more parallelism by allowing threads to lock and work on more than one data structure at the same time.  If you use multiple locks you need to prevent a loop of held locks.  The simplest way to do that is to design access such that a thread will only hold one lock at a time.  If a thread never waits for a second lock when holding one then it will never contribute to a deadlock.

---

### Post by abhishek2301 on 2009-05-30
Thanks very much for your inputs!!!
I want some suggestion.
I have the situation in my first post.
I have a 10 objects and I want to run a method in each object continuously through a loop.
Each object has a priority queue which has interactions with other objects.
Any object can push elements into others priority queue.
I had not considered parallelism in my design and constructed it in a strictly sequential logic only.
Now I want to speed up my program by using multi-threading.
I want to run the method of 5 objects in one thread and the method of the other 5 objects in another thread.
I am creating the objects in a main class and calling the methods of the object from the main class only.
In this situation will it be good idea to use multi-threading in the way described above or I need to redesign ??
Will i run into any sort of problems since there can be interactions among multiple threads.
If I need mutex to lock all the shared objects then how to do it since the threads will be running in the main class and the shared data structures(priority queue) are in a different class!!!

---

### Post by slavik on 2009-05-31
start making graphs ;)

---

