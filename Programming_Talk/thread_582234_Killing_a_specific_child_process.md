---
title: "Killing a specific child process"
date: 2007-10-19
forum: Programming Talk
---

### Post by ittiam on 2007-10-19
hi,

i am spawning multiple child processes from the same parent. For example my code looks like

```

static pid_t previousChild = -2;
if(condition)
{
    pid = fork();

    if(pid == -1)
       exit(-1);

    if(pid == 0)
    {
       if(previousChild != -2)
          kill(previousChild, SIGTERM);
        ......
        .....
        previousChild = pid;
    }
    else
        waitpid(pid,0,0);
       
}

```

Whenever the kill() is executed it kills the entire process group ie my program is terminated fully and comes back to the prompt. Every time i spawn a new child i want to kill the previous child created.
Also i have a basic doubt, every time we spawn a child we check whether it is equal to zero, but do all child processes  have pid as 0, then how are we to distinguish between different child processes?

---

