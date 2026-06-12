---
title: "semaphores, atomic wait(s) and signal(s)"
date: 2010-02-25
forum: Programming Talk
---

### Post by cybo on 2010-02-25
i'm reading a book on OS and it talks about semaphores. it says that wait(s) and signal(s) should be implemented as atomic operations. to do that we should use spinlocks, but the book doesn't show how to do it. i'm not new to coding but i'm relatively new to coding for multiple processes and threads

below is the pseudocode i came up with (part of it is from the book):

```

typedef struct {
  int lock; // 1 - locked, 0 - unlocked
  int value;
  struct process* list;  
} sempahore;

void wait(sempahore* s) {
  // spin until the lock is obtained
  while(compare_and_swap(&(s->lock), 0, 1));

  s->value--;
  if (s < 0) {
    add this process to s->list;
    block();
  }
 
  // release the semaphore
  compare_and_swap(&(s->lock), 1, 0);
}

void signal(semaphore* s) {
  // spin until the lock is obtained
  while(compare_and_swap(&(s->lock), 0, 1));

  s->value++;
  if (s->value <= 0) {
    remove process P from s->list;
    wakeup(P);
  }

  // release the semaphore lock
  compare_and_swap(&(s->lock), 1, 0);
}

```

there two questions i'd like to ask
1) is that even correct?
2) seems a little silly to lock the semaphore, since the semaphore itself is used as a lock. if you were to implement wait() and signal() atomically how would you do it?

any help is appreciated.

---

### Post by Some Penguin on 2010-02-25
Correctness seems unlikely, because I don't see how that code will know when to return from the block() function when you haven't passed in any parameters.

You will probably also want to describe the compare_and_swap operation.

---

### Post by cybo on 2010-02-26
that is how compare_and_swap is defined in wikipedia ([http://en.wikipedia.org/wiki/Compare-and-swap]("http://en.wikipedia.org/wiki/Compare-and-swap")):

```

int compare_and_swap (int *word, int testval, int newval) {
   int oldval;
   oldval = *word;
   if (oldval == testval) *word = newval;
   return oldval;
}
```

the basic idea in compare_and_swap is that it tests memory location word for the testval. if *word and testval are the same then assign *word a newval if they are different leave *word as it was before. compare_and_swap always returns an old value stored in *word. 

compare_and_swap usually does not need to be implemented, the code is just given in order to understand what it does. this function is usually provided by the system library (very often it is implemented in actual hardware) and is atomic, meaning that when this function is executing is cannot be interrupted by any thread.

---

