---
title: "How to get/set thread stacksize?"
date: 2009-10-13
forum: Programming Talk
---

### Post by resander on 2009-10-13
I am totally new to threads and want to find the stack size of a thread or default size for all threads, so I am learning and experimenting. Done this so far:

```

#include <stdio.h>
#include <pthread.h>

static void * experiment ( void * a )
   {
   pthread_attr_t tattr;
   size_t size;
   int ret = pthread_attr_getstacksize(&tattr, &size);
   printf ( "a=%d| ret=%d,size=%u\n" , (int)a , ret , size ) ;
   pthread_exit( NULL );
   }

int main( int argc , char * argv[] )
   {
   pthread_t thr;
   int arg = 123 ;
   pthread_create(&thr, NULL, experiment, (void*)arg );
   return 0;
   }

```

It printed:  a=123| ret=0 size=3085774356

The value of size is enormously large. Why? Am I doing this right?

I vaguely remember that default size for processes? is 1MB which would 
be big enough. Certainly not the huge number 308... I got above.

Advice would be most appreciated.

---

### Post by uljanow on 2009-10-13
```
man 3 pthread_attr_setstack
```

I think the default stack size on my machine (x86) is 16MB .

---

### Post by resander on 2009-10-14
Was I doing things right? No, I forgot to give an initial attribute that sets default stack. With this:

```

static void * experiment ( void * a )
   {
   pthread_attr_t tattr;
   int ret = pthread_attr_init ( &tattr ) ;
   size_t size;
   ret = pthread_attr_getstacksize(&tattr, &size);
   printf ( "Get: ret=%d,size=%u\n" , ret , size ) ;

   size = 100000 ;
   ret = pthread_attr_setstacksize(&tattr, size);
   int ret2 = pthread_attr_getstacksize(&tattr, &size);
   printf ( "Set & Get: ret=%d ret2=%d,size=%u\n" , ret , ret2 , size ) ;

   pthread_exit( NULL );
   }

```

I get:

 Get:        ret=0 size=8388608
 Set & Get:  ret=0 ret2=0 size=100000

which shows the default stack for the thread is 8MB and that setstack works.


Uljanow:
Thanks for your input, 16MB on your PC, 8MB measured above and 1MB (for 32-bit Intels) that I read about somewhere (as result of Googling on 'thread stacksize'), so maybe it is always best to measure by getstacksize at runtime if it is important to know.

---

