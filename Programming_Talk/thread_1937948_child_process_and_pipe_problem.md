---
title: "child process and pipe problem"
date: 2012-03-08
forum: Programming Talk
---

### Post by Skillz12 on 2012-03-08
Hi can someone please help me with this problem. It was my school test  on wednesday and I failed som I'm trying to solve this problem because  next week I have correction option.
 
 Here is the assignement:
 
 Processes and Pipes
 
 Your task is to create a program that creates 102 childs. Always two  neighboring children will be connected with pipe, instead of the first  child who will have pipe only for output. Also the last child have only  pipe for input. All children will have standard inputs and outputs  redirected to the pipe. First child generates children and sends via  pipe to the second child, second child sends it to he third....etc...101  child receives the number and displays it on the screen. First, create  your first child then create others in a for loop and finally the last  child. For pipes use two dimensional array int pipe[100][2].
 
 Scheme:
 child_1 -> child_2 -> child_3 .... -> child_102

Here is my code, can you please tell me if I create child from a child and etc. ? how can I implement pipes into the for loop?
 ```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main (int argc, char *argv[])
{
    for (int i = 1; i <= atoi(argv[1]); i++) 
    {   
        
        int pid = fork();
        if (pid != 0) 
        {    
            //printf("I am a parent PID: %d\n", getpid());
              break;
        }
        if (pid == 0)
        {   
            printf("Child %d  .my PID is %d\n", i, getpid());
            exit(0);
        }
    }
}

```

---

### Post by Arndt on 2012-03-09
> **Skillz12 said:**
> Hi can someone please help me with this problem. It was my school test  on wednesday and I failed som I'm trying to solve this problem because  next week I have correction option.
 
 Here is the assignement:
 
 Processes and Pipes
 
 Your task is to create a program that creates 102 childs. Always two  neighboring children will be connected with pipe, instead of the first  child who will have pipe only for output. Also the last child have only  pipe for input. All children will have standard inputs and outputs  redirected to the pipe. First child generates children and sends via  pipe to the second child, second child sends it to he third....etc...101  child receives the number and displays it on the screen. First, create  your first child then create others in a for loop and finally the last  child. For pipes use two dimensional array int pipe[100][2].
 
 Scheme:
 child_1 -> child_2 -> child_3 .... -> child_102

Here is my code, can you please tell me if I create child from a child and etc. ? how can I implement pipes into the for loop?
 ```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main (int argc, char *argv[])
{
    for (int i = 1; i <= atoi(argv[1]); i++) 
    {   
        
        int pid = fork();
        if (pid != 0) 
        {    
            //printf("I am a parent PID: %d\n", getpid());
              break;
        }
        if (pid == 0)
        {   
            printf("Child %d  .my PID is %d\n", i, getpid());
            exit(0);
        }
    }
}

```

Did you get no instructions for how to create a pipe? There is an intuitively named system call for the purpose.

---

