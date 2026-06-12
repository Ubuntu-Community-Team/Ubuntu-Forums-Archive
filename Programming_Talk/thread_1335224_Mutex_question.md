---
title: "Mutex question"
date: 2009-11-23
forum: Programming Talk
---

### Post by SwedishWings on 2009-11-23
I have been digging around to find some simple mutex/semaphore functions. I found references to set_bit() and get_bit(), but found zero doc's on how to use them. 

I found a lot more on sepamphores but they are, perhaps, overkill.

Any ideas?

/Mike

---

### Post by Can+~ on 2009-11-23
Guessing that it's C:

```
#include <semaphore.h>
```

When compiling, use [FONT="Courier New"]-lpt[/FONT] (or [FONT="Courier New"]-lpthread[/FONT]). Also, read the manpages about linux libraries:

```
man 3 sem_init
```

Btw, if you don't have man(3), install them with:

```
sudo apt-get install manpages-dev
```

---

### Post by SwedishWings on 2009-11-24
Thanks!

After some more digging, i found what i was looking for:

```
#include <pthread.h>

// Init mutex
/////////////

pthread_mutex_t mutex;
pthread_mutex_init(&mutex, NULL);

// Use mutex 
////////////

pthread_mutex_lock(&mutex);

// do critical stuff in my thread here 

pthread_mutex_unlock(&mutex);

```

---

