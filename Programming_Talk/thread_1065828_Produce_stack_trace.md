---
title: "Produce stack trace"
date: 2009-02-10
forum: Programming Talk
---

### Post by JFASI on 2009-02-10
One thing that I really like about Mac OS X is that you can enable the crash reporter to display a stack trace whenever a program crashes. Is there any way to do this in Ubuntu at the console? I am writing an application and I'm seeing strange crashes. 

Normally, I just install libc6-dgb and compile using -g, so that crashes are reported as I like it, but I do not have sufficient privileges on this machine to do so.

---

### Post by johnl on 2009-02-10
Hi,

You can install a signal handler for SIGSEGV to catch segmentation faults in your program.

gcc provides the ability to generate a backtrace with the backtrace() function.

Here's an example I threw together from the gcc documentation.

```

/* 
 * compile with '-rdynamic' to include function names.
 * otherwise you will just get function addresses.
 */
#include <signal.h>
#include <stdlib.h>
#include <stdio.h>
#include <execinfo.h>

void print_trace (void)
{
    void *array[10];
    size_t size;
    char **strings;
    size_t i;

    size = backtrace (array, 10);
    strings = backtrace_symbols (array, size);

    printf ("Obtained %zd stack frames.\n", size);

    for (i = 0; i < size; i++)
        printf ("%s\n", strings[i]);

    free (strings);
}

void handle_segv(int sig)
{
    print_trace();
    exit(-1);
}

/* this will cause a seg fault. */
void dummy_2(void)
{
    int *p;
    while(1) {
        *(p++) = 0xDEADBEEF;
    }
}

/* this function is just to generate more stack frames */
void dummy_1(void)
{
    dummy_2();
}

int main(int argc, char* argv[])
{
    struct sigaction newact;
    struct sigaction oldact;

    newact.sa_handler = handle_segv;
    sigemptyset(&newact.sa_mask);
    newact.sa_flags = 0;

    /* register the SIGSEGV handler */
    int rc = sigaction(SIGSEGV, &newact, &oldact);

    dummy_1();
    return 0;
}

```

Here's the output I got on my system (with -rdynamic):

```

Obtained 8 stack frames.
./test(print_trace+0x16) [0x400a62]
./test(handle_segv+0x10) [0x400ad6]
/lib/libc.so.6 [0x7fb80cddc060]
./test(dummy_2+0x8) [0x400ae8]
./test(dummy_1+0x9) [0x400afe]
./test(main+0x5a) [0x400b5a]
/lib/libc.so.6(__libc_start_main+0xe6) [0x7fb80cdc7466]
./test [0x400989]

```

---

