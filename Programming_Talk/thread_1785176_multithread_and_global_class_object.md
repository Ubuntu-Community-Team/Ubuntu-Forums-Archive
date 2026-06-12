---
title: "multithread and global class object"
date: 2011-06-17
forum: Programming Talk
---

### Post by shao tian on 2011-06-17
I am making a multithread program using C++, GNU under Ubuntu. 
There will be a global class object called server. server.processRequest(str) will be called by each thread. Question is, within the server.processRequest(), should I dynamically declare all the variables needed to be used? What I am concerning is, if two thread are calling server.processRequest() at the same time, are the variables used in server.processRequest() not thread-safe? the server object is global to all threads, dose that mean the methods of this object is also global to all threads, instead of that each thread will have a new copy of the global objects' method?

---

### Post by BkkBonanza on 2011-06-18
You want to make sure any data used by a thread is local to that thread unless you explicitly need it to be shared by all threads. Generally this means using only local variables in the thread function, but you can allocate heap data as well used by each thread. Do not use anything global unless you have very well considered how it will be affected by simultaneous changes by multiple threads. 

Thread safe variables are only the start of what you need to consider. You also should read up on semaphores and similar tools for managing how threads interact. If you don't understand multi-threading safely then you will have problems that are very hard to debug, and appear to be random.

---

