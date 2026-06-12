---
title: "problems with time.h and Type Field 'tv_nsec' could not be resolved"
date: 2011-08-29
forum: Programming Talk
---

### Post by Uk Meterman on 2011-08-29
Hi,
I am using some source code that uses the time fields tv_nsec and tv_sec and can't resolve them. Time.h is included and on further inspection it seems that there are two forms of the time fields depending on if __use_gnu or __use_bsd is defined. What is the correct way to set the #defines to use the gnu form of time.h?

Thanks

---

### Post by Bachstelze on 2011-08-29
Try compiling with -std=gnu99.

---

### Post by Uk Meterman on 2011-08-29
Hi,
I am still haveing the same problem even with -std=gnu99
```

gcc -E -P -v -std=gnu99 -dD /media/local_data/modbus_project/workspace/.metadata/.plugins/org.eclipse.cdt.make.core/specs.c 
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=x86_64-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/x86_64-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/x86_64-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu

```The problem code is 
```


int _sleep_and_flush(modbus_t *ctx)
{
#ifdef _WIN32
    /* usleep doesn't exist on Windows */
    Sleep((ctx->response_timeout.tv_sec * 1000) +
          (ctx->response_timeout.tv_usec / 1000));
#else
    /* usleep source code */
    struct timespec request, remaining;
    request.tv_sec = ctx->response_timeout.tv_sec;   //field tv_sec not defined
    request.tv_nsec = ((long int)ctx->response_timeout.tv_usec % 1000000) // field tv_nsec
        * 1000;
    while (nanosleep(&request, &remaining) == -1 && errno == EINTR)
        request = remaining;
#endif
    return modbus_flush(ctx);
}

```Thanks

---

### Post by Bachstelze on 2011-08-29
And what exactly is the error?

---

### Post by Uk Meterman on 2011-08-29
Hi, 
The error is for the two lines indicated and is as shown
```


Description    Resource    Path    Location    Type
Field 'tv_nsec' could not be resolved    modbus.c    /libmodbus-3.0.1/src    line 110    Semantic Error
Field 'tv_sec' could not be resolved    modbus.c    /libmodbus-3.0.1/src    line 109    Semantic Error

```

Thanks

---

### Post by Bachstelze on 2011-08-29
You are using a build system I am not familiar with, so I don't know what those errors are supposed to mean. Compiling libmodbus with ./configure and make works fine here.

---

### Post by dwhitney67 on 2011-08-29
In lieu of including <time.h>, try including <sys/time.h>.

---

### Post by Bachstelze on 2011-08-29
> **dwhitney67 said:**
> In lieu of including <time.h>, try including <sys/time.h>.

The program in question has a ./configure script that should take care of all this. I don't know why OP is trying to compile it in another way...

---

### Post by Uk Meterman on 2011-08-29
Hi,
I am trying to import the project into Eclipse, and somehow the #define __USE_GNU  is NOT set how do i correct this?

Thanks

---

### Post by dwhitney67 on 2011-08-29
> **Bachstelze said:**
> The program in question has a ./configure script that should take care of all this. I don't know why OP is trying to compile it in another way...

I merely took the code snip he posted earlier, and compiled it using gcc.

```

#include <sys/time.h>
#include <errno.h>

typedef struct
{
   struct timeval response_timeout;
} modbus_t;

int _sleep_and_flush(modbus_t *ctx)
{
#ifdef _WIN32
    /* usleep doesn't exist on Windows */
    Sleep((ctx->response_timeout.tv_sec * 1000) +
          (ctx->response_timeout.tv_usec / 1000));
#else
    /* usleep source code */
    struct timespec request, remaining;
    request.tv_sec = ctx->response_timeout.tv_sec;   //field tv_sec not defined
    request.tv_nsec = ((long int)ctx->response_timeout.tv_usec % 1000000) // field tv_nsec
        * 1000;
    while (nanosleep(&request, &remaining) == -1 && errno == EINTR)
        request = remaining;
#endif
    return modbus_flush(ctx);
}

```
```

gcc -c snip.c

```


P.S.  These macros are available in sys/time.h if __USE_GNU is defined. 
```

#ifdef __USE_GNU
/* Macros for converting between `struct timeval' and `struct timespec'.  */
# define TIMEVAL_TO_TIMESPEC(tv, ts) {                                   \
        (ts)->tv_sec = (tv)->tv_sec;                                    \
        (ts)->tv_nsec = (tv)->tv_usec * 1000;                           \
}
# define TIMESPEC_TO_TIMEVAL(tv, ts) {                                   \
        (tv)->tv_sec = (ts)->tv_sec;                                    \
        (tv)->tv_usec = (ts)->tv_nsec / 1000;                           \
}
#endif

```

---

### Post by Uk Meterman on 2011-08-29
Hi,
All sorted, just re imported the project with Linux GCC selected as the tool chain and it now works fine.

---

