---
title: "errors when using semaphore"
date: 2008-02-09
forum: Programming Talk
---

### Post by shadow_boi on 2008-02-09
hi guys.

I am using ubuntu.

My codes have these lines:

semaphore mutex = 1;
semaphore full = 0;
semaphore empty = 9;

when I compiled my codes in terminal, i got the following errors:

 error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘mutex’
 error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘full’
 error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘empty’

Can you tell me what i did wrong?

thanks.

---

### Post by hod139 on 2008-02-09
What is a semaphore?  Is it a class that you wrote?  The compiler has no idea what it is.

---

### Post by shadow_boi on 2008-02-09
ph.

i thought it is a class in the c library.

ok, now i got it.

thanks.

---

### Post by shadow_boi on 2008-02-09
however, even i do:

#include <pthread.h>
 pthread_semaphore_t *headmutex;

I also got errors.

---

### Post by aks44 on 2008-02-09
Google only yields TWO (!!!) results when searching for **pthread_semaphore_t**. That makes me seriously doubt that it is declared in pthread.h (or anywhere else for that matter).........


EDIT: here's what the [first Google link]("http://www.cs.ucsb.edu/~rich/class/cs170/notes/Semaphores/index.html") says about it:
```
/* NOTE: this code is notional only; the Pthreads package does not include
 *       support for semaphores.  They are imagined here for purposes of
 *       presentation only.  This code would never compile, let alone run.
 */
```(it is even written in **bold** in the original page, just above the code you copy-pasted from that very page)

:roll:

---

### Post by shadow_boi on 2008-02-09
hm.

thanks.

so i need to write my own semaphone class, since either c library or ubuntu has it?

---

### Post by aks44 on 2008-02-09
[http://www.google.com/search?q=posix+semaphore](http://www.google.com/search?q=posix+semaphore)

---

