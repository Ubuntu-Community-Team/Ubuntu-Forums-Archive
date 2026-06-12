---
title: "Why does my make file feel the need to delete my objects?"
date: 2011-01-22
forum: Programming Talk
---

### Post by ownaginatious on 2011-01-22
So I have the following make file:

```

CC=gcc
CFLAGS= -m32 -Wall -pedantic

ASM=nasm
ASFLAGS= -f elf -d ELF_TYPE

.SUFFIXES: .out .asm .o

all: p2.out p3.out

.asm.o:
        $(ASM) $(ASFLAGS) $<

driver.o: driver.c
        $(CC) $(CFLAGS) -c -o $@ $?

%.out: driver.o asm_io.o %.o
        $(CC) $(CFLAGS) -o $@ $?

clean:
        rm *.o *.out

```

This is what I get when I run make -f makefile_p4.
```

gcc -m32 -Wall -pedantic -c -o driver.o driver.c
nasm -f elf -d ELF_TYPE asm_io.asm
nasm -f elf -d ELF_TYPE p2.asm
gcc -m32 -Wall -pedantic -o p2.out driver.o asm_io.o p2.o
nasm -f elf -d ELF_TYPE p3.asm
gcc -m32 -Wall -pedantic -o p3.out driver.o asm_io.o p3.o
[COLOR="Red"]rm asm_io.o p2.o p3.o[/COLOR]

```

Anyone have any idea why 'make' deletes those three object files when it's done? It makes no sense to me...

Thanks.

---

### Post by ownaginatious on 2011-01-22
Okay, I figured out the problem. Those files are considered intermediary, since nothing aside from the pattern requires them. I was able to solve the 'autodeletion' problem by adding them to the .SECONDARY rules.

Now I'm having another problem, and that's with my pattern:

```

%.out: driver.o asm_io.o %.o
        $(CC) $(CFLAGS) -o $@ $?

```

Now I think the problem is that make expects *all* patterns to be of the form "%.n : %.m" at the top level, where n and m are two extensions. The problem is though is that the files I'm generating from that must _also_ depend on driver.o and asm_io.

When I change the source code of asm_io.asm and try to recompile, I get the following:

```

[dillon@LINOOX Assembly Folder]$ make -f makefile_p4 
nasm -f elf -d ELF_TYPE asm_io.asm
gcc -m32 -Wall -pedantic -o p2.out asm_io.o
/usr/lib/gcc/x86_64-unknown-linux-gnu/4.5.2/../../../../lib32/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [p2.out] Error 1

```

Now as you can see, gcc _isn't_ getting the the three files I specified that anything matching the pattern should depend on! The stranger thing is that this problem appears to occur randomly... sometimes all three dependencies show up and the thing goes through fine, and other times 1 or 2 of the dependencies will randomly disappear :s.

Could someone please tell me a way to get around this? It's really beginning to drive me insane... It amazes me that there is literally zero information about this anywhere on the internet...

Thanks..

---

### Post by nvteighen on 2011-01-22
Try this:

```

CC=gcc
CFLAGS= -m32 -Wall -pedantic

ASM=nasm
ASFLAGS= -f elf -d ELF_TYPE

**.PHONY: clean**
.SUFFIXES: .out .asm .o

all: p2.out p3.out

.asm.o:
        $(ASM) $(ASFLAGS) $<

driver.o: driver.c
        $(CC) $(CFLAGS) -c -o $@ $?

%.out: driver.o asm_io.o %.o
        $(CC) $(CFLAGS) -o $@ $?

clean:
        rm *.o *.out

```

.PHONY tells GNU Make that clean isn't a file target, but a "function" (actually called a "phony target"). That should solve this. What I'm not sure is whether 'all' should also be .PHONY or not.

---

### Post by StephenF on 2011-01-22
> **nvteighen said:**
> .PHONY tells GNU Make that clean isn't a file target, but a "function" (actually called a "phony target"). That should solve this. What I'm not sure is whether 'all' should also be .PHONY or not.
Yes it should but what are the odds you would create a file called 'all' shortly after modifying your source code?

---

### Post by gmargo on 2011-01-22
I think you're running into problems because you're trying to combine target rule patterns with dependencies.

I would simplify the middle part of your Makefile to something more explicit like this:
```

all: p2.out p3.out

COMMONOBJS=driver.o asm_io.o

.asm.o:
        $(ASM) $(ASFLAGS) $<

.c.o:
        $(CC) $(CFLAGS) -c $<

p2.out: p2.o $(COMMONOBJS)
        $(CC) $(CFLAGS) $(LDFLAGS) -o $@ p2.o $(COMMONOBJS)

p3.out: p3.o $(COMMONOBJS)
        $(CC) $(CFLAGS) $(LDFLAGS) -o $@ p3.o $(COMMONOBJS)

```

---

### Post by Vox754 on 2011-01-22
> **ownaginatious said:**
> ...
Now I'm having another problem, and that's with my pattern:

```

%.out: driver.o asm_io.o %.o
        $(CC) $(CFLAGS) -o $@ $?

```

...

```

gcc -m32 -Wall -pedantic -o p2.out asm_io.o

```

Now as you can see, gcc **_isn't_ getting the the three files** I specified that anything matching the pattern should depend on!...

Could someone please tell me a way to get around this? It's really beginning to drive me insane... It amazes me that there is literally zero information about this anywhere on the internet...

Thanks..

In this case, you should use
```

%.out: driver.o asm_io.o %.o
	$(CC) $(CFLAGS) -o $@ $^  # <---

```

The variable "$?" means only the prerequisites that are newer than the target, but to create the executable you want all object files, thus "$^".

I don't think you need to browse a lot on the internet. Just read the GNU make manual, which is readily accessible as an info manual and html.

---

### Post by ownaginatious on 2011-01-22
> **Vox754 said:**
> The variable "$?" means only the prerequisites that are newer than the target, but to create the executable you want all object files, thus "$^".

I don't think you need to browse a lot on the internet. Just read the GNU make manual, which is readily accessible as an info manual and html.

Ahh, now I feel like an idiot - haha.... I even remember reading over that too :p.

Anyway, thanks a lot everyone! I really appreciate the the help. I'll have to keep all this '.PHONY' and '$^' stuff in mind for the future.

---

