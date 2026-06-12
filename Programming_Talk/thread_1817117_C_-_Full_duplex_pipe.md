---
title: "C - Full duplex pipe"
date: 2011-08-02
forum: Programming Talk
---

### Post by matt-e-matt on 2011-08-02
I'm trying to implement a full duplex pipe for two programs to  communicate between each other.  Basically, main reads to numbers as  char arrays, forks a child process which converts and add the numbers,  the child process then writes the result as a char array and the parent  process reads the result and prints it to the screen.  The book I have does a horrible job at explaining it, and I can't find anything adequate through google. 
```

// main.c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <wait.h>

int main(void)
{
    pid_t          cid;
    int   c_ret_status, fd1[2], fd2[2];
    char num1[sizeof(int)], num2[sizeof(int)], sum[sizeof(int)];;

    puts("Enter first number: ");
    fgets(num1, sizeof(int), stdin);
    puts("Enter second number: ");
    fgets(num2, sizeof(int), stdin);

    pipe(fd1);
    pipe(fd2);

    if((cid = fork()) == 0)
    {
        close(fd1[0]);
        close(fd2[1]);

        dup2(fd2[0], STDIN_FILENO);
        dup2(fd1[1], STDOUT_FILENO);

        execl("add", "add", NULL, NULL);
        //_exit(0);
    }
    else
    {
        sleep(1);

        close(fd1[1]);
        close(fd2[0]);

        dup2(fd1[0], STDIN_FILENO);
        dup2(fd2[1], STDOUT_FILENO);

        write(fd2[1], num1, sizeof(int));
        write(fd2[1], num2, sizeof(int));

        read(fd1[0], sum, sizeof(int));
    }

    wait(&c_ret_status);
    printf("Sum is %s\n", sum);

    return 0;
}

```
```

// add.c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
    char n1[sizeof(int)], n2[sizeof(int)], s[sizeof(int)];
    int num1 = 0, num2 = 0, sum = 0;

    puts("\nReading first number...");
    read(STDIN_FILENO, n1, sizeof(n1));
    puts("Reading second number...");
    read(STDIN_FILENO, n2, sizeof(n2));

    num1 = atoi(n1);
    num2 = atoi(n2);

    puts("Adding and converting numbers...");
    sum = num1 + num2;
    sprintf(s, "%d", sum);

    puts("Writing number to main...");
    write(STDOUT_FILENO, s, sizeof(s));
    
    return 0;
}

```

Any help is much appreciated.

---

### Post by karlson on 2011-08-02
> **matt-e-matt said:**
> I'm trying to implement a full duplex pipe for two programs to  communicate between each other.  Basically, main reads to numbers as  char arrays, forks a child process which converts and add the numbers,  the child process then writes the result as a char array and the parent  process reads the result and prints it to the screen.  The book I have does a horrible job at explaining it, and I can't find anything adequate through google. 

Any help is much appreciated.

So what exactly is the question?
Have you consulted this:
[http://www.pearsonhighered.com/educator/product/Advanced-Programming-in-the-UNIX-Environment/9780201433074.page](http://www.pearsonhighered.com/educator/product/Advanced-Programming-in-the-UNIX-Environment/9780201433074.page)

---

### Post by matt-e-matt on 2011-08-02
> **karlson said:**
> So what exactly is the question?
Have you consulted this:
[http://www.pearsonhighered.com/educator/product/Advanced-Programming-in-the-UNIX-Environment/9780201433074.page](http://www.pearsonhighered.com/educator/product/Advanced-Programming-in-the-UNIX-Environment/9780201433074.page)


I'm asking how I would make the code I posted work.

I have that book, it does not explain full duplex pipes.

---

### Post by karlson on 2011-08-03
> **matt-e-matt said:**
> I'm asking how I would make the code I posted work.

I have that book, it does not explain full duplex pipes.

One thing I would recommend thinking about is what you are writing and what you are reading.

In the original process you are writing when you are creating an integer and copying into an array of sizeof(int) which is 4 bytes you are quite likely to truncate the value.

My suggestion is to change the code as follows:
```

// main.c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <wait.h>

int main(void)
{
    pid_t          cid;
    int   c_ret_status, fd1[2], fd2[2], num1, num2, sum;
    char number[11];

    puts("Enter first number: ");
    fgets(number, sizeof(number), stdin);
    num1 = atoi(number);
    puts("Enter second number: ");
    fgets(number, sizeof(number), stdin);
    num2 = atoi(number);

    pipe(fd1);
    pipe(fd2);

    if((cid = fork()) == 0)
    {
        close(fd1[0]);
        close(fd2[1]);

        dup2(fd2[0], STDIN_FILENO);
        dup2(fd1[1], STDOUT_FILENO);

        execl("add", "add", NULL, NULL);
        //_exit(0);
    }
    else
    {
        sleep(1);

        close(fd1[1]);
        close(fd2[0]);

        dup2(fd1[0], STDIN_FILENO);
        dup2(fd2[1], STDOUT_FILENO);

        write(fd2[1], &num1, sizeof(num1));
        write(fd2[1], &num2, sizeof(num2));

        read(fd1[0], &sum, sizeof(sum));
    }

    wait(&c_ret_status);
    printf("Sum is %d\n", sum);

    return 0;
}

```
```

// add.c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
    int num1 = 0, num2 = 0, sum = 0;

    puts("\nReading first number...");
    read(STDIN_FILENO, &num1, sizeof(num1));
    puts("Reading second number...");
    read(STDIN_FILENO, &num2, sizeof(num2));

    puts("Adding and converting numbers...");
    sum = num1 + num2;

    puts("Writing number to main...");
    write(STDOUT_FILENO, &sum, sizeof(sum));
    
    return 0;
}

```

---

### Post by matt-e-matt on 2011-08-03
Thanks for the help, the code still doesn't work properly though.

---

### Post by karlson on 2011-08-03
> **matt-e-matt said:**
> Thanks for the help, the code still doesn't work properly though.

I'd hate to think this is a homework problem but you should consider why are you doing the same thing in the spawned process as you do in the original one?  You are overwriting the STDIN and STDOUT for the original process...  Why are you doing that?

---

### Post by slavik on 2011-08-03
are pipes a requirement? also, when you fork, you carry pipe data over (since file descriptors carry over)

---

### Post by matt-e-matt on 2011-08-03
This definitely isn't homework, I'm learning it for fun before I move on to threads, so I guess you could say using fork, pipe, dup2, etc are all required.  I've been staring at this stuff for ever, reading and searching for a lot of sources, but there is obviously something I just do not get.  If some one could spell it out for me, fix m code so it works properly, provide me with similar code I could look, or give me sources that explain this well, I would really appreciate that.

---

### Post by matt-e-matt on 2011-08-03
Double post.. sorry.

---

### Post by matt-e-matt on 2011-08-03
Alright so I figured it out, I had to get rid of the 2 dup2 functions in main's else statement.

---

