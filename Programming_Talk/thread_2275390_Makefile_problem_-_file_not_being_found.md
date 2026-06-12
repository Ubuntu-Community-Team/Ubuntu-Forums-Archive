---
title: "Makefile problem - file not being found"
date: 2015-04-25
forum: Programming Talk
---

### Post by latte123 on 2015-04-25
Hi all - 

 I'm doing a small operating system using the code from the tutorial on the brokenthorn.com website. Unfortunately that tutorial doesn't include a makefile so I'm having to do that myself.  

The code is on Github here - 
[https://github.com/mooseman/plan_42/tree/master/p42](https://github.com/mooseman/plan_42/tree/master/p42) 

I've created a makefile but I'm getting this error message - 

andy@obsidian ~/plan_42/p42 $ make
nasm  -f elf -F stabs  Boot1.asm
nasm: fatal: unable to open input file `Boot1.asm'
make: *** [Boot1.o] Error 1 

Ok, so it's not finding that file - that's my problem.  

Here's the makefile as it is at the moment. I should say that I'm awful at makefiles so my answer to a "why did you do that?" question is likely to be "I don't know.".... :)  

CC      = g++
LD     = g++
NASM    = nasm 
 

CFLAGS  = -Wall -Wextra -Wno-missing-field-initializers -m32 -O3 -std=c99 
LDFLAGS = -m32
NASMFLAGS = -f elf -F stabs 


PROG = p42

OBJS = Boot1.o Stage2.o $(PROG).o cpu.o dma.o gdt.o hal.o idt.o 


#default: $(PROG)
all:    $(PROG)

$(PROG): $(OBJS)
    $(LD) $(LFLAGS) $(OBJS)  -o $(PROG)

Boot1.o: Boot1.asm
    $(NASM) $(NASMFLAGS) Boot1.asm

Stage2.o: Stage2.asm
    $(NASM) $(NASMFLAGS) Stage2.asm


cpu.o:    cpu.cpp
    $(CC) $(CFLAGS) cpu.cpp

dma.o:    dma.cpp
    $(CC) $(CFLAGS) dma.cpp        

gdt.o:    gdt.cpp
    $(CC) $(CFLAGS) gdt.cpp    

hal.o:    hal.cpp
    $(CC) $(CFLAGS) hal.cpp

idt.o:    idt.cpp
    $(CC) $(CFLAGS) idt.cpp


SUBDIRS = SysBoot/Stage1    \
        SysBoot/Stage2        \
        SysCore/Fat12        \
        SysCore/FloppyDisk    \
        SysCore/Hal        \
        SysCore/Include        \
        SysCore/Kernel        \
        SysCore/Keyboard    \
        SysCore/Lib        \
        SysCore/proc

VPATH = %.cpp %.c %.asm $(SUBDIRS)


P42SOURCES = cpu.cpp dma.cpp gdt.cpp hal.cpp idt.cpp pic.cpp pit.cpp tss.cpp user.cpp fat12.cpp flpydsk.cpp joco.cpp entry.cpp exception.cpp fsys.cpp main.cpp mmngr_phys.cpp mmngr_virtual.cpp panic.cpp sysapi.cpp task.cpp vmmngr_pde.cpp vmmngr_pte.cpp kybrd.cpp cstd.cpp ctype.c stdio.cpp string.cpp 

#   ##########

So..... if someone familiar with makefiles is able to help here, that would be very much appreciated!  Many thanks in advance - 
- latte123

---

### Post by TheFu on 2015-04-26
Please use "code tags" when posting code/commands/output in these forums - also, Makefiles are highly sensitive to tab vs spaces. Using a tab is mandatory for any lines that build targets. Be certain your "editor" isn't helping by swapping tabs for spaces or inserting tabs for some number of spaces.

Also, you can have any file as a makefile - just use **make -f whatever-name-for-makefile-that-you-like**
Like JCL - most people find a simple example makefile and use that as a template. You should do the same. Be certain you download it, not copy/paste - so the tabs don't get screwed.

Most people would use generic source-->targets for .asm.o and .c.o and .cxx.o - not specific ones like you are showing.

It has been about 15 yrs since I worked in any detail on makefiles, so I can't really help much more.  There is a gnu makefile tutorial, methinks too. Google should find it.

---

### Post by steeldriver on 2015-04-26
Is the github yours or a 3rd party? it looks like the source/asm files are in subdirectories, in which case make isn't going to know how to find them (you define SUBDIRS but don't appear to do anything with it)

If that's the case, probably the easiest thing is to move the makefile to the directory containing the files, and run it from there

---

### Post by latte123 on 2015-04-26
Hi again - 

  Thanks very much for your help TheFu and steeldriver!  

Sorry for not using the "code" tags..... d'oh.....  :)  

I'll try to do the generic source->target approach - that sounds good.  

I'll also do some more digging on how the "subdirs" thing in Make works.  
Yes, the repo shown is in fact mine.  

Thanks again - bye for now - 
- latte123

---

