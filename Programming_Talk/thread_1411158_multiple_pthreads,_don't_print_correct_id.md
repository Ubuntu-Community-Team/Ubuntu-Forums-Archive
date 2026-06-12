---
title: "multiple pthreads, don't print correct id"
date: 2010-02-19
forum: Programming Talk
---

### Post by cybo on 2010-02-19
i have a problem.

i'm creating 30 threads but for some reason i don't get their id's printed correctly. the code is below. can anyone explain what is the problem.

```

void* thread_function(void* arg) {
  int id = *(int*)arg
  printf("thread id = %d\n", id);
}

#define THREAD_COUNT 30
int main() {
  pthread_t threads[THREAD_COUNT];
  int i = 0;
  
  for (i = 0; i < THREAD_COUNT; i++) {
    pthread_create(&threads[i], NULL, thread_function, (void*)&i);
  }

  for (i = 0; i < THREAD_COUNT; i++) {
    pthread_join(threads[i], NULL);
  }
}

```

the output i get looks like this

thread id = 1 
thread id = 1 // <-- problem
thread id = 2
thread id = 4
thread id = 4 // <-- problem
thread id = 6
thread id = 6 // <-- problem
thread id = 7
thread id = 8
.............
(correct ids, no id repetition)
.............
thread id = 25
thread id = 26
thread id = 28
thread id = 28 // <-- problem
thread id = 1  // <-- problem

as you noticed some of the ids are repeated (and some are missing). this doesn't happen just with 30 threads, it happens with any number of threads that are created (except when only 1 is created). can anyone explain why this is happening? i talked to several people and none of them can explain it. 

any help is appreciated.

---

### Post by Simon17 on 2010-02-19
Congratulations. You've just learned firsthand about race conditions.

Each thread has access to the same variable, i. Since you have no have of controlling how or when the threads execute, i may take on any value when the threads are running.

---

### Post by falconindy on 2010-02-19
> **Simon17 said:**
> Congratulations. You've just learned firsthand about race conditions.

Each thread has access to the same variable, i. Since you have no have of controlling how or when the threads execute, i may take on any value when the threads are running.
Hrmm... 'i' is being accessed sequentially in the for loop. The created threads aren't accessing 'i' on their own. They're given life only to print their ID and die. How is this causing a race?

---

### Post by Simon17 on 2010-02-19
They aren't given a unique id, they're given a pointer to i. So maybe "race" isn't the right term, but the problem still comes about because each thread is accessing i concurrently when the thread is created.

---

### Post by MadCow108 on 2010-02-19
the loop creates asynchron threads
There is no guarantee that the thread will have executed any code before the main thread loop advances the counter (and thus changes the data with which the thread works)

example:
i=0
thread 0 created
i=1
thread 0 accesses i reads 1
thread 1 created
thread 1 reads i reads 1
i=2

---

### Post by cybo on 2010-02-19
so how would i create arbitratry number of threads, each with a unique id?

---

### Post by Simon17 on 2010-02-19
Make a copy of i when when creating the thread, not in the new thread.

---

### Post by cybo on 2010-02-19
> **Simon17 said:**
> Make a copy of i when when creating the thread, not in the new thread.

i still get the same result.

here is what i have done:

```

void* thread_function(void* arg) {
  int id = *(int*)arg
  printf("thread id = %d\n", id);
}

#define THREAD_COUNT 30
int main() {
  pthread_t threads[THREAD_COUNT];
  int i = 0;
  **_int j = 0;_**
  
  for (i = 0; i < THREAD_COUNT; i++) {
    _**j = i**_;
    pthread_create(&threads[i], NULL, thread_function, **_(void*)&j_**);
  }

  for (i = 0; i < THREAD_COUNT; i++) {
    pthread_join(threads[i], NULL);
  }
}

```

---

### Post by MadCow108 on 2010-02-19
this is just a single copy
you need THREAD_COUNT copies.

---

### Post by howlingmadhowie on 2010-02-19
> **cybo said:**
> i still get the same result.

here is what i have done:

```

void* thread_function(void* arg) {
  int id = *(int*)arg
  printf("thread id = %d\n", id);
}

#define THREAD_COUNT 30
int main() {
  pthread_t threads[THREAD_COUNT];
  int i = 0;
  **_int j = 0;_**
  
  for (i = 0; i < THREAD_COUNT; i++) {
    _**j = i**_;
    pthread_create(&threads[i], NULL, thread_function, **_(void*)&j_**);
  }

  for (i = 0; i < THREAD_COUNT; i++) {
    pthread_join(threads[i], NULL);
  }
}

```

don't use an & :)

this will force the program to pass by value and not by reference:

```

pthread_create(&threads[i], NULL, thread_function, (void*)i);

```

then you can find the threadid by just recasting to a long inside thread_function:

```

void* thread_function(void *threadid) {
  long tid=(long)threadid;
...
}

```

---

### Post by MadCow108 on 2010-02-19
that also works but saving integers in pointer types may have portability issues.
see:
[http://library.gnome.org/devel/glib/unstable/glib-Type-Conversion-Macros.html](http://library.gnome.org/devel/glib/unstable/glib-Type-Conversion-Macros.html)

---

### Post by Simon17 on 2010-02-19
> **MadCow108 said:**
> that also works but saving integers in pointer types may have portability issues.
see:
[http://library.gnome.org/devel/glib/unstable/glib-Type-Conversion-Macros.html](http://library.gnome.org/devel/glib/unstable/glib-Type-Conversion-Macros.html)

Yes, that's just a bad idea.

OP, can you just change the function so that it just accepts an int, and not a pointer?

---

### Post by howlingmadhowie on 2010-02-19
> **Simon17 said:**
> Yes, that's just a bad idea.

OP, can you just change the function so that it just accepts an int, and not a pointer?

Actually it's a fairly standard solution and perfectly safe as long as you know that the number won't be longer than however long a pointer is, so nowadays it's quite safe to pass 32bit numbers this way for desktop PCs, and quite certainly safe up to NUM_THREADS for any sensible value of NUM_THREADS.

Changing the function isn't really an option. POSIX threads just work like that.

Another solution is to create a NUM_THREADS length array and then store the numbers 1, 2, 3, ... in it. Then you pass a pointer to the element you want in the array.

---

### Post by cybo on 2010-02-19
thanks everyone. both ways worked. i didn't know that it is possible to stuff an integer into a pointer.

---

### Post by Simon17 on 2010-02-19
Okay Howie, I didn't know that the pointer argument was required. To be honest, I don't work with pthreads. I only use boost::thread.

---

### Post by howlingmadhowie on 2010-02-19
> **Simon17 said:**
> Okay Howie, I didn't know that the pointer argument was required. To be honest, I don't work with pthreads. I only use boost::thread.

Yeah, it's a strange thing about POSIX threads. It's actually perfectly adequate, because you can create a structure for each thread you create and then pass a pointer.  I've never used boost before, but lots of people talk about it, so maybe i'll have a look :)

---

