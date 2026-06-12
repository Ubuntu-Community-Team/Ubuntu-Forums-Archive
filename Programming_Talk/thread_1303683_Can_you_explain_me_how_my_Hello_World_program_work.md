---
title: "Can you explain me how my Hello World program works?"
date: 2009-10-28
forum: Programming Talk
---

### Post by 0xABC123 on 2009-10-28
Hello!

This program (testapp):
```

#include <stdio.h>
#include <stdlib.h>

int number = 5;

void sayhello()
{
    printf( "Hello world!\n" );
}

int main()
{
    sayhello();
    printf( "Number: 0x%x:%d\n", (unsigned)&number, number );
    return EXIT_SUCCESS;
}

```Gives this output:
> 
Hello world!
Number: 0x601028:5
So the memory address of *number* is 0x601028. I tried to write a program which overwrites *number* with something else, and came up with this (test2):
```

#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <sys/ptrace.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <sys/syscall.h>
#include <unistd.h>
#include <errno.h>

int main()
{
    pid_t child = fork();
    char who[8];

    if ( child == 0 )
    {
        strcpy( who, "Child" );
        printf( "Child started\n" );

        ptrace( PTRACE_TRACEME, 0, NULL, NULL );
        int ok = execl( "./bin/testapp", "testapp", NULL );

        if ( ok == -1 )
            fprintf( stderr, "Failed to execute, reason: %s\n", strerror(errno) );
        else
            printf( "Success!\n" );

    }
    else
    {
        strcpy( who, "Parent" );
        printf( "Parent started\n" );

        ptrace( PTRACE_POKEDATA, child, (void*)0x601028, 10 );

        int status = 0;
        waitpid( child, &status, 0 );
    }

    fflush( stdout );
    fflush( stderr );
    printf( "%s returned\n", who );
    return EXIT_SUCCESS;
}

```Sometimes test2 gives this output when I run it in terminal (child started before parent??):
> 
Child started
Parent started
Parent returned
Hello world!
Number: 0x601028:10
And sometimes it gives this output (parent started before child, but number is 5??):
> 
Parent started
Child started
Parent returned
Hello world!
Number: 0x601028:5
Why output isn't always the same? And why it never prints "Success" and "Child returned"? I don't understand.

---

### Post by dwhitney67 on 2009-10-28
One application is not going to be able to affect the memory of another application.  That's the whole purpose of a Memory Mgmt Unit; to prevent an application from stepping over memory that is outside of its program space.

As for the address you are attempting to write to, it is not a physical address, but instead a virtual memory address (or something to that effect).

Anyhow, if you need to write to another app's memory space, consider creating a shared-memory space (that both apps share).

---

### Post by lisati on 2009-10-28
One program isn't usually allowed to access another's memory space (including variables), unless you make special arrangements to do so. The subject of [inter-process communication]("http://en.wikipedia.org/wiki/Inter-process_communication") is a rich one, and involves more than can easily be learned with a simple "hello world" style program.

---

### Post by 0xABC123 on 2009-10-28
> **dwhitney67 said:**
> 
Anyhow, if you need to write to another app's memory space, consider creating a shared-memory space (that both apps share).
> **lisati said:**
> One program isn't usually allowed to access another's memory space (including variables), unless you make special arrangements to do so. The subject of [inter-process communication]("http://en.wikipedia.org/wiki/Inter-process_communication") is a rich one, and involves more than can easily be learned with a simple "hello world" style program.
I don't think that's possible if the other program is a closed-source win32 exe which I run using wine.
[U]
Edit: The original question was, why and how my program does what it does?[/U]

---

### Post by Arndt on 2009-10-28
> **0xABC123 said:**
> I don't think that's possible if the other program is a closed-source win32 exe which I run using wine.
[U]
Edit: The original question was, why and how my program does what it does?[/U]

If an execl succeeds, no code after it will be run. You have replaced the code completely with another program. That's why you don't see Child returned, or Success.

Sometimes the output is 5, and sometimes 10. When it's 5, it's probably because the poke happened before the execl.

---

### Post by 0xABC123 on 2009-10-29
Why doesn't ptrace( PTRACE_TRACEME, 0, NULL, NULL ); halt the execution of HelloWorld thread until it calls execl?

---

### Post by Arndt on 2009-10-29
> **0xABC123 said:**
> Why doesn't ptrace( PTRACE_TRACEME, 0, NULL, NULL ); halt the execution of HelloWorld thread until it calls execl?

How do you mean "halt until"? If you halt it, how does it reach the execl call?

What happens can probably be explained by this: when a process makes a system call, it's eligible for a context switch, and if some other process wants to run, that process is then continued. Since a process could hog the processor indefinitely doing calculations, a context switch also happens after a certain time (second, tenth of second - I don't know). If there were only these two processes running, they would probably run in lock-step, each going to the next system call in each step. But there are many other processes, and one can't really know in which order things happen here, unless there is some explicit synchronization.

---

