---
title: "Fork() system call with c"
date: 2010-04-06
forum: Programming Talk
---

### Post by mike_ldis on 2010-04-06
Hallo! I am new trying to create a program that uses fork() to create some child prosecces.The amount of the procceses that will be created every time will be given from the argv[1]. My code is
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
main(int argc, char **argv)
{
int pid;
int i;
        for(i=1;i<=*(argv+1);i++){
               pid=fork(); 
               printf("Prosecc id:%d \n",pid);
}
        
}
When i execute this the o/s crashes.Any suggestions?

---

### Post by lisati on 2010-04-06
> **mike_ldis said:**
> Hallo! I am new trying to create a program that uses fork() to create some child prosecces.The amount of the procceses that will be created every time will be given from the argv[1]. My code is
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
main(int argc, char **argv)
{
int pid;
int i;
        for(i=1;i<=*(arg[COLOR="Red"]v[/COLOR]+1);i++){
               pid=fork(); 
               printf("Prosecc id:%d \n",pid);
}
        
}
When i execute this the o/s crashes.Any suggestions?
It's probably the "argv" in the "for" statement.

Is the following what you want?
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
main(int argc, char **argv)
{
int pid;
int i;
        for(i=1;i<=*(arg[COLOR="Red"]c[/COLOR]+1);i++){
               pid=fork(); 
               printf("Prosecc id:%d \n",pid);
}
        
}

```

---

### Post by mike_ldis on 2010-04-06
> **lisati said:**
> It's probably the "argv" in the "for" statement.

Is the following what you want?
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
main(int argc, char **argv)
{
int pid;
int i;
        for(i=1;i<=*(arg[COLOR=Red]c[/COLOR]+1);i++){
               pid=fork(); 
               printf("Prosecc id:%d \n",pid);
}
        
}

```

No the amount of the procceses that will be created will be given from the first argument of the argv (argv[1])

---

### Post by Compyx on 2010-04-06
> **mike_ldis said:**
> Hallo! I am new trying to create a program that uses fork() to create some child prosecces.The amount of the procceses that will be created every time will be given from the argv[1]. My code is
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char **argv)
{
    int pid;
    int i;
    for(i = 1; i <= *(argv + 1); i++){
        pid = fork(); 
        printf("Prosecc id:%d \n", pid);
    }
    return 0;        
}

```
When i execute this the o/s crashes.Any suggestions?

I cleaned your code up a little, but left the error. The error is the assumption that argv[1] constains an integer. It contains a pointer to an array of char, so you need to convert argv[1] into an integer.

Since a pointer may very well be a very large number, when cast to int, your program forks() a lot. You should therefor check the return value of fork().

But, to solve your int/string problem: (untested)
```

char *endptr;
long num = strtol(argv[1], &endptr, 0);
if (endptr == argv[1]) {
    fprintf(stderr, "no digits found!\n");
    /* bail out or default to some number */
} else if (*endptr != '\0') {
    fprintf(stderr, "garbage after digits!\n");
}

```

Ofcourse, in production code, you would also check for overflow by examining errno and the value returned by strtol().

But the intent should be clear: all arguments in the argument vector argv are 'strings', so if you need to get a number from one of the arguments, you should use one of the strto* functions.

---

### Post by MadCow108 on 2010-04-06
this would probably loop as often as you want:
**(argv + 1) - '0'
the double dereference makes a char out of the char** and then by subtracting the ascii value of 0 you obtain the real number
you could also write this:
*argv[1] - '0'
or
atoi(argv[1])

but the main problem is that have created a kind of forkbomb, no wonder your os crashes

when you fork you create a copy of the parent process, including the loop.
So the child processes again spawn many child processes and so on.

---

### Post by Xyro on 2010-04-06
Try this:

```

# include <stdio.h>
# include <stdlib.h>
# include <unistd.h>

int main(int argc, char **argv)
{

  int pid;
  int i;

  for(i=1;i<=atoi(argv);i++)
  {
    pid=fork();
    // Child pid = 0, parent pid = child'd process id. If child, exit loop (no fork() bomb, please).
    if (pid == 0)
    {
      printf("Child #: %d \n", i);
      break;
    }
  }

  return 0;

}

```

---

