---
title: "Strange problem with man pages for Pthreads"
date: 2010-06-26
forum: Programming Talk
---

### Post by codingfreak on 2010-06-26
Hi,

I am using UBUNTU 10.04 and I am facing a strange problem with man pages for pthreads.

I dont find the man page for pthread_create while I see man pages for some of the other pthread related functions. If I give man pthread_ and press tab I see the following output.

```
$ man pthread_
pthread_attr_getaffinity_np     pthread_getaffinity_np
pthread_attr_getguardsize         pthread_getattr_np
pthread_attr_getstack                   pthread_getconcurrency
pthread_attr_getstackaddr         pthread_getcpuclockid
pthread_attr_getstacksize          pthread_setaffinity_np
pthread_attr_setaffinity_np      pthread_setconcurrency
pthread_attr_setguardsize         pthread_setschedprio
pthread_attr_setstack                   pthread_timedjoin_np
pthread_attr_setstackaddr        pthread_tryjoin_np
pthread_attr_setstacksize         pthread_yield
```So how could I install man pages for pthread_create and other ???

At present my man page version is 2.5.7.
> $ man -V
man 2.5.7

---

### Post by mmix on 2010-06-26
I am not on ubuntu now, but this might works, "manpages-dev".

[https://launchpad.net/ubuntu/lucid/i386/manpages-dev/3.23-1](https://launchpad.net/ubuntu/lucid/i386/manpages-dev/3.23-1)

[https://launchpad.net/ubuntu/lucid/amd64/manpages-dev](https://launchpad.net/ubuntu/lucid/amd64/manpages-dev)

---

### Post by Zip247 on 2010-06-26
There is a bug filed on launchpad for this

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/538577](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/538577)

You can possibly look here for help.

[http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_create.3.html](http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_create.3.html)

---

### Post by dwhitney67 on 2010-06-26
Is the package 'manpages-posix-dev' installed on your system?

---

### Post by codingfreak on 2010-06-26
> **dwhitney67 said:**
> Is the package 'manpages-posix-dev' installed on your system?

Hmmm ... seems I dont have the 'manpages-posix-dev' package installed. After installation it solved my problem. But how could they include a small subset of pthread man pages ... and leave out the rest of them :(

---

### Post by monkeyking on 2011-05-29
> **dwhitney67 said:**
> Is the package 'manpages-posix-dev' installed on your system?

Thanks

---

