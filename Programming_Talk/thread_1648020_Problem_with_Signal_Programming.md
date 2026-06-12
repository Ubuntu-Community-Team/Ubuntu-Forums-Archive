---
title: "Problem with Signal Programming"
date: 2010-12-18
forum: Programming Talk
---

### Post by NoJamNoMusic on 2010-12-18
Hi

So I have this basic code,

```

#include <stdio.h>
#include <signal.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>

int main(int argc,char *argv[])
{
    pid_t pid;
    
    pid = fork();
    
    if ( !pid ) 
    {
        printf("child %ld",(long)pid);
        printf(": waiting for signal\n");
        pause();
        printf("child: bye\n");
        return;
    }
    
    sleep(3);    // child will run first
    printf("Sending signal to child %ld\n",(long)pid);
    kill( pid, SIGCONT );
    wait( NULL );
    printf("child terminated\n");
}

```

I am using Ubuntu 10.04 and this is programmed in C.

The output is this...

```

child 0: waiting for signal
Sending signal to child 1929

```
and it stucks here.

The problem is either that the parent never sends the signal
or that the child never receives it.

I have read the manuals for kill, kill(2), pause(), I have opened signal.h and confirmed that SIGCONT,SIGSTOP and SIGKILL cannot be ignored.

I am missing something guys, please help me!

---

### Post by johnl on 2010-12-18
I think you need to register a handler for SIGCONT.  It doesn't have to do anything, you just need to register one.

```

#include <stdio.h>
#include <signal.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>

void handler(int signum) 
{
}


int main(int argc,char *argv[])
{
    pid_t pid;

    signal(SIGCONT, handler);
    
    pid = fork();
    
    if ( !pid ) 
    {
        printf("child %ld",(long)pid);
        printf(": waiting for signal\n");
        pause();
        printf("child: bye\n");
        return 0;
    }
    
    sleep(3);    // child will run first
    printf("Sending signal to child %ld\n",(long)pid);
    kill( pid, SIGCONT );
    wait( NULL );
    printf("child terminated\n");
}

```

```

$ ./test 
child 0: waiting for signal
Sending signal to child 4012
child: bye
child terminated

```

It could be because SIGCONT defaults to SIG_IGN (ignore signal) or because catching a signal with the SIG_DFL (default handler) won't wake up a process that called pause().

The pause() man page hints that the second case could be likley:

```

       pause()  causes the calling process (or thread) to sleep until a signal
       is delivered that either [B]terminates the process or causes  the  invoca&#8208;
       tion of a signal-catching function.[/B]

```

Sounds like being caught by the default handler doesn't count as invoking a signal catching function.

---

### Post by Arndt on 2010-12-18
> **NoJamNoMusic said:**
> Hi

So I have this basic code,

```

#include <stdio.h>
#include <signal.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>

int main(int argc,char *argv[])
{
    pid_t pid;
    
    pid = fork();
    
    if ( !pid ) 
    {
        printf("child %ld",(long)pid);
        printf(": waiting for signal\n");
        pause();
        printf("child: bye\n");
        return;
    }
    
    sleep(3);    // child will run first
    printf("Sending signal to child %ld\n",(long)pid);
    kill( pid, SIGCONT );
    wait( NULL );
    printf("child terminated\n");
}

```

I am using Ubuntu 10.04 and this is programmed in C.

The output is this...

```

child 0: waiting for signal
Sending signal to child 1929

```
and it stucks here.

The problem is either that the parent never sends the signal
or that the child never receives it.

I have read the manuals for kill, kill(2), pause(), I have opened signal.h and confirmed that SIGCONT,SIGSTOP and SIGKILL cannot be ignored.

I am missing something guys, please help me!

It may be that SIGCONT is only received by a process when it is actually resumed after having been suspended. Does it work better if you use SIGUSR1, for example?

---

### Post by NoJamNoMusic on 2010-12-18
johnl you are the man!

That's what I was thinking but I didnt know what the solution was.
Your code is working, and thanks for the explanation.
Signal handler invocation is the key word.


Arndt, you the man too!

You are right,because when I try the same code with SIGKILL or SIGSTOP it works fine.
Basically SIGCONT just resumes.

Thanks guys :popcorn:

---

