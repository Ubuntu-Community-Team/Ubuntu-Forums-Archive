---
title: "Error in pipes code"
date: 2014-05-07
forum: Programming Talk
---

### Post by one_girl on 2014-05-07
I want this program communicate between parent and child ,the parent send signal to child choice the two number randomly, and then parent add  that two number choice it by child  and print the total . 




```

#include <stdio.h> /* For printf */
#include <string.h> /* For strlen */
#include <stdlib.h> /* For exit */
 
main(){
    int pid, fd[2], bytes;
    int num1 = rand()%100; 
int num = rand()%100; 
    if (pipe(fd) == -1) { 
        perror("pipe"); 
        exit(1); 
    }
    if ((pid = fork()) == -1) { 
        perror("fork");
printf("Please Enter First number: ");    /*I want a Parent to send a sginal to the child then the child will choice random num between 0 and 100 */


printf("Please Enter First number: ");    /*I want a Parent to send a sginal to the child then the child will choice random num between 0 and 100 */


printf("Total number is : ");    //the parent will add the two random num


        exit(1); 
    }






    if (pid == 0) { 
 
close(fd[0]); 


write(fd[1], &num, sizeof(num));
sleep (3);
 read(fd[0], &num1, sizeof(num1));
       
       
    } 
    else { 
        close(fd[1]); 
        read(fd[0], &num1, sizeof(num1));
        close(fd[0]);  
    }
}

```

---

### Post by ofnuts on 2014-05-08
Some more homework eh?

I'm surprised you survived your programming class up to now because you code like it's your first or second program ever and piping between two process is a bit above that level.

I'm not going to debug your code. Some random remarks:


[LIST=1]
[*]the only comments in there (besides the questions) state the obvious (near the #include's).
[*]you are otherwise file descriptors without really telling what you expect that to do.
[*]I don't understand why you are print these 3 lines after perror("fork")
[*]pipes are unidirectional. If you want the processes to interact you need two pipes (parent->child and child->parent
[*]giving real names (copy to adequately named variables, or use #define's constants) to the pipe handles (and to other variables) will help you write code that you can follow
[/LIST]
[B]
Methodology[/B]: programming is not writing code and expecting it to work the first time. The art of programming is mostly debugging your own code, ie understanding why it doesn't work as expected and how to fix it. One of my programming idols wrote that debugging is twice as hard as writing the code, so you cannot debug code that you wrote without understsanding well what was going on.  Code rarely works by some miracle. So:

[LIST=1]
[*]Add comment to you code that explain to you, in your own terms, what the code is supposed to do (writing these will make you ask yourself some questions that may help you understand what you should write)
[*]Add printf() statements here and there that show you what paths you code is following and what the vale of some variables are
[*]Match the output of 2) with what your wrote in 1) and explain the discrepancies.
[*]If you can't explain them, then ask here
[/LIST]

---

