---
title: "Multithread GURUS -  Is there a way to grab process affinity and priority"
date: 2012-10-17
forum: Programming Talk
---

### Post by akvino on 2012-10-17
Is there a way to grab affinity and priority from the thread on the system basis, or does one have to query /proc file system for such info. 

This must be done within C application. I need to find out what runs on what core and what their scheduling, priority, and affinity masks are? 

Further clarification. I have an app running on the client side and they have scheduling issues. I need to capture system wide affinity, priority, and scheduling for each thread. Is this possible from the application without polling /proc?

---

