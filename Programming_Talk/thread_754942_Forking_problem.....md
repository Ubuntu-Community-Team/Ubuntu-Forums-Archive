---
title: "Forking problem...."
date: 2008-04-14
forum: Programming Talk
---

### Post by buntu_Geek on 2008-04-14
Hi guys,

I have done some small programs involving forking process...

Having faced many problems with my programs... have these things unresolved in my mind::


1) Which process executes first.. child or process...

I am sure tat u cant predict this.. coz i got different results when i execute programs with same logics.... 

2) How does the kernel priorities... By asking tat i mean to ask ... How do u predict what happens...

3) If we are unable to predict then whats the best synchronization one can think...

4) wait() .. or waitpid() are there only for making the parent wait for the child.... what if a child want to wait for the parent process to give something to eat???

:confused:

Thanks in advance for any fruitful posts.....

buntu_Geek

---

### Post by themusicwave on 2008-04-14
1) The parent process always executes before it's child.  It starts the child process so it must have executed first right?

Unless you put a mechanism into your program to make it behave predictably, then it will be unpredictable.  

The kernel gives every process a chance to run most of the time.  At least it tries to do so.  Which process is running at which point is basically random.

What you need to do to make the child process wait is to simply get it into a blocking state.  It needs to willing give up the CPU until a specific event happens.  Once that happens it needs to wake up do its work and go back to sleep.

In different languages you do this differently(obviously) so the answer varies by language.

---

### Post by pedro_orange on 2008-04-14
The user can influence the priority of a process, but ultimately thats down to the kernel. 
It also depends on the type of process.
Some processes have waits in them (Like wait for input from keyboard) and others are instruction heavy processes (such as number crunchers). Processes with waits in are generous, and happily move out of the way for other processes that require the CPU.
However number crunchers that do not give up the CPU are seen as greedy, and the Kernel actually splits the number cruncher into sections so that it can interrupt during that process. Otherwise your PC would just lock up.

I've stolen this bash script from a book called "Linux's programmers toolbox" which illustrates priorites of generous vs. greedy.

niceguy:
```

# !/bsh/sh
while true; do
sleep .1
done
```

cruncher:
```

# !/bsh/sh
while true; do
true
done
```

runex:
```

# !/bsh/sh
./cruncher &
./niceguy &
trap 'echo stopping; kill %1 %2; break' SIGINT
while true; do
ps -C niceguy -C cruncher -o etime,pid,pri,cmd
sleep .5
done
```

Ctrl+C to break the infinite script

There are also a number of ways to schedule processes, like FIFO and Round Robin. You really need to have a good read about the linux process scheduler to understand it. (I only know the proper basics)

> 1) Which process executes first.. child or process...

Well, it depends on the process. But the parent creates the child, therefore it would start. It may require some sort of return from the child. Therefore it may wait for the child process to come back with a value. Or they may both run concurrently. 

> 3) If we are unable to predict then whats the best synchronization one can think...

Are you talking about serialisation? Mutexes/Semaphores?

> 4) wait() .. or waitpid() are there only for making the parent wait for the child.... what if a child want to wait for the parent process to give something to eat???

Well you could do a standard wait. Or you could use a lock. 
Or you could just wait until you have the information you wish to give to the child thread before you create it, and pass it to it on creation.

It all depends on the situation.

---

### Post by buntu_Geek on 2008-04-14
Great man.. Thanks a lot... you two...

@Pedro_orange...

You were talking about the locking a process.. how is tat? and also @ musicwave ... you were talking about putting a process to a blocking state.... how is tat achieved in C...

and.. i m no good at shell scripting... just started with some basics

So please give me some examples in C... quite good at it....

Thanks Again..

---

### Post by Tuna-Fish on 2008-04-14
> **buntu_Geek said:**
>  you were talking about putting a process to a blocking state.... how is tat achieved in C...

Call any blocking io function. Simple read() is blocking io, that is, when you read from disk, your process blocks until the requested data is delivered by kernel to your buffer. To use it between processes, make a pipe or a socket, and read from it by your work process. Until your parent process writes to it, your work process blocks.

[php]
#include <sys/types.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>

/* Read characters from the pipe and echo them to stdout.   */

void 
read_from_pipe (int file)
{
  FILE *stream;
  int c;
  stream = fdopen (file, "r");
  while ((c = fgetc (stream)) != EOF)
    putchar (c);
  fclose (stream);
}

/* Write some random text to the pipe.  */

void 
write_to_pipe (int file)
{
  FILE *stream;
  stream = fdopen (file, "w");
  fprintf (stream, "hello, world!\n");
  fprintf (stream, "goodbye, world!\n");
  fclose (stream);
}
// ############### START HERE
int main (void) {
  pid_t pid;
  int mypipe[2];

  /* Create the pipe.  */
  if (pipe(mypipe) )
    {
      fprintf (stderr, "Pipe failed.\n");
      return EXIT_FAILURE;
    }

  /* Create the child process.  */
  pid = fork ();
  if (pid == (pid_t) 0)
    {
      /* This is the child process.  */
      read_from_pipe (mypipe[0]);
      return EXIT_SUCCESS;
    }
  else if (pid < (pid_t) 0)
    {
      /* The fork failed.  */
      fprintf (stderr, "Fork failed.\n");
      return EXIT_FAILURE;
    }
  else
    {
      /* This is the parent process.  */
      write_to_pipe (mypipe[1]);
      return EXIT_SUCCESS;
    }
}
[/php]

The common worker thread pattern actually is that you create a pipe, or two pipes, and the worker thread sits in 

while (1) {
read(pipe);
if (I_just_got_exit_maker_from_pipe) break;
do_work;
}

---

### Post by buntu_Geek on 2008-04-14
So simply for synchronisation.... i have to do a costly IO ... 

Isnt there any other way...

I am asking for a way to make child wait for some thing from parent.....where as parent waiting for child can be acheived using wait() -- a sys call...

---

### Post by themusicwave on 2008-04-14
To make it work you need some way for the parent process and child process to communicate.

Common methods are:

Files
Loopback IP address 127.0.0.1
Shared Memory

All the ways I can think of right now use I/O.

It really isn't that costly as long as you sleep times are sane.  Just don't make the sleep time too short or you will just be wasting CPU cycles and starving out other processes.

I would also guess that the wait() sys call uses one of the above mentioned methods.  You just don't realize it.

---

### Post by Tuna-Fish on 2008-04-14
> **buntu_Geek said:**
> So simply for synchronisation.... i have to do a costly IO ... 

This comment makes no sense. The cost of the IO is perhaps 1/1000th of the cost of the context switch. When you use pipes like that, nothing ever leaves memory. And that pattern is very common among programs in unixland, meaning it has been optimized for in the kernel.

> 
I am asking for a way to make child wait for some thing from parent.....where as parent waiting for child can be acheived using wait() -- a sys call...
Very likely wait does something very similar behind the scenes.

What exactly are you really trying to do?

I just want to point out that when you switch processes, caches are flushed, which means writing all it to memory and reading them back full again. If cost of in-memory io is killing you, you shouldn't be forking in the first case.

---

### Post by Tuna-Fish on 2008-04-14
Perhaps what you really want is threads?

---

### Post by slavik on 2008-04-14
> **buntu_Geek said:**
> Hi guys,

I have done some small programs involving forking process...

Having faced many problems with my programs... have these things unresolved in my mind::


1) Which process executes first.. child or process...

I am sure tat u cant predict this.. coz i got different results when i execute programs with same logics.... 

2) How does the kernel priorities... By asking tat i mean to ask ... How do u predict what happens...

3) If we are unable to predict then whats the best synchronization one can think...

4) wait() .. or waitpid() are there only for making the parent wait for the child.... what if a child want to wait for the parent process to give something to eat???

:confused:

Thanks in advance for any fruitful posts.....

buntu_Geek

1. after fork, the child usually runs first because in the olden days of unix you forked and the child would almost instantly call exec (most of the time), then a new version of fork called vfork appeared which didn't copy the parent's variables (thus it was faster than regular fork)

2. what exactly are you trying to predict? (I don't understand your question)

3. synchronization: shared memory, pipes, messages queues, sockets. shared memory and pipes will need to be used along with semaphores.

4. if you need the parent process to 'kick' the child process, fork() returns the pid of the child process to the parent process (and 0 to the child, -1 if forking failed), then you need to use one of the methods in #3 for synchronization (shared memory is fastest AFAIK, message queues are the easiest to use IMO)

EDIT:
if you use sockets, don't use INET sockets, use domain (UNIX) sockets. you allocate each one in exactly the same way (same system calls) but INET sockets will travel down the network stack before coming back. UNIX (domain) sockets are like INET sockets are more like pipes.

---

### Post by buntu_Geek on 2008-04-15
Thanks guys....

I havnt used sockets and semaphores as of now...... I only know pipes....

Anyways.... i ll give you weird thing that i encountered recently....

 

```


#include<stdio.h>
#include<sys/types.h>
#include<unistd.h>
#include<stdlib.h>
int main()
{
 char s[20],x;
 int t;
 int fd1[2];
 pid_t pid1;
 pipe(fd1);
 pid1=fork();
 if(pid1==0)
 {
  while(1)
  {
   close(fd1[1]);
   read(fd1[0],&x,4);

   if(x=='*')
        exit(0);
         if(x<'A'||x>'Z')
        {
                printf("[%d]:error",getpid());
                exit(1);
        }

   printf("[%d]:%d",getpid(),(int)x);
   }
  }
 else
 {
  while(1)
  {
   close(fd1[0]);
   scanf("%s",s);
   printf("[%d]:%c",getpid(),s[0]);
   write(fd1[1],&s[0],4);
   if(s[0]=='*')
   {
   wait(NULL);
   exit(0);
   }
    if(s[0]<'A'||s[0]>'Z')
                {
                        wait(NULL);
                        printf("[%d]:error",getpid());
                        exit(1);
                }

  }
 }
 return 0;
}

```

There is no special purpose for this program but just experimentation....

The program does following: 1) parent reads input, sends to child  the 1st character read (thro pipe) , then... 2) child reads from pipe and outputs its ascii.. this is done till a special chara is encountered ('*') ... 

When i tried to execute this code.. the problem was .. it never entered the child... ( the output reflects...so..)

when i changed the above code with all the printfs appended with '\n'.. 
It worked....

I dunno whether its the problem with printf or switching of child and parent process..... but what is the link between an stdio and IPC... :confused:

or 

Am i wrong somewhere...

Probably a bug.... dunno.... i m still a noob...

---

### Post by stroyan on 2008-04-15
The newlines interact with the default buffering of stdio.
The default will buffer up to BUFSIZE characters before actually writing.
When output is to a tty the buffer will flush for each newline output.
You can change the buffering behaviour with a call to setvbuf().
```

 setvbuf(stdout,NULL,_IONBF,0);

```

---

### Post by Tuna-Fish on 2008-04-16
I think your bug is in wait, it takes the address of an int as an argument, not an int. So, you gave it null, and it tried to write stuff to null, causing premature death. try:
int status;
wait(&status);

---

### Post by WW on 2008-04-16
Tuna-Fish, take a look at the man page for wait:
> 
If  status  is  not  NULL,  wait() and waitpid() store status information in the int to which it points.


---

### Post by Tuna-Fish on 2008-04-16
> **WW said:**
> Tuna-Fish, take a look at the man page for wait:

oh, sorry.

---

