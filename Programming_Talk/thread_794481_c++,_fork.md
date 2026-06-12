---
title: "c++, fork"
date: 2008-05-14
forum: Programming Talk
---

### Post by tcarter1980 on 2008-05-14
please can anyone give me example with function "fork()" ?

---

### Post by LaRoza on 2008-05-14
[http://www.space.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/fork.html](http://www.space.unibe.ch/comp_doc/c_manual/C/FUNCTIONS/fork.html)

---

### Post by dempl_dempl on 2008-05-14
[PHP]#include <stdio.h>
#include <unistd.h>
/*
You are free to change my name with yours :)
*/
int main()
{
    printf("Fork example. Brought you by Dushan Savich, also known as dempl_dempl \n");


int pid = fork();

if(pid == 0)
{
     printf("Hello, everybody!  I\'m a child program/process !\n"); 
}
else
{
  printf("Hello, kids!  I\'m a daddy process ! My child's process id [ pid ] is %d\n" , pid);
}

  printf("This one you will see in both programs!! It should be printed twice. Bye!\n");
 
return 0; 
}[/PHP]


Cheers!

---

### Post by gth759k on 2010-04-26
when I try to compile this I get error: 'fork' undeclared (first use of this function). Any suggestions?

---

### Post by dwhitney67 on 2010-04-27
> **gth759k said:**
> when I try to compile this I get error: 'fork' undeclared (first use of this function). Any suggestions?

Yes... post your code, and indicate how you are compiling it.

The code post by dempl_dempl should have provided you with most of the clues necessary to proceed further with your exercise.

---

### Post by Compyx on 2010-04-27
The code in question isn't a very good example though. There's no checking for errors: fork() returns -1 when it fails. And fork() returns a pid_t, not an int, although pid_t might very well be typdef'd to int (and probably is), pid_t is the correct and portable type for the return value of fork().

The title of this thread is also a bit misleading, the code in question smells a lot like C, not C++.

---

### Post by dwhitney67 on 2010-04-27
> **Compyx said:**
> The code in question isn't a very good example though. There's no checking for errors: fork() returns -1 when it fails. And fork() returns a pid_t, not an int, although pid_t might very well be typdef'd to int (and probably is), pid_t is the correct and portable type for the return value of fork().

The title of this thread is also a bit misleading, the code in question smells a lot like C, not C++.

Why did you not just provide a complete/thorough example... as the OP had originally requested?

You were quick to criticize one's efforts, but you offer little more.

If you know of a better way in C++ to fork a new process, other than using fork(), please do let us know.

---

### Post by Compyx on 2010-04-27
Fair enough, how about this:
[php]
/* vim: set et ts=4 sw=4 sts=4 fdm=marker: */

/**
 * @brief   small fork(3) example
 * @author  Bas Wassink <compyx.focus@gmail.com>
 */

#include <stdio.h>      /* needed for printf() and fprintf() */
#include <stdlib.h>     /* needed for EXIT_FAILURE/EXIT_SUCCESS */
#include <string.h>     /* needed for strerror() */
#include <unistd.h>     /* needed for fork() and getpid() */
#include <sys/types.h>  /* needed for pid_t */
#include <errno.h>      /* needed for errno */

int main(void)
{
    pid_t pid;      /* this is used to hold the rerurn value of fork() */

    printf("Parent/only process with pid %d\n", getpid());

    /* attempt to fork
     *
     * fork() is called once, but returns twice: once in the parent and once
     * in the child. fork() returns -1 on error and sets errno (to EAGAIN or
     * ENOMEM).
     */
    pid = fork();

    /* check the return value of fork: three possible outcomes: -1 signals an
     * error, 0 means we're in the child and > 0 means we're in the parent:
     */
    if (pid < 0) {
        /* fork() call failed, report error and exit */
        fprintf(stderr, "%s:%d: fork() call failed with errno %d: %s\n",
                __FILE__, __LINE__, errno, strerror(errno));
        return EXIT_FAILURE;

    } else if (pid == 0) {
        /* pid == 0 means we're in the child process */
        printf("Child code path: my pid is %d\n", (int)getpid());

    } else {
        /* here we're in the parent process, the pid fork() returned is the
         * pid of the child */
        printf("Parent code path: my pid is %d and my child's pid is %d\n",
                (int)getpid(), (int)pid);
    }

    /* this code is shared among parent and child */
    printf("Shared code path: hello, my pid is %d\n", (int)getpid());

    return EXIT_SUCCESS;
}
[/php]

Example run:
```

compyx@aspire7730g:~/tmp$ gcc -Wall -Wextra -pedantic -ansi fork.c 
compyx@aspire7730g:~/tmp$ ./a.out 
Parent/only process with pid 6667
Parent code path: my pid is 6667 and my child's pid is 6668
Shared code path: hello, my pid is 6667
Child code path: my pid is 6668
Shared code path: hello, my pid is 6668
compyx@aspire7730g:~/tmp$ 

```

This is C code of course, not C++, although it compiles fine as C++.

---

### Post by johndpate on 2010-05-26
great reply compyx!  thanks!

---

