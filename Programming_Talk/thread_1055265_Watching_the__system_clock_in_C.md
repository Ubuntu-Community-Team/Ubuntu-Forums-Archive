---
title: "Watching the  system clock in C"
date: 2009-01-30
forum: Programming Talk
---

### Post by spadewarrior on 2009-01-30
Hello.

I am writing a program in which I need a way to continually monitor the system clock and perform a specific function when it reaches a certain value. The problem is that this has to occur independently of other functions and, once started, keep operating until the program terminates.

Does this make sense and does anyone have any ideas, standard C functions or reading materials that they could suggest to help me with this task?

Thanks.

:)

---

### Post by johnl on 2009-01-30
It sounds to me like you might want to register an alarm.

```

#include <signal.h>
#include <stdlib.h>
#include <stdio.h>

void alarm_handler(int sig)
{
    printf("alarm!\n");
    /* queue another alarm signal */
    alarm(5);
}

int main(int argc, char* argv[])
{
    signal(SIGALRM, alarm_handler);

    /* request SIGALRM in 5 seconds */
    alarm(5);

    while(1) {
        printf("sleeping...\n");
        sleep(1);
    }
}

```


Obviously you can base your timing off the current system time, etc.

---

### Post by spadewarrior on 2009-01-31
Thanks, I'll have a look into that :).

---

### Post by spadewarrior on 2009-01-31
Is there a way to pass other variables to the alarm handling function? I can't seem to pass anything other than int sig. Ideally I'd like to pass a pointer to a struct, but I can't work out if this is possible from the man page.  

Would I have to use a seperate process and some kind of volatile variables? I'm getting a bit out of my depth here...

---

### Post by stroyan on 2009-01-31
There is no way to pass additional parameters to alarm() for a signal handler function to use.  It may be possible to have a global data structure that the signal handler would refer to when deciding what to do about an alarm signal.

You do need to be very careful about what you do in a signal handler.  Very few operations are really safe for a signal handler.  Look at the section on "Async-signal-safe functions" inside of the "man 7 signal" manual entry.  It lists the functions that posix standards list as safe to call from signal handlers.

Starting another thread or a separate process may be a better approach for you.  Safe threading can be almost as tricky as working with signal handlers.  A separate process would make interactions with the code in your other functions much more limited.  That makes safe operations easy because it results in few shared resources.  But it would require more explicit communication of any data that the timer-initiated function needs to read or modify in the original program.

---

### Post by spadewarrior on 2009-01-31
OK, thanks I'll check that out.

---

