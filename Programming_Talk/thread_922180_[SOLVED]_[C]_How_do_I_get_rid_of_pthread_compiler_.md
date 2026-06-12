---
title: "[SOLVED] [C] How do I get rid of pthread compiler warning?"
date: 2008-09-17
forum: Programming Talk
---

### Post by dwhitney67 on 2008-09-17
Here's the code:
[PHP]#include <pthread.h>

int main()
{
  pthread_mutexattr_t attr;

  pthread_mutexattr_init( &attr );
  pthread_mutexattr_setpshared( &attr, PTHREAD_PROCESS_PRIVATE );
  pthread_mutexattr_settype( &attr, PTHREAD_MUTEX_TIMED_NP );

  // ...

  return 0;
}[/PHP]
I am compiling with:
```
gcc -Wall -pedantic -std=gnu99 Prog.c -lpthread
```
I get a warning indicating an implicit declaration of pthread_mutexattr_settype() is being made.

The man-page for pthread_mutexattr_settype() is less than useful.  When I compile a similar program (in C++) using the g++ compiler, I do not get the warning... and in fact I am able to use PTHREAD_MUTEX_DEFAULT, which supplants PTHREAD_MUTEX_TIMED_NP.

---

### Post by WW on 2008-09-17
No solution here, just a possible clue.  On my computer running gutsy, the declaration of the pthread_mutexattr_settype function in pthread.h is inside an #ifdef:
```

#ifdef __USE_UNIX98
...
#endif

```
I get the same error you do when I compile the snippet that you showed, both with and without the option -std=gnu99.

---

### Post by scourge on 2008-09-17
Forget about my previous advice of declaring it yourself (in case you were quick enough to read it). Looks like passing the -D_GNU_SOURCE parameter to gcc solves the problem.

---

### Post by dwhitney67 on 2008-09-17
> **scourge said:**
> Forget about my previous advice of declaring it yourself (in case you were quick enough to read it). Looks like passing the -D_GNU_SOURCE parameter to gcc solves the problem.
Thanks a lot!  How/where did you find out about this little nugget?  I looked through the pthread.h and features.h files (in /usr/include) and the _GNU_SOURCE didn't pop up.  Maybe I must have glanced over it.

P.S.  Btw, I decided to #define _GNU_SOURCE in the source file.  If I had a Makefile, then I would use your suggestion.

---

### Post by scourge on 2008-09-18
> **dwhitney67 said:**
> Thanks a lot!  How/where did you find out about this little nugget?  I looked through the pthread.h and features.h files (in /usr/include) and the _GNU_SOURCE didn't pop up.  Maybe I must have glanced over it.

No problem. It's in features.h:
```

/* If _GNU_SOURCE was defined by the user, turn on all the other features.  */
#ifdef _GNU_SOURCE
# undef  _ISOC99_SOURCE
# define _ISOC99_SOURCE	1
# undef  _POSIX_SOURCE
# define _POSIX_SOURCE	1
# undef  _POSIX_C_SOURCE
# define _POSIX_C_SOURCE	200112L
# undef  _XOPEN_SOURCE
# define _XOPEN_SOURCE	600
# undef  _XOPEN_SOURCE_EXTENDED
# define _XOPEN_SOURCE_EXTENDED	1
# undef	 _LARGEFILE64_SOURCE
# define _LARGEFILE64_SOURCE	1
# undef  _BSD_SOURCE
# define _BSD_SOURCE	1
# undef  _SVID_SOURCE
# define _SVID_SOURCE	1
# undef  _ATFILE_SOURCE
# define _ATFILE_SOURCE	1
#endif

```

If _XOPEN_SOURCE has a value of at least 500, then __USE_UNIX98 will be defined.

---

