---
title: "how to make simple script to compile and run a CPP program"
date: 2007-10-08
forum: Programming Talk
---

### Post by EzarKun on 2007-10-08
Hi,

newbie here
I have a CPP file called: partD.cpp

I was wondering how to make a script, like a makefile or something, to compile it and run it too.

it should compile with the line

g++ partD.cpp -o partD.o

and run with

./partD.o

thanks, and its kind of urgent

---

### Post by CptPicard on 2007-10-08
Umm... how about...

```

#!/bin/bash

g++ partD.cpp -o partD.o
./partD.o

```

;)

---

### Post by EzarKun on 2007-10-08
hi, thanks for the reply

its for a school assignment and its my first time programming in a linux environment.

could you please tell me some more.

like what file i should place your script in and what is its file extention.

also how do i run the scipt in a terminal.

thanks

---

### Post by CptPicard on 2007-10-08
A text file named according to your choice, it doesn't matter. Linux also doesn't use file extensions as much as Windows does, but shell scripts are often named *.sh. So suppose you've got your file called "myscript.sh"... then you've got to make it executable

```

chmod +x myscript.sh

```

and then you can just run it in the shell by

```

./myscript.sh

```

Makefiles are a bit of a different animal, but some googling should help you with them...

---

### Post by EzarKun on 2007-10-08
thank you very much

---

### Post by j_g on 2007-10-09
I use very minimal make files for my projects. I use a couple "variables" to store the names of the source files, library/include files, etc.

For example, assume I have two source files named file1.c and file2.c and wish to create an executable named MyProgram. Also assume that I need to link with the X Windows library (X11).

```
# Add any needed libs here
LIBS=-lX11
# Add names of source files here
SOURCES=file1.c file2.c

CC=gcc 
LDFLAGS=-g
CFLAGS=-Wall

# Change MyProgram to the name of your executable
.PHONY: MyProgram
MyProgram: $(SOURCES)
 $(CC) $(CFLAGS) -o $@ $(LDFLAGS) $(SOURCES) $(LIBS)
```

Sometimes, you may need to specify include files (as well as libs) for extra libs you use, such as GTK include files. In this case, I think that it can be useful to use the pkg-config utility (with the --cflags and --libs options, to yield both the libs and include files) for a given extra lib. For example, if MyProgram used the libglade 2.0 lib, and GTK 2.0 libs, in addition to the X Windows lib, I may specify my LIBS line as so:

```
LIBS=`pkg-config --libs --cflags libglade-2.0` `pkg-config --libs --cflags gtk+-2.0` -lXt
```

If you name your make file as simply **makefile** then you can execute it (to compile MyProgram) by just typing make at the terminal.

Of course, this doesn't subsequently run the program, but you could substitute the command "make" for the line "g++ partD.cpp -o partD.o" in the above suggested shell script.

---

