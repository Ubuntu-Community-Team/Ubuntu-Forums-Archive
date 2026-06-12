---
title: "muliti processors with java apps"
date: 2010-03-21
forum: Programming Talk
---

### Post by badperson on 2010-03-21
Hi,
now that multi processor machines are the norm, when and how will a java app use more than one processor? If you create multiple threads, and a separate processor is available, will the jvm select a free processor on its own? 

Do you need to explicity instruct your app to use more than one processor, or do you need to create a new jvm for every task using its own processor? I've googled around and many posts indicate a pretty unimpressive increase in performance using multi cpus. 

What's the best skillset to develop for this?
thanks,
bp

---

### Post by CptPicard on 2010-03-21
> **badperson said:**
> If you create multiple threads, and a separate processor is available, will the jvm select a free processor on its own? 

Simply put, yes. That's all there is to it.

> I've googled around and many posts indicate a pretty unimpressive increase in performance using multi cpus. 

Depends on what they're doing. A typical issue that Java programmers seem to be prone to is also constantly spawning new threads for even the smallest of tasks; thread creation is a relatively expensive operation.

---

### Post by slavik on 2010-03-21
jvm doesn't select threads, the threading implementation in the kernel does.

There are 3 different pthread implementation, the one in Linux is called NTPL which uses kernel threads (in fact, Linux scheduler doesn't really distinguish between threads and processes). The pthread implementation in some older solaris versions used user space threads (that is similar to how Python does threads).

---

