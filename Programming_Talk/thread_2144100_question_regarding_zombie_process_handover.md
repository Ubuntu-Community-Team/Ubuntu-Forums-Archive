---
title: "question regarding zombie process handover"
date: 2013-05-11
forum: Programming Talk
---

### Post by IAMTubby on 2013-05-11
I was reading up about zombie process and I did this piece of code to create one.

```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 pid_t pid;

 pid = fork();

 /* parent */
 if(pid)
 {
  sleep(60);
 }
 /* child */
 else
 {
   printf("I'm the child\n");
   exit(0);
 }
}

```
I executed this and on another terminal I was watching the ps output. I could see that for those 60 seconds, the above executable was a zombie, as in, I was getting a.out<defunct>. All good!

[B]But my question is, after 60 seconds,the executable is no longer a zombie process. So who moves it out of the process table, the parent itself or 'init' ?(Note : my parent process is not using 'wait')
[/B]
Please advise.
Thanks

---

### Post by ofnuts on 2013-05-11
The "zombie" state means that the parent hasn't yet collected the result from the child (the process is no longer active but its control structure is kept around in case the parent needs them). So you see the child process as zombie when the parent sleeps. But when the parent exits after waking up from its one-minute sleep, this exits kills all ist child processes whatever their states (running or zombie)

---

