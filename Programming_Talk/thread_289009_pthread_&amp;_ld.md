---
title: "pthread &amp; ld"
date: 2006-10-30
forum: Programming Talk
---

### Post by alion on 2006-10-30
I'm trying to run simple pthread example:
```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <pthread.h>
#include <ctype.h>
#include <string.h>

void *thread_function(void* arg);

char message[] = "Hello World";

int main()
{
        int res;
        pthread_t a_thread;
        void* thread_result;
        res = pthread_create(&a_thread, NULL, thread_function, (void*)message);
        if( res != 0 )
        {
                perror("Thread creation failed");
                exit(EXIT_FAILURE);
        }
        printf("Waiting for thread to finish...\n");
        res = pthread_join(a_thread, &thread_result);
        if(res != 0)
        {
                perror("Thread join failed");
                exit(EXIT_FAILURE);
        }
        printf("Thread joined, it returned %s\n",(char*) thread_result);
        printf("Message is now %s\n", message);
        exit(EXIT_SUCCESS);
}

```

So, I use the following command to compile it:
```
cc -D_REENTRANT --verbose -I/usr/include/nptl thread1.c -o thread1 -L/usr/lib/nptl  -lpthread
```
and get:

**/usr/bin/ld: cannot find /usr/lib/tls/libpthread_nonshared.a**

There is no /usr/lib/tls directory on my machine at all.
I tried to create it manually and did ln -s on all files from /usr/lib/nptl,
but ld couldn't find libc_nonshared.a file in that case...


My System is: 
Linux desktop 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

Thank you for any help.

---

### Post by ckh on 2006-10-30
1. you should implement thread_function
   ex:
```

void *thread_function(void* arg)
{
	printf("thread_function implement here\n");
}


```

2.I successfully compile it just after remove "-L/usr/lib/nptl" parameter:
```
cc -D_REENTRANT  -I/usr/include/nptl thread1.c -o thread1  -lpthread

```
maybe there are something wrong in it.


hope this helps :)

---

### Post by amo-ej1 on 2006-10-31
```

gcc -Wall -lpthread buh.c 

```

and changing 

```

void *thread_function(void* arg);
[CODE]

to
[CODE]
void *thread_function(void* arg){}

```

already did the trick for me ;) hurray for minimal effort ;)

---

### Post by alion on 2006-10-31
Oooh, I was just too sleepy and overlooked the function implementation :-| . It was in my original file:
```

void *thread_function(void *arg) {
printf(“thread_function is running. Argument was %s\n”, (char *)arg);
sleep(3);
strcpy(message, “Bye!”);
pthread_exit(“Thank you for the CPU time”);
}
```

The point here was really in -L/usr/lib/ntpl option. Something wrong to it. I removed it. And in this case the Linuxthreads (/usr/lib/libpthread.a) library was used, I believe.

I would like to dig sources and take more deep look...

Thank you for your help!

---

### Post by amo-ej1 on 2006-10-31
hmmz,

linuxthread vs nptl is not something you can 'choose'. Use:

```

e@lap:~$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.4

```

to check if your system is using linuxthreads or nptl, but any recent system will be running nptl.

---

