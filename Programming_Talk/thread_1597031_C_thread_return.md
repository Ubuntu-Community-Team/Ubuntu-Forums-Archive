---
title: "C thread return"
date: 2010-10-14
forum: Programming Talk
---

### Post by Xender1 on 2010-10-14
I am having trouble returning information from the function my threads are calling. What I am passing in is a struct mystruct and returning one aswell. When I try and access the information I return I get a seg fault. I am writing this in C and this is what I have going on:
```

#include <stdio.h>
#include <stdlib.h>
#include <pthread.h>

struct data
{
    //given as arg
    char *filename;
    //returned from thread
    int x; int y;
};

void *getcoords(void *ptr);

int main(int argc, char** argv) {

        struct data testinfo; //struct
        pthread_t mythread;  //thread
        void *ret;  //return value from struct
        testinfo.filename = "testfile.txt";  //load coords from this file

//create thread passing in the struct with the filename
        pthread_create(&mythread,NULL,getcoords,(void*)&testinfo); 
//join thread and return value to the variable ret
        pthread_join(mythread,&ret);
   //a struct of data* now to hold the return info
        struct data *newinfo;
        newinfo = (struct data*) ret;
        //this line segfaults
        printf("%s %d %d\n",newinfo->filename,newinfo->x,newinfo->y);

       return 0;
}

void *getcoords(void *ptr) {
    struct data *ret = (struct data *) ptr;
    ret->x = 1;
    ret->y = 2;

    return(ptr);
}

```

Turns out, that this only seg faults when I compile within netbeans, but when I run from command line it work using this
```

gcc -pthread -Wall -o mybackup main.c

```
I see that netbeans is compiling with
```

gcc -pthread   -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.c

```

I dont see what would make the difference especially a seg fault.

---

### Post by spjackson on 2010-10-15
The manual command line compiles and links in one step, whereas the netbeans version compiles only without linking, so you are not comparing like with like. However, a significant feature is that the netbeans  command includes debugging information (-g) whereas your command line  build does not. It could be that you are using some undefined behaviour  which is thankfully caught in debug mode, but perhaps works for now in  release mode.

However, the code looks ok to me and I can't get it to segfault in either debug or release mode.

Are you sure that the segfaulting is from the version of the code you posted? It could happen if getcoords() returned an address of one of its stack variables, but in the code you posted this isn't happening: it simply returns its parameter.

Can you run the netbeans build in a debugger? Does it segfault then? If so, look at the addresses: does newinfo == &testinfo as it is supposed to?

---

### Post by nvteighen on 2010-10-15
No segfault here either... Care to post the output you get?

---

