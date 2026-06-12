---
title: "waking kernel threads"
date: 2008-09-28
forum: Programming Talk
---

### Post by akshata on 2008-09-28
Hi,
    Im a novice to kernel programming and needed some help

I have wriiten a simple program to create kernel threads.

init_module()
{
struct task_struct *k;
k=kthread_create(mythread,data,"thread 1");
}

static int mythread(void * data)
{
..................
}

When i do insmod the thread iss created by mythread is not called. Should i wake up the thread? how do i do it?
How do i put it to sleep again? Do i ahev  to use some semaphores for this?

Thanks

---

### Post by the_unforgiven on 2008-09-28
> **akshata said:**
> Hi,
    Im a novice to kernel programming and needed some help

I have wriiten a simple program to create kernel threads.

init_module()
{
struct task_struct *k;
k=kthread_create(mythread,data,"thread 1");
}

static int mythread(void * data)
{
..................
}

When i do insmod the thread iss created by mythread is not called. Should i wake up the thread? how do i do it?
How do i put it to sleep again? Do i ahev  to use some semaphores for this?

Thanks
Check this:
[http://lwn.net/Articles/65178/](http://lwn.net/Articles/65178/)

Essentially, you need to do wake_up_process() on the return value of kthread_create().

In normal cases, this will be done asynchronously by the kernel when the event on which the thread is waiting is triggered (say, via interrupt service routine, workqueue or tasklet).

---

