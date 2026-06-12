---
title: "c++ - segfault when using localtime_r"
date: 2009-01-13
forum: Programming Talk
---

### Post by jmartrican on 2009-01-13
Hello,

When I run localtime_r via a function I get a segfault.  I created a small program to demonstrate.  

```

jose@jmart1:~/code$
jose@jmart1:~/code$ cat test_ctime2.cpp
#include <ctime>
#include <sys/time.h>//for gettimeofday and timeval

void get_time(){
        timeval tv;
        tm *timeinfo = 0;
        gettimeofday(&tv, 0);
        //timeinfo = localtime_r (&tv.tv_sec, timeinfo);
        localtime_r (&tv.tv_sec, timeinfo);
}

int main(){
    get_time();
}
jose@jmart1:~/code$
jose@jmart1:~/code$ g++ test_ctime2.cpp
jose@jmart1:~/code$ ./a.out
Segmentation fault (core dumped)
jose@jmart1:~/code$
jose@jmart1:~/code$ cat /proc/version
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008
jose@jmart1:~/code$


```

Does anyone have any ideas what it could be or try to duplicate it?

In case it helps here is the backtrace.  I can't make anything out of it.
```

(gdb) run
Starting program: /home/jose/code/a.out

Program received signal SIGSEGV, Segmentation fault.
0xb7d2e169 in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt
#0  0xb7d2e169 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0x0804a640 in ?? ()
#2  0x00000001 in ?? ()
#3  0xb7f3fff4 in ?? () from /lib/ld-linux.so.2
#4  0x00f40820 in ?? ()
#5  0xbfbc8dc8 in ?? ()
#6  0xbfbc8de4 in ?? ()
#7  0xb7caf2dc in ?? () from /lib/tls/i686/cmov/libc.so.6
#8  0x0804a628 in ?? ()
#9  0xbfbc8dc8 in ?? ()
#10 0x00000000 in ?? ()
(gdb)

```

The backtrace from my real program that I am using it in is more informative in that the localtime_r call is in it.
```

#0  0xb7ca1169 in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt
#0  0xb7ca1169 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0x080b5a20 in ?? ()
#2  0xbf82f7d0 in ?? ()
#3  0xb7effe73 in ?? () from /lib/ld-linux.so.2
#4  0xb7ca0e24 in ?? () from /lib/tls/i686/cmov/libc.so.6
#5  0x496d6662 in ?? ()
#6  0x00000001 in ?? ()
#7  0xbf82f7f0 in ?? ()
#8  0xbf82f7ec in ?? ()
#9  0xb7efbfc0 in ?? () from /lib/ld-linux.so.2
#10 0xb7c9f3ac in localtime_r () from /lib/tls/i686/cmov/libc.so.6
#11 0x0805afe7 in lock_file::lock_file_now () at lock_file.cpp:51
#12 0x080785d6 in main (argc=11, argv=0xbf830294) at jackHammer.cpp:80

```

Thanks!

---

### Post by u-slayer on 2009-01-13
> **jmartrican said:**
> tm *timeinfo = 0;


I'm guessing it has something to do with this, since you can't be passing around a Null Pointer. I changed it to this:

```
tm *timeinfo = new tm;
```

and it ran just fine, It didn't do anything, but it didn't crash at least.

---

### Post by jmartrican on 2009-01-13
u-slayer,

Thanks a lot, that in fact fixed it for the demonstration code.  The only problem is that in my real code the pointer is not set to 0.

```

    //Obtaining test ID
    //...using C time functions for creating test ID
    time_t rawtime;
    tm *timeInfo;
    char testId[80];
    time(&rawtime);
    localtime_r (&rawtime, timeInfo);
    strftime (testId, 80, "%Y%j%H%M%S", timeInfo);
    //Write pid and test ID to lock file
    lockFStream<<getpid()<<"\n"<<testId;
    return string(testId);

```

This is the code that spit out that second backtrace from my first post.

It gets better.  Even without the pointer being set to 0 the problem exists with the demonstration code if you call localtime_r multiple times... example below.

```

jose@jmart1:~/code$ cat test_ctime2.cpp
#include <ctime>
#include <sys/time.h>//for gettimeofday and timeval

void get_time(){
        timeval tv;
        tm *timeinfo;
        gettimeofday(&tv, 0);
        //timeinfo = localtime_r (&tv.tv_sec, timeinfo);
        localtime_r (&tv.tv_sec, timeinfo);
}

int main(){
    for (int i = 0; i < 10; i++)
        get_time();
}

```

---

### Post by WW on 2009-01-14
You haven't allocated the memory for the result of localtime_r.  Take a look at the man page for localtime_r and related functions.  When you use the *_r variant, you must provide the memory for the result; that is, the second argument must point to an actual instance of a struct tm.  Try making timeInfo an instance of a tm instead of a pointer to one, e.g.:
```

    //Obtaining test ID
    //...using C time functions for creating test ID
    time_t rawtime;
    tm timeInfo;
    char testId[80];
    time(&rawtime);
    localtime_r (&rawtime, &timeInfo);
    strftime (testId, 80, "%Y%j%H%M%S", &timeInfo);

```

---

### Post by jmartrican on 2009-01-14
WW,

That did it.  Thanks a lot!

---

