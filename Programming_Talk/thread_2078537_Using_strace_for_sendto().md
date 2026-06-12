---
title: "Using strace for sendto()"
date: 2012-10-31
forum: Programming Talk
---

### Post by DBQ on 2012-10-31
Hi everybody.

I am using strace to trace my UDP client and server (written in C).

I want to be able to see (using strace) what target port the client specifies in sendto() system call.  Is there a way of doing this?

Thanks in advance!

---

### Post by Tony Flury on 2012-10-31
> **DBQ said:**
> Hi everybody.

I am using strace to trace my UDP client and server (written in C).

I want to be able to see (using strace) what target port the client specifies in sendto() system call.  Is there a way of doing this?

Thanks in advance!

According to "man strace" - strace will print the arguments to systems calls - have you actually tried it ?

---

