---
title: "Problem with running program using GCC"
date: 2013-07-01
forum: Programming Talk
---

### Post by theRandy on 2013-07-01
Ok so im trying to run the following code to show the different sizes of data types:
```
#include <stdio.h>

int main() {
    printf("The 'int' data type is\t\t %d bytes\n", sizeof(int));
    printf("The 'unsigned int' data type is\t %d bytes\n", sizeof(unsigned));
    printf("The 'short int' data type is\t %d bytes\n", sizeof(short int));
    printf("The 'long int' data type is\t %d bytes\n", sizeof(long int));
    printf("The 'long long int' data type is\t %d bytes\n", sizeof(long long int));
    printf("The 'float' data type is\t %d bytes\n", sizeof(float));
    printf("The 'char' data type is\t\t %d bytes\n", sizeof(char));
    }
```

when i try compile it with GCC i get the error message
```
root@bt:~/Documents/Programming# gcc datatype_sizes.c -fno-builtin -g
datatype_sizes.c: In function ‘main’:
datatype_sizes.c:10: error: expected declaration or statement at end of input
root@bt:~/Documents/Programming# 

```

and when i use ls -l a.out and then try to run the program using ./a.out it runs the wrong piece of code:
```
root@bt:~/Documents/Programming# gcc datatype_sizes.c -fno-builtin -g
datatype_sizes.c: In function ‘main’:
datatype_sizes.c:10: error: expected declaration or statement at end of input
root@bt:~/Documents/Programming# ls -l a.out
-rwxr-xr-x 1 root root 8471 2013-06-21 14:37 a.out
root@bt:~/Documents/Programming# ./a.out
Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 

Hello, world! 


```

Any idea why this is happening, ive never had this problem up until now with GCC.

---

### Post by sanderj on 2013-07-01
No problems here ...

sander@flappie:~$ gcc blabla.c 
sander@flappie:~$ ./a.out 
The 'int' data type is		 4 bytes
The 'unsigned int' data type is	 4 bytes
The 'short int' data type is	 2 bytes
The 'long int' data type is	 8 bytes
The 'long long int' data type is	 8 bytes
The 'float' data type is	 4 bytes
The 'char' data type is		 1 bytes
sander@flappie:~$

---

### Post by pmu on 2013-07-01
Hi,

Your a.out would be an executable of a previous code that you compiled.

Did you try compiling without the [COLOR=#000000][FONT=Ubuntu Mono]-fno-builtin -g ?
[/FONT][/COLOR]

---

### Post by sanderj on 2013-07-01
No, it can't be.
And yes, I just compiled like I posted; with a plain "gcc". See here again:

sander@flappie:~$ gcc blabla.c -o blablabla
sander@flappie:~$ ./blablabla 
The 'int' data type is		 4 bytes
The 'unsigned int' data type is	 4 bytes
The 'short int' data type is	 2 bytes
The 'long int' data type is	 8 bytes
The 'long long int' data type is	 8 bytes
The 'float' data type is	 4 bytes
The 'char' data type is		 1 bytes
sander@flappie:~$

---

### Post by theRandy on 2013-07-01
Yes i tried it with fno-builtin. without it i get more error messages:

```
root@bt:~/Documents/Programming# gcc datatype_sizes.c
datatype_sizes.c: In function ‘main’:
datatype_sizes.c:4: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:5: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:6: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:7: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:8: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:9: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:10: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
datatype_sizes.c:10: error: expected declaration or statement at end of input

```

---

### Post by theRandy on 2013-07-01
Ahhh never mind i screwed up and accidentally saved the same code twice one without a curly bracket at the end and one with on my desktop accidentally..... Working fine now:

```
root@bt:~/Documents/Programming# gcc -fno-builtin datatype_sizes.c
root@bt:~/Documents/Programming# ./a.out
The 'int' data type is         4 bytes
The 'unsigned int' data type is     4 bytes
The 'short int' data type is     2 bytes
The 'long int' data type is     8 bytes
The 'long long int' data type is     8 bytes
The 'float' data type is     4 bytes
The 'char' data type is         1 bytes

```

:redface: My bad

---

### Post by dwhitney67 on 2013-07-01
I'm not sure why you felt compelled to use the -fno-builtin option for such a trivial program.

The -g option is used to ensure that symbolic information is included within the produced executable; again, IMHO, unnecessary for your program.

The warning you got earlier regarding the "format '%d' expects ..." is due to the fact that you are attempting to print the value returned by sizeof(), which is not an int, but instead a long unsigned int.  You would be better off using '%lu' as your format statement in the printf() calls.

Lastly, why are you working as the root-user on your system?

---

### Post by trent.josephsen on 2013-07-01
sizeof gives a size_t, which happens to be an unsigned long for you, but you would do well to use the %zu specifier instead, which is defined by C99. You're relying on two C99 features already, as gcc will be happy to warn you if you compile with -pedantic, so use -std=c99 (or -std=c11) to make sure you don't run into any additional standard-related problems.

gcc by default compiles a bastardized version of C and enables no optional warnings. You will get much better diagnostics if you specify a language standard and ask for all the diagnostics. When I am compiling a lot from the command line, I alias cc to "gcc -std=c11 -pedantic -Wall -Wextra -Wwrite-strings" to save typing.

---

