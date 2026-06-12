---
title: "simple codes about fork() and wait()"
date: 2010-09-23
forum: Programming Talk
---

### Post by rob2468 on 2010-09-23
```
#include<unistd.h>

main()
{
    int i, j;
    printf("My pid is %d, my father's pid is %d\n", getpid(), getppid());
    for(i=0; i<3; i++)
        if(fork() == 0)
            printf("%d pid = %d, ppid = %d\n", i, getpid(), getppid());
        else
        {
            j=wait(0);
            printf("%d: The chilid %d is finished.\n", getpid(), j);
        }
}

```OUTPUT
```
My pid is 6549, my father's pid is 6533
0 pid = 6550, ppid = 6549
1 pid = 6551, ppid = 6550
2 pid = 6552, ppid = 6551
6551: The chilid 6552 is finished.
6550: The chilid 6551 is finished.
2 pid = 6553, ppid = 6550
6550: The chilid 6553 is finished.
6549: The chilid 6550 is finished.
1 pid = 6554, ppid = 6549
2 pid = 6555, ppid = 6554
6554: The chilid 6555 is finished.
6549: The chilid 6554 is finished.
2 pid = 6556, ppid = 6549
6549: The chilid 6556 is finished.
```I know something about c programming.A c program will execute sequentially.but How the "else" code work.what is the working procedure of the program.
My os teacher gave this.I'm confused about it.

---

### Post by lloyd_b on 2010-09-23
The fork() function takes one process (the "parent" process), and creates a second process (the "child" process) that's an almost exact duplicate of the parent process.  So after a successful fork(), there are now two almost identical processes, both at the same point of execution in the program.

The difference between the two processes is the return value from fork().  In the parent process, fork() returns the PID of the new child process that was created.  In the child process, however, fork() returns 0.

So that "if(fork() == 0)" will be true only for the child process, and the else clause will be taken by the parent process.

Lloyd B.

---

