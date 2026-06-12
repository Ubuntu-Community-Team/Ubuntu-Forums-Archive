---
title: "problem with pthreads"
date: 2008-02-22
forum: Programming Talk
---

### Post by ninjarat on 2008-02-22
Hey, I'm new here.  And I have a problem.  When trying to compile this code with GCC I get an error that SIG_BLOCK is undefined.  How is this possible?  I have included <pthread.h> and <signal.h>.  Is it a dev package problem? :confused:

The problem snippet is:
```

    sigset_t signal_mask;

    sigemptyset(&signal_mask);
    for (register int i=0; mask_signals[i]; ++i)
    {
        sigaddset(&signal_mask,mask_signals[i]);
    }
	pthread_sigmask(SIG_BLOCK,&signal_mask,NULL);
```
where mask_signals is defined as:
```
static int mask_signals[] =
{
    SIGHUP,SIGINT,SIGQUIT,SIGPIPE,
    SIGALRM,SIGTERM,SIGCHLD,SIGWINCH,
    SIGVTALRM,SIGPROF,0
};
```

Any help would be appreciated!  Thanks. :)

---

### Post by stroyan on 2008-02-22
SIG_BLOCK should be defined when your code includes <signal.h> and signal.h includes /usr/include/bits/sigaction.h.
Perhaps your compilation had earlier warnings about missing header files.
You can ensure you have basic header files with 'sudo apt-get install build-essential'.
You can check exactly what header files are being included using
'gcc -E file.c' or 'gcc -E feat.c | grep ^#' .

---

### Post by ninjarat on 2008-02-22
Thanks!  I did what you said.  It actually didn't work, but I was able to find out what the problem was thanks to that 'gcc -E whatever.c | grep ^#' command you posted.  It was due to the fact that for some reason __USE_POSIX was not defined.  WTF.  Thanks again!  :)

---

### Post by ruy_lopez on 2008-02-22
You can try adding this:

```
gcc -lpthread ... 
```

---

