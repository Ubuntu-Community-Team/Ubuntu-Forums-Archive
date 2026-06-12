---
title: "start a process"
date: 2012-08-20
forum: Programming Talk
---

### Post by conradin on 2012-08-20
Hi all, 
I want to start a process that will return when I use the ps command, in such a way that I can name the process, and have it running, when ps looks for it. I tried writing a script that doesn't close, and a c program that sleeps for a while, but those didn't work. I just want to be able to name the process and let it "run" while its doing nothing. 
What is an easy way to get that done?

---

### Post by trent.josephsen on 2012-08-20
What do you mean by "didn't work"? What specifically did you try?

---

### Post by conradin on 2012-08-25
Looking more in depth, I saw fork() and clone() system calls. Then i saw wait() and a niffty example in the man wait pages, the program I can recompile to run as any process name I need. Its not a bash script, but I only need to name the process Vnmr so my script can find it. 
solved!


```
#include <sys/wait.h>
#include <stdlib.h>
#include <unistd.h>
#include <stdio.h>

int main(int argc, char *argv[])
{
      pid_t cpid, w;
      int status;
      cpid = fork();
      if (cpid == -1) 
           {
               perror("fork");
               exit(EXIT_FAILURE);
           }

           if (cpid == 0)       /* Code executed by child */
           {
               printf("Child PID is %ld\n", (long) getpid());
               if (argc == 1)
                   pause();                    /* Wait for signals */
               _exit(atoi(argv[1]));

           } else                   /* Code executed by parent */
           {  
               do {
                   w = waitpid(cpid, &status, WUNTRACED | WCONTINUED);
                   if (w == -1) 
                   {
                       perror("waitpid");
                       exit(EXIT_FAILURE);
                   }

                   if (WIFEXITED(status)) 
                   {
                       printf("exited, status=%d\n", WEXITSTATUS(status));
                   } else if (WIFSIGNALED(status)) 
                   {
                       printf("killed by signal %d\n", WTERMSIG(status));
                   } else if (WIFSTOPPED(status)) 
                   {
                       printf("stopped by signal %d\n", WSTOPSIG(status));
                   } else if (WIFCONTINUED(status)) 
                   {
                       printf("continued\n");
                   }
               } while (!WIFEXITED(status) && !WIFSIGNALED(status));
               exit(EXIT_SUCCESS);
           }
}
```

---

### Post by ofnuts on 2012-08-26
> **conradin said:**
> Hi all, 
I want to start a process that will return when I use the ps command, in such a way that I can name the process, and have it running, when ps looks for it. I tried writing a script that doesn't close, and a c program that sleeps for a while, but those didn't work. I just want to be able to name the process and let it "run" while its doing nothing. 
What is an easy way to get that done?
It's not too clear whether you expect this process to be started from a script or  a C program... If the process is meant to run indefinitely you can't merely start it from any process or script since exiting these processes will kill their children. 

One way to have them stay around is to use the "nohup" command to start them.

I'm not too expert in this but I think there are ways to ask you desktop manager to start the process (so that it lives as long as your login session, since it becomes a child of your main session process).

---

