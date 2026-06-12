---
title: "C programming problem in Netbeans 6.8"
date: 2010-12-12
forum: Programming Talk
---

### Post by shivugh on 2010-12-12
[B]Hi fellas, 

I am trying to learn C programming using Netbeans 6.8 in Ubuntu linux and I am having trouble compiling a simple 'hello world' program.[/B]

**This is the program I wrote:**

#include<stdio.h>
#include<stdlib.h>
int main()
{
    printf("Hello");
}

**This is the output (error) I am getting:**

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/Mike/NetBeansProjects/Hello world'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/hello_world
make[2]: Entering directory `/home/Mike/NetBeansProjects/Hello world'
mkdir -p dist/Debug/GNU-Linux-x86
gcc     -o dist/Debug/GNU-Linux-x86/hello_world build/Debug/GNU-Linux-x86/Hello.o build/Debug/GNU-Linux-x86/main.o build/Debug/GNU-Linux-x86/Hi.o  
build/Debug/GNU-Linux-x86/main.o: In function `main':
/home/Mike/NetBeansProjects/Hello world/main.c:14: multiple definition of `main'
build/Debug/GNU-Linux-x86/Hello.o:/home/Mike/NetBeansProjects/Hello world/Hello.c:4: first defined here
build/Debug/GNU-Linux-x86/Hi.o: In function `main':
/home/Mike/NetBeansProjects/Hello world/Hi.c:14: multiple definition of `main'
build/Debug/GNU-Linux-x86/Hello.o:/home/Mike/NetBeansProjects/Hello world/Hello.c:4: first defined here
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/hello_world] Error 1
make[2]: Leaving directory `/home/Mike/NetBeansProjects/Hello world'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/Mike/NetBeansProjects/Hello world'
make: *** [.build-impl] Error 2
BUILD FAILED (exit value 2, total time: 191ms)


**Any help would be much appreciated.** :)

---

### Post by GregBrannon on 2010-12-12
Did you show all of your code?  What's the "Hi.c" file that also has a main definition?

---

### Post by Queue29 on 2010-12-12
The Netbeans IDE seems to have created a file with "main" already in it (which advanced IDE's have a habit of doing) and you have created your own file, "Hi.c", which also contains a conflicting main function. You need to pick and use only one. Better yet, use something like gedit and the command line to learn C. Complex IDE's only get in the way, like how you are experiencing.

---

### Post by shivugh on 2010-12-13
Hi,

As explained by Queue29, Netbeans seem to create a file with 'main' already in it. I don't know why it does that. When I deleted the 'main' file. The program seem to work. Also when I created another file within the same 'project', the problem seem to resurface. Can anyone explain to me what is going on? I am new to this C programming thing. 

Thanks fellas

---

### Post by dwhitney67 on 2010-12-13
> **shivugh said:**
> Hi,

As explained by Queue29, Netbeans seem to create a file with 'main' already in it. I don't know why it does that. When I deleted the 'main' file. The program seem to work. Also when I created another file within the same 'project', the problem seem to resurface. Can anyone explain to me what is going on? I am new to this C programming thing. 

Thanks fellas

As Queue29 hinted at, using Netbeans (or any other IDE) has nothing to do with (learning) C, and in fact, can encumber your learning progress.

If you want to learn C, then I would also suggest that you learn it by using a simple editor (gedit) or vim, and then compile the program using the command line.

If you insist on using Netbeans, then I would suggest that you put aside your notes (or textbook) on C, and instead focus on the documentation for Netbeans.

---

