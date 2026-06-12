---
title: "[SOLVED] Pthread Condition Variables &amp;amp; Mutex locking?"
date: 2008-09-27
forum: Programming Talk
---

### Post by bluedalmatian on 2008-09-27
If a pthread waits on a condition variable using pthread_cond_wait(), I know pthread_cond_wait automatically unlocks the mutex before the thread goes to sleep but does it automatically lock it again when it returns or do I need to do that manually?

Imagine a thread which blocks on a queue until there is something on the Q:

while(workQ.empty())
{
       //Q empty, block
       pthread_cond_wait(&Qempty,&Qmutex);
}

//Q has a job on it so remove it from Q and process it

//do we need to relock Qmutex here?

MyTask task=workQ.front();   //remove next job from Q
workQ.pop();

---

### Post by dribeas on 2008-09-27
> **bluedalmatian said:**
> I know pthread_cond_wait automatically unlocks the mutex before the thread goes to sleep but does it automatically lock it again when it returns or do I need to do that manually?

Mutex is automatically acquired when your process finishes the wait in the condition. There is no need to acquire it again.

---

### Post by bluedalmatian on 2008-09-28
Thats great thanks dribeas

---

