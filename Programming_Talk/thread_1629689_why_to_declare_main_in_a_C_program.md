---
title: "why to declare main in a C program"
date: 2010-11-24
forum: Programming Talk
---

### Post by jamesbon on 2010-11-24
I made a program which is still in development. I did not declared main in my program deliberately.As I am developing a library for making graph and other algorithm  which I would use in my programs.The purpose to develop such a library in C  is to work upon the problems given in book Introduction to Algorithms Thomas H Coreman
Here is the code if some one wants to see.

```
    #include<stdio.h>
    #include<stdlib.h>
    #define GREY 1
    #define BLACK 0
    #define WHITE 2
    typedef struct node *graph;
    
    graph cnode(int data);        //cnode is to create a node for graph
    void cgraph(void);
    struct node {
        int data, color;
        struct node *LEFT, *RIGHT, *TOP, *DOWN;
    };
    
    graph root = NULL;
    
    void cgraph(void)
    {
        int n, choice, dir, count;
    
        choice = 1;
        count = 1;
        graph priv, temp;
    
        printf("Printf we are making a graph the first is root node\n");
        while (choice == 1) {
            count++;
            if (count == 1) {
                printf("This is going to be root node \n");
                scanf("%d", &n);
                root = cnode(n);
                count--;
                priv = root;
            }        //ending if
            else {
                printf
                    ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
                scanf("%d", &dir);
                printf("Enter the data  for graph node\n");
                scanf("%d", &n);
                temp = cnode(n);
                if (dir == 1) {
                    priv->LEFT = temp;
                }
                if (dir == 2) {
                    priv->RIGHT = temp;
                }
                if (dir == 3) {
                    priv->TOP = temp;
                }
                if (dir == 4) {
                    priv->DOWN = temp;
                }
                priv = temp;
            }        //ending else
            printf
                ("Enter 1 to continue adding nodes to graph any thing else would take you out\n");
            scanf("%d", &choice);
        }            //ending while
    }                //ending main
    
    graph cnode(int data)
    {
        graph temp = (graph) malloc(sizeof(graph));
    
        temp->data = data;
        temp->LEFT = NULL;
        temp->RIGHT = NULL;
        temp->TOP = NULL;
        temp->DOWN = NULL;
        temp->color = -1;
        return temp;
    }
```

When I compiled the above program I got following error.

```
    cc graph.c
    /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
    (.text+0x20): undefined reference to `main'
    collect2: ld returned 1 exit status

```
What does this error signify and why should I declare main in my program?

---

### Post by ceclauson on 2010-11-24
The short and easy answer is that you need to use special options if you want to make a library and not a stand alone executable.

As for what the options are--I know you want to use the -c switch with gcc so that is compiles only, and doesn't try to link, like:

gcc test.c -c -o test.o

test.o is an object file, not executable.  Once you have one or more .o files that contain code you'd like to put in a library, you need to archive them.  Here's a page on that:

[http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/static-libraries.html](http://www.linux.org/docs/ldp/howto/Program-Library-HOWTO/static-libraries.html)

---

### Post by Arndt on 2010-11-24
> **jamesbon said:**
> 
When I compiled the above program I got following error.

```
    cc graph.c
    /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o: In function `_start':
    (.text+0x20): undefined reference to `main'
    collect2: ld returned 1 exit status

```
What does this error signify and why should I declare main in my program?

Again, do get yourself a good book about the C programming language. It is guaranteed that it will contain the answer to your question and many of your future ones.

If you want to do it the hard way, get the source to the startup code (the function _start), read about the ELF object code format, and how processes are started in Linux. These things are even going to be useful if you want to do kernel-level programming. With gdb, you can single-step programs instruction for instruction. Exercise: write your own linker, and make it support at least programs you can build using the assembler.

---

### Post by dwhitney67 on 2010-11-24
As ceclauson indicated, you need to derive an object file for each .c module you have.  But first you need to decide if you will build a static library or a shared-object library, because the steps are slightly different.

Say you have one.c and two.c...

For static library:
```

gcc -Wall -c one.c
gcc -Wall -c two.c

ar -r libmylib.a one.o two.o

```

For a shared-object library:
```

gcc -Wall -fPIC -c one.c
gcc -Wall -fPIC -c two.c

gcc -fPIC -shared libmylib.so one.o two.o

```

Then to build an app that contain at least one module with a main(), something like this is employed:
```

gcc -Wall -c main.c

gcc main.o -L<path to libmylib> -lmylib

```
If you decide to build both the static and shared-object library, then you need to specify specifically which library to use when building the app; for example, to explicitly use the static library:
```

gcc main.o -L<path to libmylib.a> -static -lmylib

```

---

### Post by jamesbon on 2010-11-24
> **Arndt said:**
> 
If you want to do it the hard way, get the source to the startup code (the function _start), read about the ELF object code format, and how processes are started in Linux. These things are even going to be useful if you want to do kernel-level programming. 
Thanks I liked this suggestion of yours.Yes I am getting deeper and deeper into kernels.Recently did some n number of experiments and decided to strengthen my C concepts also.I see at many places some or the other thing which would be new to me or let me re read the school book.

---

