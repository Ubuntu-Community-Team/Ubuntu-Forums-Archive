---
title: "Looking for a simple compiler"
date: 2007-04-02
forum: Programming Talk
---

### Post by M$LOL on 2007-04-02
I am looking for a simple c++/c compiler (cli or gui) that I can use for compiling .cpp files I have written using gedit. Just something simple, not an IDE or anything.

I have gcc, but I don't know enough about it to use it.

---

### Post by samjh on 2007-04-02
GCC is the best compiler for Unix/Linux.  You use g++ to compile C++ source code.

It's not difficult to learn to use.

To compile your cpp file, just type:
```
g++ *yourcppfile.cpp* -o *compiledbinary*
```

For example, if your cpp file was helloworld.cpp, and you wanted a binary executable named helloworld:
```
g++ helloworld.cpp -o helloworld
```

It's as easy as that!

You can also use the following additional options:

-Wall (enables all warnings, a good idea to enable this for all compilations)
-g (adds debugging symbols for use by a debugger, like gdb)
-s (reduces binary executable size)
-O1 or -O2 or -O3 (optimises your executable for speed, -O2 is usually the best)

---

### Post by M$LOL on 2007-04-02
Ok thanks. In g++ helloworld.cpp -o helloworld, is the -o one of the -O1 -O2 -O3 options, or is that something else?

Thanks for the help.

---

### Post by WW on 2007-04-02
To get the basic set of C/C++ compiling tools, install the **build-essential** package:
```

$ sudo apt-get install build-essential

```
This will provide gcc, g++, make, standard libraries, and some other stuff.

---

### Post by raul_ on 2007-04-02
g++ is gcc for c++. just use it as u use gcc.

"-o <execfile>" is to create the executable file

EDIT: i just read that u never used gcc.

Basically you can do

gcc -c file.c file2.c ....fileN.c

And that will create the *.o files (something between the source and the executable)

Then you can do

gcc -o <executablename> file.o file2.o ... fileN.o


and that creates your exec file, that u can run with "./execname"

to skip the *.o part, you can do directly

gcc -o <execname> file1.c file2.c ....fileN.c

if you don't specify a exec name, your program will be compiled into "a.out" , the very creative name that the Gnu developers came with :P


Before (or after) those flags, you can also set flags like -Wall (turn on all warnings) or -ansi (check for ansi standards or something like that). For example:

gcc -o test test.c -Wall -ansi

or

gcc -Wall - ansi -o test test.c

---

### Post by samjh on 2007-04-02
> **M$LOL said:**
> Ok thanks. In g++ helloworld.cpp -o helloworld, is the -o one of the -O1 -O2 -O3 options, or is that something else?

Thanks for the help.

-o stands for "output file".  The commands are case sensitive.  Notice that the -O1 -O2 and -O3 commands use capital O.  -o is lower case o.

---

