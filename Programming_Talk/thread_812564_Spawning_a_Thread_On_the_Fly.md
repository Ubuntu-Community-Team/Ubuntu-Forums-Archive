---
title: "Spawning a Thread On the Fly"
date: 2008-05-30
forum: Programming Talk
---

### Post by dwhitney67 on 2008-05-30
Today I was asked a (simple) question about how I would design a server to support receiving data from multiple clients (via TCP).

I have resolved a similar problem to this in the past... more than 7 years ago... however I cannot remember the design I settled on.

My main concern is not so much on how to start a new thread for a client that connects, but instead on how to get the parent thread to "join" with a child thread when it terminates, and yet at the same time field (potentially) new connections from additional clients.

Since it is quite possible that the server would have N-number of child-threads running, is there an easy way to join with any thread?  Bear in mind that the threads may not necessary behave in a "FIFO" fashion... in other words, it cannot be assumed that the first thread started will be the first to end.

To summarize, what I need is a "join-any" construct.  The pthread library provides the pthread_join() function, but this works only on a per thread basis.  How can I monitor (join) with any random thread that terminates?

Any thoughts?


P.S.  I wish I could change the thread title... I really don't care about spawning... it's the capturing of the end-life of a thread that really matters.

---

### Post by ZylGadis on 2008-05-30
The modern way to do TCP servers is multiplexing fds. Take a look at epoll.

---

### Post by smartbei on 2008-05-30
A simple enough way would be to make a thread acquire a sempahore on entering and release it when finished. Then, you could the the main program thread just wait until the semaphore is at its maximum value (which could be reasonably high - your not going to have more than a million threads...).

---

### Post by stroyan on 2008-05-30
If you use pthread_detach or pthread_attr_setdetachstate to create each
thread as detached instead of joinable then you don't need to make some
thread call pthread_join for each thread.  The resources of the thread
will be immediately released when the thread terminates.

  But you may want to use a stable pool of worker threads and use
condition variables to assign work to them rather than incurring the
overhead of frequently starting and terminating threads for short-lived
activities.  Whether using a stable thread pool or dynamic threads you
may need to consider what to do when there is a resource pinch such as
running low on thread stack space or maximum open file descriptors.

---

### Post by dwhitney67 on 2008-05-31
Stroyan, thank you for the excellent advice.

I have heard of detachable threads, however until now, I never fully understood their benefit.

---

