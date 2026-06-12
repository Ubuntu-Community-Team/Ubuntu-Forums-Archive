---
title: "Whats wrong with this code ?"
date: 2009-08-29
forum: Programming Talk
---

### Post by cation007 on 2009-08-29
Hi,
I am trying to learn the basics of IPC.

I am trying to run this sample code (its not my code) on Mac's shell.

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>

int main(void)
{
        int     fd[2], nbytes;
        pid_t   childpid;

        pipe(fd);

	printf("Testing ");

	childpid = fork();

 printf("\n");
 return(1);       
}

As far as I understood, once you fork, the child process should not print "Testing "

But the above code prints "Testing " twice.

And if I print "Testing \n", it prints only once.

What is going wrong ? I am confused.

Thanks,

---

### Post by dribeas on 2009-08-29
> **cation007 said:**
> 
As far as I understood, once you fork, the child process should not print "Testing "

But the above code prints "Testing " twice.

And if I print "Testing \n", it prints only once.


 I can only assume that the first printf is not flushing the data to stdout, but rather writing in an internal buffer. After the fork, both processes have exact same memory maps, and at that point both of them have an internal buffer with "Testing" on it. Then each one of them, with the printf("\n") flush the internal memory into the file (console in this case) producing duplicated output.

If you force the output buffer to flush before you create the child process ( fflush(stdout) after the printf and before the fork() ) then you will see that there is a single "Testing" string in the console, while there are two newlines.

---

### Post by soltanis on 2009-08-29
As usual, buffering is your problem. The standard output is line-buffered (it flushes on "\n") and both processes have the same data in their buffer (your testing message).

Try writing to stderr, or use setvbuf(2) to turn off buffering, and see the difference.

---

### Post by cation007 on 2009-08-29
Hey thanks,
That makes sense.

Is there any other things I need to take care before forking ?

or is it only with stdins and stdouts ?

---

### Post by soltanis on 2009-08-29
Well, obviously anything else that is buffered. Establishing pipes. That kind of stuff.

---

