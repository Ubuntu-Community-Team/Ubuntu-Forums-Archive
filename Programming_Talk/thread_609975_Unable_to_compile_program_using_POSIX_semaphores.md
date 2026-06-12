---
title: "Unable to compile program using POSIX semaphores"
date: 2007-11-11
forum: Programming Talk
---

### Post by mmebane on 2007-11-11
I've got Kubuntu Feisty installed and have been using it to do my homework for my Systems Programming class with no problems, up until my current assignment, which is using pthreads.  I've installed libpthread-dev, but am getting linking errors when trying to use semaphores.  I've done a lot of searching, but no luck so far.  Any ideas?  Am I doing something blindingly stupid?

Here's an ultra-bare-bones test case:

```
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <pthread.h>
#include <semaphore.h>

sem_t threadLock;

int main( int argc, char **argv ) {
    sem_init( &threadLock, 0, 1 );

    sem_destroy( &threadLock );

    return 0;
}

```

And I'm trying to build it with:

```
gcc -Wall -lpthread -o semtest semtest.c
```

But I get

```
/tmp/ccQbg9az.o: In function `main':
semtest.c:(.text+0x29): undefined reference to `sem_init'
semtest.c:(.text+0x35): undefined reference to `sem_destroy'
collect2: ld returned 1 exit status
```

---

### Post by LaRoza on 2007-11-11
Do you have to link semaphore also?

---

### Post by j_g on 2007-11-11
Try adding the following includes:

```
#include <sys/types.h>
#include <sys/sem.h>
#include <sys/ipc.h>
#include <sys/shm.h>

```

---

### Post by DMills on 2007-11-11
That is a link time error, and a quick look at the man pages reveals that these are part of the posix realtime library, so try adding -lrt to the end of the compiler options. 

Regards, Dan.

---

### Post by mmebane on 2007-11-11
There is no libsemaphore or anything like it, and adding the headers didn't do anything, but when I add -lrt I get:

```
/usr/bin/ld: warning: libpthread.so.0, needed by /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/librt.so, may conflict with libpthread.so.20
```

So... I removed libpthread20, which in turn removed libpthread-dev, and now everything is working fine, with no need to link against librt.  At least, the following program compiles without a peep and works as expected.  Weird.

```
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <pthread.h>
#include <semaphore.h>

sem_t sem1, sem2;

void *thread1( void *arg ) {
    sem_wait( &sem1 );
    printf( "I'm in thread 1, postin ur semaphores\n" );
    sem_post( &sem2 );

    pthread_exit( NULL );
    return NULL;
}

void *thread2( void *arg ) {
    sem_wait( &sem2 );
    printf( "I'm in thread 2, lol\n" );

    pthread_exit( NULL );
    return NULL;
}



int main( int argc, char **argv ) {
    sem_init( &sem1, 0, 1 );
    sem_init( &sem2, 0, 0 );

    pthread_t threads[ 2 ];

    pthread_create( &threads[ 0 ], NULL, thread2, NULL );
    sleep( 1 );
    pthread_create( &threads[ 1 ], NULL, thread1, NULL );

    pthread_join( threads[ 0 ], NULL );
    pthread_join( threads[ 1 ], NULL );


    sem_destroy( &sem2 );
    sem_destroy( &sem1 );

    return 0;
}
```

---

