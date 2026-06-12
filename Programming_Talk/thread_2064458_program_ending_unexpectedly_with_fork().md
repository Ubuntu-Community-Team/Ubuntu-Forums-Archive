---
title: "program ending unexpectedly with fork()"
date: 2012-09-29
forum: Programming Talk
---

### Post by shaaraddalvi on 2012-09-29
I actually wanted to learn about the pipe() command and so I thought I'll fork() a child, take input of an integer array from user in parent process, send that array to child using pipe() and and print the array via child process.
While doing this, I am struck with taking input of the array in the parent process at the first place...Whenever I dynamically create an array, say of 5 elements, it takes input of only the first element via the for loop, and as soon as I press the enter key to enter the second element, the program closes. The for loop should be completed..but the program is ending..
Any help would be ace...thanks in advance.. :)
```

#include<unistd.h>
#include<iostream>

using namespace std;

int main()
{
    fork();
    int fd[2],pid,i;
    int * array;
    pid=fork();
    if(pid==0)
    {
        int tot;
        cin>>tot;
        array=new int[tot];
        for(i=0;i<tot;i++)
        {
            cout<<"Enter "<<(i+1)<<" element : ";
            cin>>array[i];
        }
    }
}

```

---

### Post by MadCow108 on 2012-09-29
whats the point of the first fork? you start 4 processes in that snippet.

you need to let the parent wait for the child, else it will end and kill its child with it
just add an else to the if and use waitpid.

---

### Post by trent.josephsen on 2012-09-29
```
    pid=fork();
    if(pid==0)
    {
        /* what process runs this code? */
    }
    /* what happens to the other process? */

```

---

