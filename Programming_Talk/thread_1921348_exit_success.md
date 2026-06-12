---
title: "exit success"
date: 2012-02-06
forum: Programming Talk
---

### Post by conradin on 2012-02-06
Hi Everyone!
I am looking at an example for pipe from man 2 pipe. 
there are two versions of exit success, with no apparent distinction between them, and gcc thinks its legit, but Im currious. What is the difference between:
               _exit(EXIT_SUCCESS);
and
               exit(EXIT_SUCCESS);
?
the source:
```


       #include <sys/wait.h>
       #include <stdio.h>
       #include <stdlib.h>
       #include <unistd.h>
       #include <string.h>

       int
       main(int argc, char *argv[])
       {
           int pipefd[2];
           pid_t cpid;
           char buf;

           if (argc != 2) {
            fprintf(stderr, "Usage: %s <string>\n", argv[0]);
            exit(EXIT_FAILURE);
           }

           if (pipe(pipefd) == -1) {
               perror("pipe");
               exit(EXIT_FAILURE);
           }

           cpid = fork();
           printf("the clone PID %d cpid\n ", cpid);
           if (cpid == -1) {
               perror("fork");
               exit(EXIT_FAILURE);
           }

           if (cpid == 0) {    		/* Child reads from pipe */
               close(pipefd[1]);    /* Close unused write end */

               while (read(pipefd[0], &buf, 1) > 0)
                   write(STDOUT_FILENO, &buf, 1);
				
               write(STDOUT_FILENO, "\n", 1);
               close(pipefd[0]);
               _exit(EXIT_SUCCESS);

           } else {            /* Parent writes argv[1] to pipe */
               close(pipefd[0]);          /* Close unused read end */
               write(pipefd[1], argv[1], strlen(argv[1]));
               close(pipefd[1]);          /* Reader will see EOF */
               wait(NULL);                /* Wait for child */
               exit(EXIT_SUCCESS);
           }
       }

```

---

### Post by MadCow108 on 2012-02-06
man exit:
> The  function  _exit()  is  like  exit(3), but does not call any functions registered with atexit(3) or on_exit(3)

---

### Post by Arndt on 2012-02-06
> **MadCow108 said:**
> man exit:

Is _exit in the C standard?

---

### Post by MadCow108 on 2012-02-06
_exit not, but the equivalent _Exit
man _exit
> CONFORMING TO
SVr4, POSIX.1-2001, 4.3BSD.  The function _Exit() was introduced by C99.

---

### Post by Arndt on 2012-02-06
> **MadCow108 said:**
> _exit not, but the equivalent _Exit
man _exit

Do you happen to know why they introduced a new name?

---

### Post by trent.josephsen on 2012-02-06
Names beginning with an underscore are reserved for file scope identifiers, UNLESS the second character is another underscore or a capital letter, in which case it is reserved unconditionally (section 7.1.3 in C99).  Introducing a new standard feature _exit would have broken any earlier code that used that name as a file scope identifier.

They do the same thing with _Bool, _Complex, ... I can't think of any others off the top of my head but I'm sure there are a few.

---

