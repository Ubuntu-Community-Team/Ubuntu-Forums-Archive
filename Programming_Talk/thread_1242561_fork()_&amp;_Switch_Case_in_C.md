---
title: "fork() &amp; Switch Case in C"
date: 2009-08-17
forum: Programming Talk
---

### Post by rahul_shilps on 2009-08-17
My sw.c is as follows:

--------------------------------------------------------------

#include<stdio.h>

int main()
{
     int pid;
     pid = fork();

     switch(pid)
     {
           case 0:
                printf ("Am child, my ID: %d", getpid() );
                ***printf ("Am child, my Parent id: %d",getppid() );***
                break;

           case -1:
                printf ("The child process has not created");
                break;

           default:
                [B][I]printf ("am in default , process id: %d",              
                                                      getpid());[/I][/B]
                sleep(10);
                break;
     }                         // switch case closed
     
     system("ps");
}     // main function close

--------------------------------------------------------------

Now i think, neither parent should not execute the code inside the **default** block of the nor the child.

As we know, value of pid=0; so it should not execute **default** block! It should only execute the block with case 0. right.

When i look at the lines of code which i keep in bold & italic, these line return me same ID. :(

1) Why? How?

2) What is the fundamental concept behind a fork()?

3)What is the role & scope of the Parent process then?

please help. I will be thankful to you.

---

### Post by Arndt on 2009-08-17
> **rahul_shilps said:**
> My sw.c is as follows:

--------------------------------------------------------------

#include<stdio.h>

int main()
{
     int pid;
     pid = fork();

     switch(pid)
     {
           case 0:
                printf ("Am child, my ID: %d", getpid() );
                ***printf ("Am child, my Parent id: %d",getppid() );***
                break;

           case -1:
                printf ("The child process has not created");
                break;

           default:
                [B][I]printf ("am in default , process id: %d",              
                                                      getpid());[/I][/B]
                sleep(10);
                break;
     }                         // switch case closed
     
     system("ps");
}     // main function close

--------------------------------------------------------------

Now i think, neither parent should not execute the code inside the **default** block of the nor the child.

As we know, value of pid=0; so it should not execute **default** block! It should only execute the block with case 0. right.

When i look at the lines of code which i keep in bold & italic, these line return me same ID. :(

1) Why? How?

2) What is the fundamental concept behind a fork()?

3)What is the role & scope of the Parent process then?

please help. I will be thankful to you.

Process 1 calls fork(). This creates a new process 2, which has process 1 as parent. The execution of the new process starts with it returning 0 from the fork() call, while the parent receives the pid of the child from the fork() call.

Process 1 will remain the parent of process 2 until one of them dies. If process 1 dies first, the 'init' process will become the parent of process 2.

Does this answer your questions?

---

### Post by rahul_shilps on 2009-08-17
> **Arndt said:**
> Process 1 calls fork(). This creates a new process 2, which has process 1 as parent. The execution of the new process starts with it returning 0 from the fork() call, while the parent receives the pid of the child from the fork() call.

Process 1 will remain the parent of process 2 until one of them dies. If process 1 dies first, the 'init' process will become the parent of process 2.

Does this answer your questions?

u said that

"while the parent receives the pid of the child from the fork() call."

how is this and what is this.
can you please elaborate?:confused:

---

### Post by stroyan on 2009-08-17
The return value of a successful fork as seen from the parent process is the pid of the child process.  That will make the parent process execute the "default" case in your switch and print its own process id as found by getpid().  The child process will execute the "case 0" code and print its parent process id as found by getppid().  Those are both the same process id.

You should include unistd.h for code that will be calling fork().
And the return type is actually "pid_t" rather than plain "int".
(But "int" will work fine in practice.)

---

### Post by rahul_shilps on 2009-08-17
> **stroyan said:**
> The return value of a successful fork as seen from the parent process is the pid of the child process.  That will make the parent process execute the "default" case in your switch and print its own process id as found by getpid().  The child process will execute the "case 0" code and print its parent process id as found by getppid().  Those are both the same process id.

You should include unistd.h for code that will be calling fork().
And the return type is actually "pid_t" rather than plain "int".
(But "int" will work fine in practice.)

Thank you i got it. Little confusion there but will resolve it.

Thank you.

---

