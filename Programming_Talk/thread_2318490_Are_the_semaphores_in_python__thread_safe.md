---
title: "Are the semaphores in python  thread safe?"
date: 2016-03-26
forum: Programming Talk
---

### Post by mfvpcrec on 2016-03-26
Hello everyone , I have a doubt after reading a python's page about semaphores. In this page [https://docs.python.org/3/library/asyncio-sync.html](https://docs.python.org/3/library/asyncio-sync.html) 
tells that the Semaphore class is not thread safe:confused:. 
Exactly What  that means?  I mean  if a semaphore is a method to sync two or more threads 
Why a semaphore is not thread safe?

Thanks to everyone!

---

### Post by bernard-godard on 2016-03-27
The URL you mention is about Inter Process Communication for synchronizing different tasks not different threads. Since each task/process has its own memory, thread safety is not a requirement.
Maybe you want to look at threading instead:
[https://docs.python.org/3.5/library/threading.html](https://docs.python.org/3.5/library/threading.html)

Note however that because of the GIL, threads in CPython are not as efficient as they could be (only one thread can execute python code at a given time).
You might then prefer to use multiprocessing:
[https://docs.python.org/3.5/library/multiprocessing.html](https://docs.python.org/3.5/library/multiprocessing.html)

---

### Post by mfvpcrec on 2016-03-27
Thank you very much, really and interesting appreciation about threads in CPython
Thanks bernard-godard

---

