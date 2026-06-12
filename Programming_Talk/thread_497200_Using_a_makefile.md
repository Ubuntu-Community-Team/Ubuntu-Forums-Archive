---
title: "Using a makefile"
date: 2007-07-10
forum: Programming Talk
---

### Post by TreeFinger on 2007-07-10
I am reading a book on programming in C.

It is getting into working on larger projects and showed how to make a simple little makefile.

I have never used a makefile before and the book is a little old.. it is from 1999 so I want to make sure I am doing everything right.

```

File: makefile.gcc

#-------------------------------------------------#
#	Makefile for Unix systems					  #
#	Using a GNU C compiler						  #
#-------------------------------------------------#
CC=gcc
CFLAGS=-g -D__USE_FIXED_PROTOTYPES__ -ansi
#
# Compiler flags:
#		-g	-- Enable debugging
#		-Wall	-- Turn on all warnings 
#		-D__USE_FIXED_PROTOTYPES__
#			-- Force the compiler to use the correct headers
#		-ansi	-- Don't use GNU extensions. Stick to ANSI C.

7-1: 7-1.c
	$(CC) $(CFLAGS) -o output 7-1.c

clean:
	rm -f output

```

In terminal I type:
```

$ make -f makefile.gcc
gcc -g -D__USE_FIXED_PROTOTYPES__ -ansi -o output 7-1.c
$

```

Is this makefile workable? I compiled the program before making the makefile with gcc so I don't think makefile will do it again.

---

### Post by Mr. C. on 2007-07-10
It is usable, but not quite correct.  You should also change the **-o output** to **-o 7-1**, and of course update your clean rule to use the correct name as well.

You'll want to make some changes when you have more than one source file.

You can test that it works:

```
touch 7-1.c
make -f makefile.gcc
```

or even

```
rm 7-1
make -f makefile.gcc
```

Do yourself a favor - rename makefile.gcc to Makefile, and then all you have to do is type:

```
make
```

MrC

---

### Post by Wim Sturkenboom on 2007-07-10
I have posted a universal makefile on [http://www.linuxquestions.org/questions/showthread.php?t=380437](http://www.linuxquestions.org/questions/showthread.php?t=380437) (post #4).
Only thing it does not do is descend into subdirectories (which would be very usefull for bigger projects).

---

### Post by TreeFinger on 2007-07-10
Mr. C.

Thanks for the tips. Everything is working great now, typing 'make' is a lot easier :guitar:

Is there anyway I could make my makefile automatically execute the new executable file after compiling if there are no errors?

---

### Post by Mr. C. on 2007-07-10
Sure, 

Change:

```
7-1: 7-1.c
	$(CC) $(CFLAGS) -o output 7-1.c
```

to 
```
7-1: 7-1.c
	$(CC) $(CFLAGS) -o output 7-1.c
        ./7-1
```

Your 7.1 command will run only after the previous CC command completes successfully.

MrC

---

