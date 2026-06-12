---
title: "C setup in netbeans"
date: 2010-06-28
forum: Programming Talk
---

### Post by qedprigmosynois on 2010-06-28
Sorry, im pretty new to C/ C++ but i was hoping if someone could tell me what is wrong with my code/IDE which is cygwin compiler in Netbeans.
I wrote a basic helloworld source code as following:
#include <stdio.h>

int main(void)
{
    printf("Hello World");
    return 0;
}

but i get this
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/Cygwin_1-Windows/helloworld.exe
make[2]: Entering directory `/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld'
mkdir -p dist/Debug/Cygwin_1-Windows
g++.exe     -o dist/Debug/Cygwin_1-Windows/helloworld build/Debug/Cygwin_1-Windows/main.o build/Debug/Cygwin_1-Windows/helloworld.o  
build/Debug/Cygwin_1-Windows/helloworld.o: In function `main':
/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld/helloworld.c:4: multiple definition of `_main'
build/Debug/Cygwin_1-Windows/main.o:/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld/main.cpp:15: first defined here
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/Cygwin_1-Windows/helloworld.exe] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2
make[2]: Leaving directory `/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld'
make[1]: Leaving directory `/cygdrive/c/Users/username/Documents/NetBeansProjects/helloworld'

BUILD FAILED (exit value 2, total time: 1s)

any help would be appreciated.
Thank you

---

### Post by Some Penguin on 2010-06-28
Why are you including two object files but showing only a single source file?

---

### Post by qedprigmosynois on 2010-06-28
i have two object files? o_O
wait where do you see that
make 1 and 2?

---

### Post by trent.josephsen on 2010-06-28
```
g++.exe -o dist/.../helloworld build/.../main.o build/.../helloworld.o
```

You're linking two object files, main.o and helloworld.o, into a single executable.  I'm guessing Netbeans set up one of them for you with a skeletal main() method, and you created another file with your own main().  Hence the redefinition.  I suggest not using Netbeans.

---

### Post by qedprigmosynois on 2010-06-28
ah really grateful for your help! :D
i found out what it was which is that netbeans offered to make me a main when i created a new project and i turned that option on....how silly of me 
but honestly if not netbeans what IDE would you recommend?

---

### Post by trent.josephsen on 2010-06-28
For learning I personally recommend writing code with a plain editor and compiling it from the command line.  IDEs really shine in enterprise level environments and where a lot of automation needs to be done for every build, but it's as valuable to know how to explicitly invoke the compiler.  YMMV, and others on the forum will probably disagree.

```
$ cat hello.c
#include <stdio.h>

int main(void)
{
    printf("Hello World\n");
    return 0;
}
$ gcc -W -Wall -ansi -pedantic -o hello hello.c
$ ./hello
Hello World
```

---

