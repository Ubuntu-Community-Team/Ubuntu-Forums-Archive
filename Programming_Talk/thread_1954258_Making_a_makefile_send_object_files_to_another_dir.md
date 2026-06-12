---
title: "Making a makefile send object files to another directory?"
date: 2012-04-07
forum: Programming Talk
---

### Post by Jamie_Edwards on 2012-04-07
Hi guys.

I'm following a tutorial on how to make an OS but it's all in one directory and that directory is getting very messy. Luckily a makefile is used to compile and link all the source files ( which are a mix of .c and .s files ).

Because the single directory is getting messy I decided to try and modify the makefile to compile and link each source file in separate directories and then sending the resulting .o files to another directory, and then link those .o files into a 'kernel' file.

The compiling part works fine. But when it comes to linking the object files together I get the following errors:

```

ld: cannot find obj/boot.o: No such file or directory
ld: cannot find obj/main.o: No such file or directory

```

Which is telling me that the makefile isn't sending the .o files into their own directory which is also then preventing ld to link the files together to make 'kernel'.

So here is my question... How do I tell the makefile to move the .o files into the obj directory?

Here is my current makefile:

```

C_SOURCES= main.c
S_SOURCES= boot.s
C_OBJECTS=$(patsubst %.c, obj/%.o, $(C_SOURCES))
S_OBJECTS=$(patsubst %.s, obj/%.o, $(S_SOURCES))
CFLAGS=-nostdlib -nostdinc -fno-builtin -fno-stack-protector -m32 -Iheaders
LDFLAGS=-Tlink.ld -melf_i386 --oformat=elf32-i386
ASFLAGS=-felf

all: kern/kernel

.PHONY: clean
clean:
	-rm -f kern/kernel

kern/kernel: $(S_OBJECTS) $(C_OBJECTS)
	ld $(LDFLAGS) -o $@ $^

$(C_OBJECTS): obj/%.o : %.c 
	gcc $(CFLAGS) $<

vpath %.c source

$(S_OBJECTS): obj/%.o : %.s
	nasm $(ASFLAGS) $<

vpath %.s asem

```

---

### Post by Jamie_Edwards on 2012-04-07
I just solved it XD it just needed me to put -o $@ in the $(C_OBJECT) and (S_OBJECT) commands :L

---

