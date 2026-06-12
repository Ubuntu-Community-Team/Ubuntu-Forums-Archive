---
title: "code::blocks ignores breakpoints"
date: 2013-09-27
forum: Programming Talk
---

### Post by ulli2 on 2013-09-27
Hello everybody,

I am using code::blocks 12.11 with gdb 7.6 in Ubuntu 13.04 and the following test program

```

#include <iostream>
#include <stdio.h>

using namespace std;

int main()
{
    int x = 15;
    int y = 7;
    int z = x/y;
    z=x+y*y;
    printf("Hello world! %i\n", z);
    return 0;
}

```

Compiler flag -g is enabled and -s is disabled in the Project´s Build options as well as the Compiler Settings.

**My problem is: Code::blocks ignores breakpoints and next line debug commands.** But sometimes debugging stops somewhere inbetween the breakpoints.

With Code::blocks 10.5, gdb 7.3 and ubuntu 11.10 everything works as expected.

It would be really great, if you had some other idea: I googled this problem for hours already and I am out of ideas.

Thank you a lot.



In case you need that:

Debugger log:

> 
Building to ensure sources are up-to-date
Selecting target: 
Debug
Adding source dir: /home/ulli/Desktop/test/Test/
Adding source dir: /home/ulli/Desktop/test/Test/
Adding file: /home/ulli/Desktop/test/Test/bin/Debug/Test
Changing directory to: /home/ulli/Desktop/test/Test/.
Set variable: LD_LIBRARY_PATH=.:
Starting debugger: /usr/bin/gdb -nx -fullname  -quiet  -args /home/ulli/Desktop/test/Test/bin/Debug/Test
done
Registered new type: wxString
Registered new type: STL String
Registered new type: STL Vector
Setting breakpoints
Debugger name and version: GNU gdb (GDB) 7.5.91.20130417-cvs-ubuntu
At /home/ulli/Desktop/test/Test/main.cpp:15
Continuing...
At /home/ulli/Desktop/test/Test/main.cpp:15
Continuing...
[Inferior 1 (process 4686) exited normally]
Debugger finished with status 0


Build log

> 
g++ -Wall -fexceptions  -g  -g -L/usr/lib64/ -lmkl_lapack64 -lmkl -lguide -lpthread -lm   -O3   -I/usr/include -I/usr/lib/lapack  -c /home/ulli/Desktop/test/Test/main.cpp -o obj/Debug/main.o
g++ -L/usr/lib -L/usr/lib/lapack  -o bin/Debug/Test obj/Debug/main.o    
Output size is 16,47 KB
Process terminated with status 0 (0 minutes, 0 seconds)
0 errors, 0 warnings (0 minutes, 0 seconds)


---

### Post by lisati on 2013-09-27
*Thread moved to **Programming Talk**.*

---

### Post by dwhitney67 on 2013-09-28
This is a an unusually complex build statement for such a "trivial" program:
```

g++ -Wall -fexceptions -g -g -L/usr/lib64/ -lmkl_lapack64 -lmkl -lguide -lpthread -lm -O3 -I/usr/include -I/usr/lib/lapack -c /home/ulli/Desktop/test/Test/main.cpp -o obj/Debug/main.o

g++ -L/usr/lib -L/usr/lib/lapack -o bin/Debug/Test obj/Debug/main.o 

```
Perhaps if you turned of the optimizer (-O3) the debugger would be able to honor your breakpoint requests.  Also, the -L and -l (lowercase ell) are not necessary when you compile a program; they're sometimes necessary when linking one or more object files in order to reference external libraries.

Btw, for your program, the following should suffice:
```

g++ -Wall -c /home/ulli/Desktop/test/Test/main.cpp -o obj/Debug/main.o

g++ -o bin/Debug/Test obj/Debug/main.o 

```

P.S.  I recommend that you learn to build your programs from the command-line, and debug them too using either 'gdb' or 'ddd' (which is a GUI front-end to 'gdb').  Using code::blocks, or any other IDE, at your level of programming competence is a disservice.

P.S. #2  Choose carefully if you plan to develop in C, or in C++... they are not the same.
```

//#include <iostream>   Not necessary; never used.
#include <cstdio>    // For C++, include cstdio, not stdio.h

using namespace std;

int main()
{
    int x = 15;
    int y = 7;
    int z = x/y;
    z=x+y*y;
    printf("Hello world! %i\n", z);

    // return 0;    Not necessary for C++ programs; the return value of 0 is implicit.
}

```

---

