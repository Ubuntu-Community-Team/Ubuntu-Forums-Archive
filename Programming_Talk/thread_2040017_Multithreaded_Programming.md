---
title: "Multithreaded Programming"
date: 2012-08-10
forum: Programming Talk
---

### Post by Gajanansp on 2012-08-10
Hi All , please help in problem of multithreaded programming . The scenario is like there are more than 2 threads locking a mutex. If first thread has locked a mutex and processing some data, more than 2 threads are waiting to unlock the mutex.
When mutex is unlocked by first thread, I was expecting mutex lock by very first thread who is waiting on mutex. But it does not happen. First thread wakes up at the last, most of times. I tried scheduling FIFO but did not observe any change. 
Please suggest .

---

### Post by Bachstelze on 2012-08-10
Normally, you have no way to know which thread will acquire the mutex first once it is released. If you want to ensure that one thread acquires it before the other, you have to use mutexes for that, as well.

---

### Post by Gajanansp on 2012-08-10
But if threads are getting created dynamicaly, then how can i use mutexes for each thread.
sceduling policies can be  set for threads but that also didn't work. As threads are sending data over socket which are supposed to received at other end in sequence. But due to this problem data is recieved in random order leading to data loss.

---

### Post by dwhitney67 on 2012-08-10
> **Gajanansp said:**
> As threads are sending data over socket which are supposed to received at other end in sequence. But due to this problem data is recieved in random order leading to data loss.

This is a design problem, not an issue with the threading library.

Perhaps you should consider including within the packets you send a unique sequence number so that the entire data set can be reconstructed on the receiving end in the proper order.

Or perhaps just use one thread perform the data sending.

---

### Post by Gajanansp on 2012-08-10
> **dwhitney67 said:**
> This is a design problem, not an issue with the threading library.
 
Perhaps you should consider including within the packets you send a unique sequence number so that the entire data set can be reconstructed on the receiving end in the proper order.
 
Or perhaps just use one thread perform the data sending.
 
Dear Friend, number of data packets I am sending is not constant. I am already sending a mesgtype as H for 1st packet and T for last packet. 
Other packets are having  mesgtype as D. But problem occurs when packet with T reaches before packet D, cause receiving program ignores remaining packets.
 
The sending process has to be multithreaded as it sends response to around 400-500 receiving programs.

---

### Post by dwhitney67 on 2012-08-10
As I stated earlier, this is a design problem.

Which ever thread is sending packet T needs to check that all other threads, that may be sending packet D, are complete.  I do not know your application's design well enough to comment on it, so I cannot suggest a definitive way for you to solve this problem.

---

### Post by Gajanansp on 2012-08-10
> **dwhitney67 said:**
> As I stated earlier, this is a design problem.
 
Which ever thread is sending packet T needs to check that all other threads, that may be sending packet D, are complete. I do not know your application's design well enough to comment on it, so I cannot suggest a definitive way for you to solve this problem.
 
Ok. Then can you suggest approach for follwoing code snippet. 
> **Sample Code]
#include <stdio.h>
#include <pthread.h>
pthread_attr_t attr said:**
> ;
int enter = 0;
void wait4it()
{
printf("\nTID :%d BEFORE LOCK MUTEXT",pthread_self());
pthread_mutex_lock(&tmutex);
printf("\nTID :%d LOCKED MUTEXT",pthread_self());
if(enter == 0)
{
printf("\nI Am First Thread %d ",pthread_self());
enter++;
sleep(2);
}
sleep(2);
printf("\nTID :%d UNLOCKING MUTEXT",pthread_self());
pthread_mutex_unlock(&tmutex);
}
main()
{
int CurrPolicy,test,NewPolicy;
int count1 =0,rc;
int * arg = &test;
pthread_attr_init(&attr);
test = pthread_attr_getschedpolicy(&attr,&CurrPolicy);
printf("CurrPlicy [%d]",CurrPolicy);
 
for (count1=0; count1<6 ;count1++)
{
rc=pthread_create(&threads[count1],NULL,wait4it,(void *)arg);
if (rc)
{
printf("\n ERROR in pthread_createis %d\n", rc);
fflush(stdout);
exit(-1);
}
 
}
printf("\n MAIN: Waiting For Threads to Exit");
for (count1 = 0;count1 < 6 ;count1 ++)
{
pthread_join(threads[count1],NULL);
}
}

 
O/P for above program is :
TID :258 BEFORE LOCK MUTEXT
TID :258 LOCKED MUTEXT
I Am First Thread 258
***TID :515 BEFORE LOCK MUTEXT***
MAIN: Waiting For Threads to Exit
TID :772 BEFORE LOCK MUTEXT
TID :1029 BEFORE LOCK MUTEXT
TID :1286 BEFORE LOCK MUTEXT
TID :1543 BEFORE LOCK MUTEXT
TID :258 UNLOCKING MUTEXT
TID :772 LOCKED MUTEXT
TID :772 UNLOCKING MUTEXT
TID :1029 LOCKED MUTEXT
TID :1029 UNLOCKING MUTEXT
TID :1286 LOCKED MUTEXT
TID :1286 UNLOCKING MUTEXT
TID :1543 LOCKED MUTEXT
TID :1543 UNLOCKING MUTEXT
***TID :515 LOCKED MUTEXT***
***TID :515 UNLOCKING MUTEXT***

---

### Post by dwhitney67 on 2012-08-10
Please post code using CODE tags; don't QUOTE it.

Now, please tell me, what is wrong with the output?

You can setup thread priorities, or even play with the scheduling style, but I'm not quite sure what to make of the example you offered is trying to demonstrate?

The first thread that is invoked will get the mutex, increment the counter, and then unlock the mutex after some delay, and then exits.  The next thread that acquires the lock could be any of the remaining 5 threads.

Btw, the proper signature for a thread function is:
```

void* thread(void* arg)
{
    ...
}

```
The thread function should also return a void pointer, or NULL.

---

### Post by ofnuts on 2012-08-10
> **Gajanansp said:**
> But if threads are getting created dynamicaly, then how can i use mutexes for each thread.
sceduling policies can be  set for threads but that also didn't work. As threads are sending data over socket which are supposed to received at other end in sequence. But due to this problem data is recieved in random order leading to data loss.Basically you cannot expect threads to be executed in a given order. If you need code to be executed in a very specific order, keep it in one single thread. In your case that would mean one thread per receiver, so all data for one receiver would be "naturally" sent in order.

---

### Post by Gajanansp on 2012-08-13
> **dwhitney67 said:**
>  
Now, please tell me, what is wrong with the output?
my need is all waiting threads should wake up in order they are waiting on mutex.
 
 
>  
You can setup thread priorities, or even play with the scheduling style, but I'm not quite sure what to make of the example you offered is trying to demonstrate? 
 
I have tried FIFO thread scheduling for same program which did not change the output. As the application is serving heavy requests hence it needs to be multithreaded to serve the responses.
Consider on scenario where for one request 10 responses will be sent.
Response packets are sent in the sequence first packet with msgtype as H,
remaining 8 packets as D and last packet as T.
While sending D packet, another thread is trying to send T packet. Once mutex is unlocked thread with packet T wakes up and sends packet, but there are D packets not yet sent, leading to ignore further D packets at receiving end.
 
 
>  
Btw, the proper signature for a thread function is:
```

void* thread(void* arg)
{
    ...
}

```
The thread function should also return a void pointer, or NULL.
Its just sample code where i missed the proper signature. Thanks for poiting it. 
I can not post my original code over here, hence i posted a code which demonstrate the work done by actual code.

---

### Post by dwhitney67 on 2012-08-13
> **Gajanansp said:**
> 
Consider on scenario where for one request 10 responses will be sent.
Response packets are sent in the sequence first packet with msgtype as H,
remaining 8 packets as D and last packet as T.
Why can't this be done in a single thread?

A separate thread (from a pool of threads) could be used to satisfy every request that is made.

If you still want to pursue the overly complex solution of using multiple threads to send packets H, D, and T, then consider devising a state-driven design, perhaps one that includes using condition signals.

---

### Post by Gajanansp on 2012-08-13
I think I should redefine my question, may be it will help u to identify the issue.
 
  There is a relay process which receives request over socket (multiple senders ) and forwards it to any of 4-5 processes depending upon type of request. Processed data is send back to relay process on IPC (msg queue) which is forwarded over socket. 
     Hence data receievd on IPC is not response of one request. It can be of multiple requests, hence multithreading is used. One thread will read data from message queue and assign it to worker threads.
 
For each socket mutex is associated with it, which is locked/unlocked if multiple response packets on single socketare to be send. Now these packets needs to be forwarded in order of H,D and T.

---

### Post by dwhitney67 on 2012-08-13
I did not fully understand what you wrote; please correct if any of what I interpreted is incorrect.

1.  You have a single thread, named 'relay', that receives requests (from other processes) via a socket.

2.  For each request, a new thread is started to process the request.

3.  The thread that processes the request inserts data onto a Message Queue.

4.  The 'relay' thread forwards data that is received on the Message Queue to other processes via the socket.

If any of the steps above are incorrect, please let me know.

As for message types H, D and T, are all these generated by the thread processing a single request?  Or are messages H and T generated elsewhere?

---

### Post by Gajanansp on 2012-08-13
> **dwhitney67 said:**
>  
1. You have a single thread, named 'relay', that receives requests (from other processes) via a socket.
Relay is a process which has ReadThread and WriteThread
ReadThread- Receives data from multiple sockets and forwards over IPC to other processes to prepare response packets.
WriteThread - This thread reads data from message queue and spwans worker thread to send it over socket
 
> 
2. For each request, a new thread is started to process the request.
When data is received on any socket a thread is created which reads data from socket and forwards it to proper process depending upon the type of requests and **exits.**
 
> 
3. The thread that processes the request inserts data onto a Message Queue.
Here other process which has processed data inserts number of messages on message queue. Packets in the message queue can of same requests or different requests. 
 
> 
4. The 'relay' thread forwards data that is received on the Message Queue to other processes via the socket.
Here One thread is reading data from message queue and forwarding it to worker threads getting created dynamically.
While sending data over socket, each thread locks a mutex associated with corresponding socket and then sends data and unlocks the mutex on success.
 
 
> 
As for message types H, D and T, are all these generated by the thread processing a single request? Or are messages H and T generated elsewhere?
message types H,D and T are generated by process after receiving from RelayThread. It selects records from DB and sends number of rows one by one. Hence first packet is sent as H, next few as D and last as T.
These packets are received again by Relay write thread which forwards to worker thread.
 
 
Thanks a lot for following up with problem.

---

### Post by Gajanansp on 2012-08-17
Some one please suggest something .....???

---

### Post by ofnuts on 2012-08-17
Maybe you root design has a problem. You can throw any amount of threads/mutexes over it without making it work.

Can you express the basic requirements without even thinking about thread/processes (your specs should not use these words)  (maybe even make a small schematic)? Then we may came up with a design that is implementable (and will likely involve threads, but likely not as you think).

---

