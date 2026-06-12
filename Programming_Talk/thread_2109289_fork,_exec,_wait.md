---
title: "fork, exec, wait"
date: 2013-01-27
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-27
I have a couple of questions in the code below which is about fork, exec and wait. 

```

#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <unistd.h>
#include <sys/wait.h>

int main( int argc, char *argv[], char *env[] )
{
   pid_t my_pid, parent_pid, child_pid;
   int status;

   child_pid = fork();

   if(child_pid == 0)
   {  printf("\nChild: I am a new-born process!");
      my_pid = getpid();    parent_pid = getppid();
      printf("Child: my pid is: %d", my_pid);
      printf("Child: my parent's pid is: %d", parent_pid);
      printf("Child: I will sleep 3 seconds and then execute - date - command \n\n");

      sleep(3); 
      printf("Child: Now, I woke up and am executing date command ");
      execl("/bin/date", "date", NULL);
      perror("execl() failure!");

      printf("This print is after execl() and should not have been executed if execl were successful! \n\n");

      _exit(1);
   }
/*
 * parent process
 */
   else
   {
      printf("\nParent: I created a child process.");
      printf("Parent: my child's pid is: %d", child_pid);
      printf("\nthis is the line before wait\n\n");
      wait(&status); /* can use wait(NULL) since exit status
                        from child is not used. */
      printf("\nthis is the line after wait ");
      printf("\n Parent: my child is dead. I am going to leave.\n \n ");
   }

   return 0;
}

```

1.Why is it that when this code executes, always the parent's part is executed first and then the child. Shouldn't that be random ? Or is it just a coincidence for me that **always** the parent part executes first ?

2.We are using **wait(&status)** to see if the child has finished executing. But we are not changing the value of 'status ' anywhere in the program. Shouldn't the return value of _exit(1) from the child process should be saved in status. But none of the resources I saw had any mention of this.

---

### Post by MadCow108 on 2013-01-27
1. forking and changing context takes a while, your program is so short it will almost always run until the wait before the child even starts up or gets a cpu slice.

2. wait stores the status of the child into *status*, so it is unset until the wait call.
if WIFEXITED(status) is true it will contain the exitcode from _exit(..) (via WEXITSTATUS)
see the manpage for an example of its usage.

---

### Post by IAMTubby on 2013-01-27
> **MadCow108 said:**
> 1. forking and changing context takes a while, your program is so short it will almost always run until the wait before the child even starts up or gets a cpu slice.
Thanks for the reply MadCow108.

So does the parent execute first upon successful fork ?
I'm trying to understand if there is a fixed order for who executes first, or is it just decided randomly, but that process keeps executing until a sleep or wait occurs ?

I have 2 problems with this code I have written.
```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
 pid_t pid;
 int status=0;

 pid = fork();

 if(pid == 0)
 {
  printf("\nchild : before calling sleep");
  sleep(3);
  printf("\nchild : after calling sleep");
  _exit(1);
 }
 else
 {
  printf("\nparent: before calling wait");
  wait(&status);
  printf("\nparent: after calling wait");
 }


 return 0;
}

```

[b]
output
<sleeping 1>
<sleeping 2>
<sleeping 3>
child : before calling sleep
parent: before calling wait
parent: after calling wait
[/b]
a.It's the child that **always** executes first.
b.This line after the child wakes up is never printed.(*printf("\nchild : after calling sleep");*)

> 
2. wait stores the status of the child into *status*, so it is unset until the wait call.
if WIFEXITED(status) is true it will contain the exitcode from _exit(..) (via WEXITSTATUS)
see the manpage for an example of its usage.
Shall read up on this Sir.

Thanks

---

### Post by ofnuts on 2013-01-27
> **IAMTubby said:**
> Thanks for the reply MadCow108.

So does the parent execute first upon successful fork ?
I'm trying to understand if there is a fixed order for who executes first, or is it just decided randomly, but that process keeps executing until a sleep or wait occurs ?

I have 2 problems with this code I have written.
[B]output
<sleeping 1>
<sleeping 2>
<sleeping 3>
child : before calling sleep
parent: before calling wait
parent: after calling wait
[/B]
a.It's the child that **always** executes first.
b.This line after the child wakes up is never printed.(*printf("\nchild : after calling sleep");*)


Shall read up on this Sir.

Thanks
You can never be sure if execution order, even if the parent is more likely to execute first (but anything could make it wait, even the printf() after starting the child).

Your missing line is likely due to exiting without flushing buffers. When the output is to a terminal, printf()  flushes the output buffer when it sees a "\n". If you take the habit of putting the "\n" at the end of printf() format strings you won't miss any lines.

---

### Post by Bachstelze on 2013-01-27
> **IAMTubby said:**
> So does the parent execute first upon successful fork ?
I'm trying to understand if there is a fixed order for who executes first, or is it just decided randomly, but that process keeps executing until a sleep or wait occurs ?

It is not decided randomly in the sense that you toss a coin to decide which one goes first, it is decided randomly in the sense that it depends on so many factors about the state of the system that you cannnot predict it in general, but that doesn't mean you can't predict it in some special cases like the one you have here (because your program is simple enough that the system will always be more or less in the same state when you run it).

---

### Post by IAMTubby on 2013-01-27
> **ofnuts said:**
> 
Your missing line is likely due to exiting without flushing buffers. When the output is to a terminal, printf()  flushes the output buffer when it sees a "\n". 

ofnuts, thanks, it works just fine :)
```

child : before calling sleep
child : after calling sleep
parent: before calling wait
parent: after calling wait

```

> 
If you take the habit of putting the "\n" at the end of printf() format strings you won't miss any lines.
Yes Sir,shall put the newline delimiter at the end of the line from now onwards.

Thanks.

---

### Post by IAMTubby on 2013-01-27
> **Bachstelze said:**
> It is not decided randomly in the sense that you toss a coin to decide which one goes first, it is decided randomly in the sense that it depends on so many factors about the state of the system that you cannnot predict it in general,
Okay. 

> 
but that doesn't mean you can't predict it in some special cases like the one you have here (because your program is simple enough that the system will always be more or less in the same state when you run it).
Okay, thanks a lot Bachstelze, I get it.

---

### Post by Bachstelze on 2013-01-27
It should be said also that even for a simple program like that, you can never be sure that for a particular run of the program, some event or other in the system will not cause the output order to be reversed, so you should really never rely on it.

---

### Post by jwbrase on 2013-01-28
> **IAMTubby said:**
> 1.Why is it that when this code executes, always the parent's part is executed first and then the child. Shouldn't that be random ? Or is it just a coincidence for me that **always** the parent part executes first ?

It will *almost* always be the parent's code that executes first. The reason is that, on any one CPU core, there is only one process running at a time, with the rest on a waiting list (actually it's a bit more complex than that, but this should give you the general idea). When it comes to the front of the list, a process is allowed to run for a short time block (generally around a hundredth of a second), after which the next process is selected. The parent process executes fork() during its time block, and, as long as it hasn't run out of time, continues executing until it runs out of time, calls sleep(), pause(), or wait() (or some other function that causes it to wait for an event), or exits. The only way that the child will execute first is if the parent runs out of time more-or-less at exactly the same time that the kernel returns to the parent from the fork() call (or if the parent runs out of time any time during the fork() call with a non-preemptible kernel).

---

### Post by IAMTubby on 2013-01-28
> **Bachstelze said:**
> It should be said also that even for a simple program like that, you can never be sure that for a particular run of the program, some event or other in the system will not cause the output order to be reversed, so you should really never rely on it.
Thanks Bachstelze. okay.

> **jwbrase said:**
> The reason is that, on any one CPU core, there is only one process running at a time, with the rest on a waiting list
Thanks jwbrase, shall remember that.

---

### Post by IAMTubby on 2013-02-17
> **MadCow108 said:**
> 
2. wait stores the status of the child into *status*, so it is unset until the wait call.
if WIFEXITED(status) is true it will contain the exitcode from _exit(..) (via WEXITSTATUS)
see the manpage for an example of its usage.
MadCow108,
I wrote this code which I think demo's the usage of WIFEXITED. Please check and let me know if it's okay. Thanks.
Edit : "wrote" is a wrong word, I actually googled and got bits from different places, and put it all together in 1 program.

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
 pid_t pid;
 int status = 0;

 pid = fork();
 /* parent process */
 if(pid)
 {
  printf("This is inside the parent \n");
  if ((pid = wait(&status)) == -1)
    perror("wait error");
  else
  {
    if (WIFSIGNALED(status) != 0)
     printf("Child process ended because of signal %d\n",WTERMSIG(status));

    else if (WIFEXITED(status) != 0)
     printf("Child process ended normally; status = %d\n",WEXITSTATUS(status));

    else
     printf("Child process did not end normally.n");
  }
  printf("this is the part after the wait \n");
  exit(1);
 }
 /* child process */
 else
 {
  printf("This is inside the child \n");
  printf("Going to sleep for 1 sec\n");
  sleep(1);
  printf("\ncame back from sleep ");
  _exit(1);
 }

```

---

