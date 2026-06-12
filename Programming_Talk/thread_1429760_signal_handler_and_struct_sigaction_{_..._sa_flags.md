---
title: "signal handler and struct sigaction { ... sa_flags }"
date: 2010-03-14
forum: Programming Talk
---

### Post by cybo on 2010-03-14
i'm trying to implement a signal handler for one of the signals. for this i need sigaction function, which uses a struct sigaction. one of the fields in this structure is sa_flags. this field can be set to a lot of different values. the signal handler will behave differently depending on the setting of the sa_flags. however i don't need to modify the behavior of the signal handler, i just need to do "stuff" when the signal arrives. so what the sa_flags should be set to?

below are values that sa_flags can take (documentation from [http://www.kernel.org/doc/man-pages/online/pages/man2/sigaction.2.html):](http://www.kernel.org/doc/man-pages/online/pages/man2/sigaction.2.html):)

sa_flags specifies a set of flags which modify the behavior of the signal.  It
       is formed by the bitwise OR of zero or more of the following:

           SA_NOCLDSTOP
                  If signum is SIGCHLD, do not receive notification when child
                  processes stop (i.e., when they receive one of SIGSTOP, SIGTSTP,
                  SIGTTIN or SIGTTOU) or resume (i.e., they receive SIGCONT) (see
                  wait(2)).  This flag is only meaningful when establishing a handler
                  for SIGCHLD.

           SA_NOCLDWAIT (Since Linux 2.6)
                  If signum is SIGCHLD, do not transform children into zombies when
                  they terminate.  See also waitpid(2).  This flag is only meaningful
                  when establishing a handler for SIGCHLD, or when setting that
                  signal's disposition to SIG_DFL.

                  If the SA_NOCLDWAIT flag is set when establishing a handler for
                  SIGCHLD, POSIX.1 leaves it unspecified whether a SIGCHLD signal is
                  generated when a child process terminates.  On Linux, a SIGCHLD
                  signal is generated in this case; on some other implementations, it
                  is not.

           SA_NODEFER
                  Do not prevent the signal from being received from within its own
                  signal handler.  This flag is only meaningful when establishing a
                  signal handler.  SA_NOMASK is an obsolete, nonstandard synonym for
                  this flag.

           SA_ONSTACK
                  Call the signal handler on an alternate signal stack provided by
                  sigaltstack(2).  If an alternate stack is not available, the
                  default stack will be used.  This flag is only meaningful when
                  establishing a signal handler.

           SA_RESETHAND
                  Restore the signal action to the default state once the signal
                  handler has been called.  This flag is only meaningful when
                  establishing a signal handler.  SA_ONESHOT is an obsolete,
                  nonstandard synonym for this flag.

           SA_RESTART
                  Provide behavior compatible with BSD signal semantics by making
                  certain system calls restartable across signals.  This flag is only
                  meaningful when establishing a signal handler.  See signal(7) for a
                  discussion of system call restarting.

           SA_SIGINFO (since Linux 2.2)
                  The signal handler takes 3 arguments, not one.  In this case,
                  sa_sigaction should be set instead of sa_handler.  This flag is
                  only meaningful when establishing a signal handler.

---

### Post by ebichete on 2010-03-14
If your needs are simple, use "signal()" instead of "sigaction()".
Here is a code fragment that shows how to catch SIGINT:

```
#include <signal.h>

void my_handler (int signum)
{
  /* do stuff */
}

int main (void)
{
  …
  if (signal (SIGINT, my_handler) == SIG_IGN)
    signal (SIGINT, SIG_IGN);
  …
}

```

---

### Post by dwhitney67 on 2010-03-14
Wrt signal():
```

The only portable use of signal() is to set a signal's disposition to SIG_DFL or  SIG_IGN.
The  semantics  when using signal() to establish a signal handler vary across systems (and
POSIX.1 explicitly permits this variation); do not use it for this purpose.

POSIX.1 solved the portability mess by specifying sigaction(2),  which  provides  explicit
control  of  the semantics when a signal handler is invoked; use that interface instead of
signal().

```

When using sigaction(), the format for a simple signal delivery is something like:
```

void sigHandler(int signo)
{
   ...
}

...

struct sigaction sigact;

sigemptyset(&sigact.sa_mask);

sigact.sa_flags   = SA_SIGINFO;
sigact.sa_handler = myHandler;

sigaction(SIGINT, &sigact, 0);

...

```
The man-pages describe each of these functions is good detail; IMO, there really is no need to query for information on the forum.

---

### Post by cybo on 2010-03-14
> **dwhitney67 said:**
> Wrt signal():
```

The only portable use of signal() is to set a signal's disposition to SIG_DFL or  SIG_IGN.
The  semantics  when using signal() to establish a signal handler vary across systems (and
POSIX.1 explicitly permits this variation); do not use it for this purpose.

POSIX.1 solved the portability mess by specifying sigaction(2),  which  provides  explicit
control  of  the semantics when a signal handler is invoked; use that interface instead of
signal().

```

When using sigaction(), the format for a simple signal delivery is something like:
```

void sigHandler(int signo)
{
   ...
}

...

struct sigaction sigact;

sigemptyset(&sigact.sa_mask);

sigact.sa_flags   = SA_SIGINFO;
sigact.sa_handler = myHandler;

sigaction(SIGINT, &sigact, 0);

...

```
The man-pages describe each of these functions is good detail; IMO, there really is no need to query for information on the forum.

i read the documentation and was unclear how to setup the signal handler that's why i asked the question on the forum. in the setup you gave the signal handler must take three arguments (because of sigact.sa_flags = SA_SIGINFO). so what if i want only one argument for my signal handler? what the sigaction.sa_flags should be set to?

---

### Post by dwhitney67 on 2010-03-14
> **cybo said:**
> in the setup you gave the signal handler must take three arguments (because of sigact.sa_flags = SA_SIGINFO). so what if i want only one argument for my signal handler? what the sigaction.sa_flags should be set to?
You lost me with this one!  You really must be confused.

The signal handler is defined with only one parameter; look at the code I provided earlier.

The sigaction(), which btw is *not* the handler, does take three parameters to set it up.  These are:

1. signal id
2. new sigaction struct
3. old sigaction struct (optional)


P.S.  Just play with this code, for I realize I had a typo in the code I presented earlier; I specified the incorrect signal handler name.
```

#include <signal.h>
#include <unistd.h>
#include <stdio.h>

int done = 0;

void sigHandler(int signo)
{
   if (signo == SIGINT)
   {
      done = 1;
   }
}

int main(void)
{
   struct sigaction sigact;

   sigemptyset(&sigact.sa_mask);

   sigact.sa_flags   = SA_SIGINFO;
   sigact.sa_handler = sigHandler;

   sigaction(SIGINT, &sigact, 0);

   printf("Press ctrl-c to quit...\n");

   while (!done) sleep(1);

   printf("all done!\n");

   return 0;
}

```

---

### Post by cybo on 2010-03-14
@dwhitney67

here is what the documentation says about the SA_SIGINFO:

> SA_SIGINFO (since Linux 2.2)
The signal handler takes 3 arguments, not one. In this case,
sa_sigaction should be set instead of sa_handler. This flag is
only meaningful when establishing a signal handler.

if i'm reading the documentation correctly, when sa_flags = SA_SIGINFO, then instead of setting sa_handler in the struct sigaction, i need to set sa_sigaction. sa_handler is a function pointer to a function which takes only one parameter, but sa_sigaction is a function pointer to a function which takes 3 parameters. 
```

struct sigaction {
  void     (*sa_handler)(int);
  void     (*sa_sigaction)(int, siginfo_t *, void *);
  sigset_t   sa_mask;
  int        sa_flags;
  void     (*sa_restorer)(void);
};

```

you can't set them both becasue sa_handler and sa_sigaction are a union.

so the question still stands: what sa_flags should be set to if i want to call handler with only one parameter without modifying function or signal behavior?

---

### Post by soltanis on 2010-03-15
> **cybo said:**
> @dwhitney67
if i'm reading the documentation correctly, when sa_flags = SA_SIGINFO, then instead of setting sa_handler in the struct sigaction, i need to set sa_sigaction. sa_handler is a function pointer to a function which takes only one parameter, but sa_sigaction is a function pointer to a function which takes 3 parameters. 


Correct so far.

> 
you can't set them both becasue sa_handler and sa_sigaction are a union.


Somewhere in the code block you got lost, because you should only be setting one of them. Namely sa_sigaction, if you set sa_flags = SA_SIGINFO.

> 
so the question still stands: what sa_flags should be set to if i want to call handler with only one parameter without modifying function or signal behavior?
Oh this was your question?

Well...what behavior do you want to modify? Because for most signals I can think you'd want to alter (INT, TERM, HUP, USR1, USR2, CHLD) the default action is either do nothing or exit. Only the stop/resume signals have any meaningful actions; do you want to alter these?

EDIT:
In the case that you wanted to alter those signals, then your best bet from what I can think of is setting sa_flags = SA_RESETHAND, which resets the signal to the default handler, then send your process the signal again. Unless there is some UNIX black magic I know not of.

---

### Post by dwhitney67 on 2010-03-15
> **cybo said:**
> @dwhitney67

here is what the documentation says about the SA_SIGINFO:



if i'm reading the documentation correctly...
You are reading it correctly; however whether you specify the single-parameter or the three-parameter signal handler, each will work for SA_SIGINFO.

Did you not test the sample app I provided?

Anyhow, I must ask... why do you care so much about using only the one-parameter signal handler?  Do you have a need for this, or are you just learning about Linux system internals?

If you want to use a 3-parameter signal handler, replace within the code I provided earlier the following:
```

...

void sigHandler2(int signo, siginfo_t* info, void* unused)
{
   if (signo == SIGINT)
   {
      done = 1;
   }
}

int main(void)
{
   ...

   //sigact.sa_handler = sigHandler;
   sigact.sa_sigaction = sigHandler2;

   ...
}

```

---

### Post by cybo on 2010-03-15
@soltanis
> Oh this was your question?

Well...what behavior do you want to modify? Because for most signals I can think you'd want to alter (INT, TERM, HUP, USR1, USR2, CHLD) the default action is either do nothing or exit. Only the stop/resume signals have any meaningful actions; do you want to alter these?

EDIT:
In the case that you wanted to alter those signals, then your best bet from what I can think of is setting sa_flags = SA_RESETHAND, which resets the signal to the default handler, then send your process the signal again. Unless there is some UNIX black magic I know not of.

i don't need to modify the signal behavior. i just want to call the same signal handler every time there is a signal generated. as far as i understand from the documentation SA_RESETHAND is equivalent to one-shot, meaning that the handler will be called only once (at least that what i understand from reading the documentation). what if my signal is periodic, say SIGVTALRM, and i want my handler to be called every time the signal arrives?

---

### Post by cybo on 2010-03-15
@dwhitney67
> Anyhow, I must ask... why do you care so much about using only the one-parameter signal handler? Do you have a need for this, or are you just learning about Linux system internals?

it is both actually. it is a requirement for the code i'm writing and i'm learning about the Linux system internals.

---

### Post by cybo on 2010-03-15
@dwhitney67

i did try the code with sa_flags = SA_SIGINFO and it worked whith the signal handler accepting only one parameter. it somewhat confusing since documentation says that the handler must have 3 parameters. but here is even more confusing part, the code also worked with sa_flags = 0. does anybody know why?

---

### Post by dwhitney67 on 2010-03-15
> **cybo said:**
> 
it is a requirement for the code i'm writing...

It seems like you are working on a 'homework' assignment.

---

### Post by cybo on 2010-03-15
> **dwhitney67 said:**
> It seems like you are working on a 'homework' assignment.

it is a part of homework assignment but i'm not trying to get the solution. in fact i'm not interested in the solution, since i already almost figured it out and the code works with sa_flags = SA_SIGINFO. i'm more interested in why it works with sa_flags = SA_SIGINFO. documentation says that the signal handler must take 3 parameters but the code works when signal handler takes only one. is it an error in the documentation? if yes then it needs to be fixed. it is also unclear why the code works with sa_flags = 0.

---

