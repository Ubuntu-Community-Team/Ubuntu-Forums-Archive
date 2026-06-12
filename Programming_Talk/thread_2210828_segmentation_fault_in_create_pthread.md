---
title: "segmentation fault in create_pthread"
date: 2014-03-12
forum: Programming Talk
---

### Post by ken18 on 2014-03-12
Trying to learn about pthread and am getting a segmentation fault using the following program.

Any idea why the segmentation fault?

```
#include <stdio.h>
#include <sys/types.h>
#include <sys/syscall.h>
#include <pthread.h>
#include <unistd.h>
#include <math.h>


void * thread(void *arg) {
    int i;
    double tmp;

    for (i=0; i<100000; i++) { 
        tmp = cos( (double) i); 
        tmp *= tmp;
        } 
    return 0;
}

int main(void) {
    int i;
    int n = 40000;    // result is segmentation fault.  n = 30000 is ok...
                      // note: cat /proc/sys/kernel/threads-max returns 90245
                      // compile string: gcc pthread7.c -Wall -lm -lpthread
    pthread_t tid[n];
 
    for (i=0; i<n; i++ ) { pthread_create( &tid[i], NULL, thread, NULL ); }
    for (i=0; i<n; i++ ) { pthread_join( tid[i], NULL ); }
    return 0;
}
```

---

### Post by spjackson on 2014-03-13
Your tid array isn't initialized, so if pthread_create fails, which it might, then you will be passing uninitialized data to pthread_join, resulting perhaps in your segmentation fault.

Instead of
> 
```

    for (i=0; i<n; i++ ) { pthread_create( &tid[i], NULL, thread, NULL ); }

```

Try
```

    for (i=0; i<n; i++ ) {
        if (pthread_create( &tid[i], NULL, thread, NULL ) != 0) {
            fprintf(stderr, "pthread_create failed with i = %d. errno = %d, %s\n",
                i, errno, strerror(errno));
            n = i; /* Don't call join with uninitialised data */
            break;
        }
    }

```
On my system the output is: pthread_create failed with i = 32752. errno = 12, Cannot allocate memory

---

### Post by ken18 on 2014-03-13
That was it, thanks!

```
pthread_create failed with i = 32752. errno = 12, Cannot allocate memory
```

Odd that it's the same exact number as yours. Also, I have 6GB of ram, but only 0.26GB was used (via getrusage) when the error occurred. Hmmm, looks like I'll have some fun chasing that one.  I doubt I'll ever need any where close to that many threads, but it bugs me to get errors that don't make sense to me.

Ken

---

