---
title: "Any way to grab the 'kill'?"
date: 2011-09-09
forum: Programming Talk
---

### Post by hakermania on 2011-09-09
Hello.

Is there any way to grab the 'kill' signal from inside the program so as to do an action before quitting just like there's a way grabbing the Ctrl+C?

I am writing in C++ and using QtCreator, thanks in advance for any answers!):P

---

### Post by karlson on 2011-09-09
> **hakermania said:**
> Hello.

Is there any way to grab the 'kill' signal from inside the program so as to do an action before quitting just like there's a way grabbing the Ctrl+C?

I am writing in C++ and using QtCreator, thanks in advance for any answers!):P

If I recall correctly that is the only one that you can't catch.

---

### Post by lensman3 on 2011-09-09
Look at the signal() function.  It should allow what you want.  You can set up your own signal handlers.

kill -9 is the only one you can't catch in Linux/Unix. The others you can catch.

---

### Post by hakermania on 2011-09-09
> **lensman3 said:**
> Look at the signal() function.  It should allow what you want.  You can set up your own signal handlers.

kill -9 is the only one you can't catch in Linux/Unix. The others you can catch.

Hey, thanks for the info, I'd like to catch the signal that the system sends to application when going e.g. for shutdown...
Any idea what type of signal it is?

---

### Post by karlson on 2011-09-09
> **hakermania said:**
> Hey, thanks for the info, I'd like to catch the signal that the system sends to application when going e.g. for shutdown...
Any idea what type of signal it is?

It sends SIGTERM (15 last I checked)

---

### Post by hakermania on 2011-09-09
> **karlson said:**
> It sends SIGTERM (15 last I checked)
Thanks!

---

### Post by cgroza on 2011-09-09
You may only catch SIGTERM. SIGKILL will terminate your program with cold blood.
As far as I know, "killall" and "kill" send SIGTERM by default.

---

### Post by dwhitney67 on 2011-09-09
> **cgroza said:**
> You may only catch SIGTERM.

As indicated earlier, a program may catch _any_ signal it pleases, with the exception if SIGKILL (9).

---

### Post by dwhitney67 on 2011-09-09
> **lensman3 said:**
> Look at the signal() function.

signal() has been deprecated; sigaction() is the preferred function to use.

For the OP's benefit, to capture SIGINT and SIGTERM:
```

#include <csignal>

class ProgramStatus
{
public:
   ProgramStatus()
   {
      struct sigaction act;
      memset(&act, 0, sizeof(act));

      act.sa_handler = sigHandler;
      sigaction(SIGINT, &act, 0);
      sigaction(SIGTERM, &act, 0);
   }

   bool isDone() { return done; }

private:
   static bool done;

   static void sigHandler(int signo)
   {
      if (signo == SIGINT || signo == SIGTERM)
      {
         done = true;
      }
   }
};

bool ProgramStatus::done = false;

```

---

### Post by Lux Perpetua on 2011-09-09
> **lensman3 said:**
> Look at the signal() function.  It should allow what you want.  You can set up your own signal handlers.

kill -9 is the only one you can't catch in Linux/Unix. The others you can catch.I don't think you can catch SIGSTOP, either, can you?

> **hakermania said:**
> Thanks!Just keep in mind that your process will be killed with SIGKILL eventually anyway if it takes too long saying its goodbyes. ;-)

---

### Post by dwhitney67 on 2011-09-10
> **Lux Perpetua said:**
> I don't think you can catch SIGSTOP, either, can you?

Upon examination of the man-pages for sigaction() and signal(), it seems that you are correct.

It should be noted that the application will not terminate when a SIGSTOP is sent; it will merely be suspended.  A SIGCONT can be used to resume the process, or a SIGKILL can be issued to kill it.  A SIGTERM, and for that fact, any other signal other than SIGKILL, is ignored when the process is suspended, but will be received when/if the process is resumed.

---

