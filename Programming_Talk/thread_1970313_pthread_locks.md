---
title: "pthread locks"
date: 2012-05-01
forum: Programming Talk
---

### Post by chmcy on 2012-05-01
hello everyone, is there anyone that can help me with mutexes? Actually i've got a program where some threads are increasing a counter and when that counter reach to a value a signal is sent to the threads that are waiting to do an other job.

void *count(){
for (i=0 ; i<COUNT_PER_THREAD ; i++) {
    pthread_mutex_lock(&mtx)
    count++;
if (count == THRESHOLD)
  pthread_cond_signal(&cond);
  ....
  pthread_mutex_unlock(&mtx);
}
}

void *suspend(){
pthread_mutex_lock(&mtx)
while (count < THRESHOLD) { 
pthread_cond_wait(&cond, &mtx);
...
pthread_mutex_unlock(&mtx);
}
in that case if a thread in suspend function lock the mtx then how the other threads in count function increase the counter? :/
thank u

---

### Post by MadCow108 on 2012-05-01
pthread_cond_wait atomically unlocks the mutex and goes to sleep until signaled. so the mutex is free to be locked by another thread.
when it wakes up it locks the mutex again

---

### Post by ofnuts on 2012-05-01
> **chmcy said:**
> hello everyone, is there anyone that can help me with mutexes? Actually i've got a program where some threads are increasing a counter and when that counter reach to a value a signal is sent to the threads that are waiting to do an other job.

void *count(){
for (i=0 ; i<COUNT_PER_THREAD ; i++) {
    pthread_mutex_lock(&mtx)
    count++;
if (count == THRESHOLD)
  pthread_cond_signal(&cond);
  ....
  pthread_mutex_unlock(&mtx);
}
}

void *suspend(){
pthread_mutex_lock(&mtx)
while (count < THRESHOLD) { 
pthread_cond_wait(&cond, &mtx);
...
pthread_mutex_unlock(&mtx);
}
in that case if a thread in suspend function lock the mtx then how the other threads in count function increase the counter? :/
thank u
pthread_cond_wait() releases the mutex if you end up waiting...

---

### Post by MadCow108 on 2012-05-01
> **ofnuts said:**
> pthread_cond_wait() releases the mutex if you end up waiting...

please phrase your sentences more clearly, for a non native speaker it might appear you said the opposite of what I said, while you said the same :)

---

### Post by chmcy on 2012-05-01
ok thank u so much!! :) i've got two more questions if u or someone else can explain to me plss..
we there is a while() at the second function and not if()? and why at the one case the lock is inside for and at the other case outside while?? 
thank u!

---

