---
title: "network programming in linux?"
date: 2009-02-18
forum: Programming Talk
---

### Post by tneva82 on 2009-02-18
What's the options for programming network code in Linux? Something similar to directplay but in linux. Especially good if one could use same code in Windows side without too much of a modification.

Or is only option to use TCP/IP directly?

Edit: Oh and language should be C/C++. Not familiar enough with others that I would be crazy enough to try practicing with them just for network code ;-)

---

### Post by the_unforgiven on 2009-02-18
> **tneva82 said:**
> What's the options for programming network code in Linux? Something similar to directplay but in linux. Especially good if one could use same code in Windows side without too much of a modification.

Or is only option to use TCP/IP directly?
From [this wikipedia article]("http://en.wikipedia.org/wiki/DirectPlay"), check the 'External Links' section.

---

### Post by tneva82 on 2009-02-18
thanks. Torque networl library gave whole bunch of errors when I tried compiling(so much for ease of installation :D) but hawkNL seems to have been installed alright so now I'm reading through docs for it.

---

### Post by tneva82 on 2009-02-18
Question: How does one get the hawkNL working? Tried to include it, added simple get version check and tried to compile with all the .o on src folder included in makefile. Still bunch of errors. Specifically:

```

err.o: In function `nlGetError':
err.c:( ) : undefined reference to `pthread_getspecific'
err.c:(): undefined reference to `pthread_key_create'
err.o: In function `nlSetError':
err.c:(): undefined reference to `pthread_setspecific'
err.c:(): undefined reference to `pthread_key_create'
mutex.o: In function `nlMutexInit':
mutex.c:(): undefined reference to `pthread_mutexattr_init'
mutex.c:(): undefined reference to `pthread_mutexattr_settype'
mutex.c:(): undefined reference to `pthread_mutexattr_destroy'
thread.o: In function `nlThreadJoin':
thread.c :(): undefined reference to `pthread_join'
thread.o : In function `nlThreadCreate':
thread.c :(): undefined reference to `pthread_create'
collect2 : ld returned 1 exit status

```

I figure I'm missing .o or two but which ones?

---

### Post by the_unforgiven on 2009-02-18
> **tneva82 said:**
> Question: How does one get the hawkNL working? Tried to include it, added simple get version check and tried to compile with all the .o on src folder included in makefile. Still bunch of errors. Specifically:

```

err.o: In function `nlGetError':
err.c:( ) : undefined reference to `pthread_getspecific'
err.c:(): undefined reference to `pthread_key_create'
err.o: In function `nlSetError':
err.c:(): undefined reference to `pthread_setspecific'
err.c:(): undefined reference to `pthread_key_create'
mutex.o: In function `nlMutexInit':
mutex.c:(): undefined reference to `pthread_mutexattr_init'
mutex.c:(): undefined reference to `pthread_mutexattr_settype'
mutex.c:(): undefined reference to `pthread_mutexattr_destroy'
thread.o: In function `nlThreadJoin':
thread.c :(): undefined reference to `pthread_join'
thread.o : In function `nlThreadCreate':
thread.c :(): undefined reference to `pthread_create'
collect2 : ld returned 1 exit status

```

I figure I'm missing .o or two but which ones?
Looks like you're missing the pthreads library.
Use the **-pthread** option in the Makefile (in CFLAGS/LDFLAGS) while compiling.

---

### Post by tneva82 on 2009-02-18
That fixed it.

Now to wonder why the bloody code doesn't send data to server. No errors whatsoever appear so it seems as if port is opened etc(code borrowed from serverclient.c in sample folder with some modification to get it working in own program. Plus server separated to own program). However no message comes saying client joined nor does data get transfered :-/

There should be good tutorials on this instead of just API and few sample files. Urgh.

---

