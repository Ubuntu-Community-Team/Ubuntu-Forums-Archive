---
title: "makefile complaining of target patterns not matching?"
date: 2012-12-28
forum: Programming Talk
---

### Post by Jamie_Edwards on 2012-12-28
Hi guys,

I'm trying to make a makefile ( which I don't have much experience with ) and while making said program it spits out the following:

```

makefile:52:target '(' doesn't match the target pattern
makefile:52:target 'patsubst' doesn't match the target pattern
makefile:52: *** mixed implicit and static pattern rules. Stop.

```

Although I have very limited knowledge of make and makefiles, I do know that it's trying to tell me that there is something wrong on line 52 of the following makefile.

```

C_MAIN_SOURCE =main.c

# Make sure to add the likes of the directories arch and gui etc here too!

ASM_SOURCES =boot.asm

# Here are the object files for the sources above
C_MAIN_OBJECTS = ( patsubst %.c, obj/%.o, $(C_MAIN_SOURCE) )

# Make sure to add the object files for directories like "gui" etc...

ASM_OBJECTS = ( patsubst %.asm, obj/%.o, $(ASM_SOURCES) )

# Flags for the C and ASM compilers, and also for the Linker
CFLAGS = -c \
    -nostdlib \
    -nostdinc \
    -fno-builtin \
    -fno-stack-protector \
    -m32 \
    -Iinclude \
    -Wall \
    -Wextra
LDFLAGS = -Tlink.ld \
    -melf_i386 \
 #   --oformat = elf32-i386
ASFLAGS = -felf

# Compilers themselves
CC = gcc
ASC = nasm

# Now onto the compiling
all: kern/kernel

.PHONY: clean

clean:
	-rm -f obj/*.o, kern/kernel

# NB: C_GUI_OBJECTS ( if its going to be called that ) will need to go in here too!
kern/kernel: $(C_MAIN_OBJECT) $(ASM_SOURCE_OBJECTS)
	ld $(LDFLAGS) -o $@ $^
	@echo "Linking Everything for kernel"

$(C_MAIN_OBJECT): obj/%.o : core/%.c
	$(CC) $(CFLAGS) $< -o $@
	@echo "Completed main.c in \"core\""

vpath %.c core

-------------------------------------------
$(ASM_OBJECTS): obj/%.o : core/arch/%.asm
-------------------------------------------
	$(ASC) $(ASFLAGS) $< -o $@
	@echo "Completed all .asm files"

vpath %.asm core/arch/

```

NB: the "----" is line 52 by the way.

Only problem is... I don't see anything wrong with it! I've cross-referenced it with ASM_OBJECTS and also ASM_SOURCES and their almost identical. I can only guess that make doesn't like searching into subdirectories without being told so ( of which I have no clue in doing? )

The way I've set up my directories is as follows:
```

"CerOS"
    |
    "core" -- main.c
    |   |
    |    "arch" -- common.c, timer.c, boot.asm
    |
    "include" -- datetime.h, multiboot.h, system.h
    |    |
    |     "arch" -- common.h
    |
    "kern" -- kernel
    |
    |
    "obj" -- // where all the object files go
    |
    |
    makefile
    link.ld

```

NB: The ones with " " are the folders and the rest are the files within them "CerOS" is the root directory

If the problem with the makefile is the fact it hasn't delved into the second dir ( "arch" ) then how do I tell make to go into it? And if it isn't the problem, what is? And how can I fix it?

Thank you for your patience.

Jamie E.

---

### Post by dwhitney67 on 2012-12-29
Try changing the following statements:
```

# Here are the object files for the sources above
C_MAIN_OBJECTS = ( patsubst %.c, obj/%.o, $(C_MAIN_SOURCE) )

# Make sure to add the object files for directories like "gui" etc...

ASM_OBJECTS = ( patsubst %.asm, obj/%.o, $(ASM_SOURCES) )

```

to be:
```

# Here are the object files for the sources above
C_MAIN_OBJECTS = **$(patsubst %.c,obj/%.o,$(C_MAIN_SOURCE))**

# Make sure to add the object files for directories like "gui" etc...

ASM_OBJECTS = **$(patsubst %.asm,obj/%.o,$(ASM_SOURCES))**

```


P.S.  Your Makefile refers to 'obj' often; you should consider defining a variable, such as OBJDIR, for this.  That way should you ever need to change it, it can be done in one place.

---

### Post by Jamie_Edwards on 2012-12-29
Thank you, so pretty much remove the spaces.

Also for the "OBJDIR" do I just put 
OBJDIR = obj

?

Thanks

Jamie E.

---

