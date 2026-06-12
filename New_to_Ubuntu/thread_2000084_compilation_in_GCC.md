---
title: "compilation in GCC"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by dharmes on 2012-06-09
I am a engg student,
I am learning programming in C.
Hence, i want to execute a program in Ubuntu 12.04,
after referring to a book.
i learned to write (in terminal),
.
gcc -g -O0 -Wall infilename.c -o outfilename.o
gdb outfilename.o
or
gcc -Wall infilename.c -o outfilename.o
.
also by reading the posts in internet,
they say to write
simply.

gcc infilename.c -o outfilename
./outfilename
or
gcc -Wall -W -Werror infilename.c -o outfilename
./outfilename
or
gcc filename.c
./a.out

which one should i choose and when,
please explain me.
in a lay-man's language

---

### Post by codemaniac on 2012-06-09
GCC is a very versatile compiler which comes with an avalanche of options .
The simplest steps involved to compile a basic C code is 

> gcc filename.c
./a.out

You can refer to the GCC man page for greater understanding on each options .
-Wall option gives you all the compilation warnings .
-o option produces the executable file and renames it as per your choice . 

If -o is not specified, the default is to put an executable file in a.out, the object file for source.suffix in source.o, its assembler file in source.s, a precompiled header file in source.suffix.gch, and all preprocessed C source on standard output.

Have the man page .

```
man gcc
```

---

### Post by codemaniac on 2012-06-09
Steps :

1.Open up a file called helloworld.c which will contain the source code , in an text editor (gedit/vim) .

2.place the below contents in the file , save and exit.

```
#include<stdio.h>
#include<unistd.h>

int main()
{
printf("Hello world\n");
}
```

3.compile the program using gcc .
gcc helloWorld.c

4. The above command line will produce an executable file called (a.out) .

5.run the executable in commandline .

```
./a.out
```

---

### Post by dharmes on 2012-06-09
> **codemaniac said:**
> GCC is a very versatile compiler which comes with an avalanche of options .
The simplest steps involved to compile a basic C code is 



You can refer to the GCC man page for greater understanding on each options .
-Wall option gives you all the compilation warnings .
-o option produces the executable file and renames it as per your choice . 

If -o is not specified, the default is to put an executable file in a.out, the object file for source.suffix in source.o, its assembler file in source.s, a precompiled header file in source.suffix.gch, and all preprocessed C source on standard output.

Have the man page .

```
man gcc
```
sir,
thanks for your help.
But is this  code sufficient for all my ENGG. level programs?

---

### Post by codemaniac on 2012-06-09
It was the simplest piece of code ever to get you started .
The ocean is endless my dear friend .

---

### Post by anewguy on 2012-06-09
As much as we may want to, and as much as you may want it, there is not a "covers all" gcc statement.  There are so many package libraries, etc., you might use, other compilation or link options you may need, etc., that it is impossible.  Usually it's a case-by-case basis.

If you are just starting, then the simplest of examples was given.  It says to compile and link the source helloworld.c and place the resulting executable in the default file name  - in this case it is a.out.

Suppose you want to keep your programs separate (real world, right?), then you would, in the simplest of examples:

gcc myprogram.c -o myprogram

to execute:

./myprogram from the command line


This is the most simplest way of specifying things.  As already mentioned, you really will need to read up on gcc, the various options, things like pkg-config, etc..  I'm no expert in this area - I've gotten mine to work and that's about it. 

But since you are just starting, start simple and work into your more difficult things later as they come up.

Dave ;)

---

