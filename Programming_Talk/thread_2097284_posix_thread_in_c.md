---
title: "posix thread in c"
date: 2012-12-22
forum: Programming Talk
---

### Post by zhaoc033 on 2012-12-22
Hi, i am teaching myself to use posix thread. Below is my code.
I am expecting the program to output:
in main thread: i = 0
in child thread: i = 0 (maybe 1 here...the goal is to test shared variables in threads.)
However, the only output i see is 
in main thread: i = 0
Why doesnt the child thread reach  this if condition? 
if (pthread_equal(tid, mainThread) != 0)
How should i change the code to get the expected output?

```

  1 #include <stdio.h>
  2 #include <stdlib.h>
  3 #include <pthread.h>
  4 
  5 void* thread(void* vargp);
  6 
  7 int main(){
  8         int i = 0;
  9         pthread_t mainThread = pthread_self();
 10         pthread_t tid;
 11         pthread_create(&tid, NULL, thread, NULL);
 12         if (pthread_equal(tid, mainThread) != 0){
 13                 printf("in child thread: i=%d\n", i);
 14                 i++;
 15         }
 16         if (pthread_equal(tid, mainThread) == 0){
 17                 printf("in main thread: i=%d\n", i);
 18                 i++;
 19         }
 20 
 21         pthread_join(tid, NULL);
 22         exit(0);
 23 
 24 }
 25     
 26 
 27 void *thread(void* vargp){
 28         //i++;
 29         printf("Hello\n");
 30         return NULL;
 31 }


```

---

### Post by Bachstelze on 2012-12-22
From [font=monospace]man pthread_create[/font] (I am on FreeBSD right now so yours may differ if you are on Linux, but the idea stays):

>      The thread is created executing start_routine with arg as its sole argu&#8208;
     ment.  [B]If the start_routine returns, the effect is as if there was an
     implicit call to pthread_exit() using the return value of start_routine
     as the exit status.[/B]


Your "child" thread never executes main(), it executes thread(), and when thread() returns the thread exits. I think you expected pthread_create() to behave like fork(); it doesn't.

---

### Post by zhaoc033 on 2012-12-22
> **Bachstelze said:**
> From [font=monospace]man pthread_create[/font] (I am on FreeBSD right now so yours may differ if you are on Linux, but the idea stays):



Your "child" thread never executes main(), it executes thread(), and when thread() returns the thread exits. I think you expected pthread_create() to behave like fork(); it doesn't.

Then which part of the program gets run concurrently?

---

### Post by Bachstelze on 2012-12-22
> **zhaoc033 said:**
> Then which part of the program gets run concurrently?

As you have coded it, none.

---

### Post by zhaoc033 on 2012-12-22
> **Bachstelze said:**
> As you have coded it, none.
Can you explain a little why?
I was thinking the if below and the thread function would be executed at the same time.
```
if (pthread_equal(tid, mainThread) == 0){
                  printf("in main thread: i=%d\n", i);
                  i++;
}
```

---

### Post by Bachstelze on 2012-12-22
> **zhaoc033 said:**
> Can you explain a little why?
I was thinking the if below and the thread function would be executed at the same time.
```
if (pthread_equal(tid, mainThread) == 0){
                  printf("in main thread: i=%d\n", i);
                  i++;
}
```

Your "child" thread executes your thread() function, and the "main" thread goes on in the main() function. They are running concurrently, but they do not run the same code.

---

