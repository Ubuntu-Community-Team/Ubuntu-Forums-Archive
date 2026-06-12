---
title: "pthread problems"
date: 2006-09-09
forum: Programming Talk
---

### Post by Grey on 2006-09-09
Okay, I am having a great deal of difficulty doing something as simple as two threads.  In the interests of resolving this problem once and for all, I have created the absolute simplest threaded program I can possibly make.  It still segfaults.

```

#include <stdio.h>
#include <pthread.h>

void* snd_player(void* popcode) {
	printf("snd player created\n");
	pthread_exit(NULL);
}

void* snd_controller(void* copcode) {
	printf("snd controller created\n");
	pthread_exit(NULL);
}

int main() {
	pthread_t* sc;
	pthread_t* sp;
	
	pthread_create(sc, NULL, snd_controller, NULL);
	printf("first thread created\n");
	pthread_create(sp, NULL, snd_player, NULL);
	printf("second thread created\n");
	while(1);
}

```

The result I get from compiling this (gcc -Wall -pthread -o thread thread.c) gives me this result:

```

first thread created
Segmentation fault (core dumped)

```

This is absolutely driving me out of my mind.  My main dev box is running Edgy, but I have also tried this on Dapper, with the same result... (which really irritates me, as my dev box was running Dapper not so long ago, and something similar was working just fine).

I have also tried creating the threads as detached... with no luck.

---

### Post by toojays on 2006-09-09
Your variables sc and sp are not initialised. I think if you added "-W -O2" to your list of arguments to gcc, it would have warned you about this.

---

### Post by Grey on 2006-09-09
Thank you.  I feel stupid now.  The tutorial on pthreads I was following didn't seem to mention that.  I had assumed that pthread_create would allocate space for it.  Guess I know better now.

---

