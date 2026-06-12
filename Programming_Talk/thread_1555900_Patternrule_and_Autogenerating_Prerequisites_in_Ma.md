---
title: "Patternrule and Autogenerating Prerequisites in Makefile"
date: 2010-08-18
forum: Programming Talk
---

### Post by blade2008 on 2010-08-18
Hi,

I have a question about makefile pattern/generic rules and auto generating prerequisites.

Example: 

foo.o : test1.c header1.h header2.h
        $(CC) $(CFLAG) -c test1.c

How can I get the header files automatically included from test1.c into foo.o so that I do not need to mention them in the prerequisites?


And what is the pattern/generic rule for making a .o file from a .c file, when I have different .c files in different subdirectories. (Means: my .c files which I want to compile into .o files are in different directories)

Because, this rule is not working:

%.o : %.c
	$(CC) $(CFLAG) $(INCLUDES) -c $< -o $@ 

I get this error when making: No targets. Stop

I hope someone can help me

---

