---
title: "C++/pthread:multi-thread communication"
date: 2009-10-22
forum: Programming Talk
---

### Post by ieasylive on 2009-10-22
hi, i work with pthread ,what i need is to exchange private messages between threads.
And i try to use socket to connect threads, but the problem is, if we have 3 threads&#65306; Server A,Client B&#65292;Client C,there is no problem exchangeing msg between AB,AC,but how about BC.
how can i do?
Thx in advance.:confused:

---

### Post by dwhitney67 on 2009-10-22
> **ieasylive said:**
> hi, i work with pthread ,what i need is to exchange private messages between threads.
And i try to use socket to connect threads, but the problem is, if we have 3 threads&#65306; Server A,Client B&#65292;Client C,there is no problem exchangeing msg between AB,AC,but how about BC.
how can i do?
Thx in advance.:confused:

What you have asked is an architectural design question, more so that a programming question.  Thus there are many options at your disposal.  You need to choose which you feel is best.

One option is to have your clients pass messages to each other via the server, thus basically relegating the server to acting as a router.  Another option is have clients communicate directly with each other; in this case, one client would have to query the server if there are other client(s) available, and if so, what are the respective IP address/port number for each client or specific client.

I'm not sure why your threads are communicating using sockets, but once again, it is a choice that is up to you to make.  Personally I would have used some sort of message queue.  Now if your server and client were _separate_ applications (even if multi-threaded), then the use of sockets makes sense.

---

### Post by ieasylive on 2009-10-26
@dwhitney67
thanks!

I agree with you.  using socket made things more and more complicated, so i give up and make it with message queue.:D

---

### Post by dwhitney67 on 2009-10-27
Just bear in mind that you don't have to literally use a "message queue" (ie mq_open()).  You could always use a mutex-protected STL queue or other homemade queue container.  The key is to ensure that the queue is thread-safe to allow concurrent pushes and pops from the queue.

---

