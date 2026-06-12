---
title: "C libraries problem!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by fredscripts on 2008-05-01
Hi!!

I'm trying to run this simple C code to get into threading:

```
#include <pthread.h>
#include <stdio.h>

void func(void) {
	printf("Thread %d\n", (int)pthread_self());
	pthread_exit(0);
}
int main(void) {
	pthread_t th1,th2;
	pthread_create(&th1,NULL,(void *)func,NULL);
	pthread_create(&th2,NULL,(void *)func,NULL);
	printf("El thread principal continua ejecutando\n");
	pthread_join(th1,NULL);
	pthread_join(th2,NULL);
	
	return 0;
}
```

It's called simplethread.c

Then I compile:
```

gcc -c simplethread.c -O -Wall
```

Everything perfect till I try to mount it to get and executable:
```

$ gcc simplethread.o -o simplethread
simplethread.o: In function `main':
simplethread.c:(.text+0x30): undefined reference to `pthread_create'
simplethread.c:(.text+0x53): undefined reference to `pthread_create'
simplethread.c:(.text+0x72): undefined reference to `pthread_join'
simplethread.c:(.text+0x85): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
$

```

I can't understand why appears this error on mounting time, because I've copied and pasted the code from an Operating Systems book.

I've already run sudo apt-get install build-essential. So anyone can help me finding how I can manage to get threading working??

Thank you very much!!!!!

---

### Post by fredscripts on 2008-05-01
Oh!! I managed to solve it, was just a newbie error,

on mounting I must run:

gcc simplethread.o -o simplethread -lpthread


Sorry for posting without googling a little before!!!

---

