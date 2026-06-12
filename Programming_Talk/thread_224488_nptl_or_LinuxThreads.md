---
title: "nptl or LinuxThreads"
date: 2006-07-28
forum: Programming Talk
---

### Post by benguin on 2006-07-28
Hi there,
I am running Dapper Drake, which I believe uses NPTL threads. I have two questions, though:

1. Does it also support LinuxThreads(Non NPTL)?
2. If so, can I specify that I want to build an application without NPTL and with LinuxThreads support? and how so?

Thanks a bunch!

-J-

---

### Post by LordHunter317 on 2006-07-28
Yes, it supports LinuxThreads if you set LD_ASSUME_KERNEL to 2.4.1 I believe, before running the application.  I believe that's all you have to do to build the application that way as well.

But why?  Unless you need to distribute a binary, there's no good reason to do that.

---

### Post by benguin on 2006-07-28
Hey thanks for the reply. Yes, that did the trick, I actually figured that out this morning at work, but thanks anyway.

Now the reason I need to do this. It's not my code to begin with. This is a somewhat old Robot control library thats is running on both linux and qnx systems. The system is a client-server like app, and it seems with NPTL certain parts are not functioning properly. Switching to LinuxThreads solved it.

Thanks again for the reply.

Cheers,
-J-

---

