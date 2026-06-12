---
title: "Can operating system be ruined by running faulty (C/C++) code?"
date: 2012-01-28
forum: Programming Talk
---

### Post by arroy_0209 on 2012-01-28
One problem with C-like language is that array boundary is not checked by the compiler and in case of overrun, the executable file may modify memory outside the area allocated to it (e.g., it may write over operating system memory or over some critical data for special purpose and so on). This may lead to system problems as is warned by some experts. Further, pointer conversion, if done in a wrong way, may lead to even system crashes.  I am not sure to what extent these warning apply to ubuntu 10.04LTS. Is there anybody who had sufferred from such complications? After reading these warnings, I am afraid of learning C/C++. Should I move to some safer languages like pyhton etc? What would you suggest?

---

### Post by shakabra on 2012-01-28
Sure, but if you are _learning_ then you should know what the code does _before_ you run it. Chances are slim.

---

### Post by r-senior on 2012-01-28
> **arroy_0209 said:**
> One problem with C-like language is that array boundary is not checked by the compiler and in case of overrun, the executable file may modify memory outside the area allocated to it (e.g., it may write over operating system memory or over some critical data for special purpose and so on).
It may try. It will fail. The operating system knows what memory each process can write to and the program gets a segmentation fault and crashes.

[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

> This may lead to system problems as is warned by some experts.
Such as who?

You won't break your system by accident learning C/C++.

---

### Post by arroy_0209 on 2012-01-28
Thanks for your reponses.

Regarding the question: who gave the warnings, I would just say that  I found these in a website which teaches C language. It is embarrassing for me to identify the person. Let us deal with the issue with scientific reasoning. That would clarify the issue. Thanks.

---

### Post by cgroza on 2012-01-28
This used to be a problem in non protected operating systems.
The program could read and write anywhere, including other program's memory.

---

