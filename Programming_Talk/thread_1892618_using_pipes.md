---
title: "using pipes"
date: 2011-12-08
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-12-08
Hi

I'm writing a program which use fork() and I need to read output from child process in parent process

That I did like this:
```

#include <stdio.h>
#include <string.h>
#include <sys/types.h>
#include <stdlib.h>
#include <errno.h>

int  main(void)
{
    int pipefd1[2], pipefd2[2], pipefd3[2];
    pid_t   pid1, pid2, pid3, wait_pid;
    int     status;
    int     i;
    int pipefd[2];

    if(pipe(pipefd1) == -1){
        fprintf(stderr, "Error: %s\n", strerror(errno));
        exit (EXIT_FAILURE);
    }


    char buffer[1024];
    switch(pid1 = fork()){
        case -1: //fail
            fprintf(stderr, "Error: fork 1\n");
            exit(1);
        case 0: //potomok
            close(pipefd1[0]);
            dup2(pipefd1[1], 1);
            dup2(pipefd1[1], 2);

            close(pipefd1[1]);
            fprintf(stdout ,"1. from forked child number: 1\n");
            fprintf(stdout ,"2. from forked child number: 1\n");
            fprintf(stdout ,"3. from forked child number: 1\n");
            exit(0);
            break;
        default:
            close(pipefd1[1]);  // close the write end of the pipe in the parent

            while (read(pipefd1[0], buffer, sizeof(buffer)) > 0){
                printf("%s", buffer);
            }

    }
    wait_pid = wait(&status);
    printf("process: %d ended with %d\n", wait_pid, status);
    exit(0);
}

```and the problem is that it prints some weird characters at the end.

I really don't know what's wrong with it.

The weir output:
```
1. from forked child number: 1
2. from forked child number: 1
3. from forked child number: 1
R&#65533;&#65533;process: 6008 ended with 0
```

---

### Post by karlson on 2011-12-08
after
```

char buffer[1024]

```

do

```

memset(buffer, 0, sizeof(buffer));

```

---

### Post by gmargo on 2011-12-10
> **Mr.Pytagoras said:**
> 
```

            while (read(pipefd1[0], buffer, sizeof(buffer)) > 0){
                printf("%s", buffer);
            }

```

The problem is that the **read()** system call does not null-terminate the input buffer, which **printf(%s)** relies on.  You must pay more attention to the return value from **read()**.

After adding these extra includes (to make the warnings go away - always use gcc's "-Wall" option to find your undeclared functions):
```

#include <unistd.h>
#include <sys/wait.h>

```And this extra variable (for read()'s return code):
```

    ssize_t rc;

```Then you could code the read loop like this:
```

            while (1) {
                /* use sizeof(buffer)-1 to leave space for terminating null */
                rc = read(pipefd1[0], buffer, sizeof(buffer)-1);
                if (rc == -1 && errno == EINTR) {
                    continue;
                }
                if (rc <= 0) {
                    break;
                }
                buffer[rc] = '\0';
                printf("%s", buffer);
            }


```

---

