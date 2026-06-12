---
title: "C to ASM --Help please"
date: 2007-03-31
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-31
Hi, Well... As in the post down the page explains, I'm learning ASM through a combination of simple c programs dropped to ASM and a book. And I've just made my first simple C program (After reading a few tuts yesterday) and dropped it to ASM. I've noticed a lot of junk in the ASM that's dropped, but I've found the <main> and decided that is the only part I actually need to look at. If not, oh well.. I figure the otherparts are the C headers or whatever. 

Anyway, I have a few questions that hopefully one of you might be able to clear up for me.

So, I'll post the two sources of the programs
ASM Code:
```
0804832c <main>:
/* A simple loop program that runs through 1000 times.
Compile using gcc - loop -g -Wall loop.c and then dump to ASM (GAS x86)
using objdump loop -s */
int main ()
{
 804832c:       55                      push   %ebp
 804832d:       89 e5                   mov    %esp,%ebp
 804832f:       83 ec 18                sub    $0x18,%esp
 8048332:       83 e4 f0                and    $0xfffffff0,%esp
 8048335:       b8 00 00 00 00          mov    $0x0,%eax
 804833a:       83 c0 0f                add    $0xf,%eax
 804833d:       83 c0 0f                add    $0xf,%eax
 8048340:       c1 e8 04                shr    $0x4,%eax
 8048343:       c1 e0 04                shl    $0x4,%eax
 8048346:       29 c4                   sub    %eax,%esp
        int i;
        int j;
        j = 0;
 8048348:       c7 45 fc 00 00 00 00    movl   $0x0,0xfffffffc(%ebp)
        for (i =0; i < 1000; i++){
 804834f:       c7 45 f8 00 00 00 00    movl   $0x0,0xfffffff8(%ebp)
 8048356:       eb 12                   jmp    804836a <main+0x3e>
                j = i + 1 + j;
 8048358:       8b 45 fc                mov    0xfffffffc(%ebp),%eax
 804835b:       03 45 f8                add    0xfffffff8(%ebp),%eax
 804835e:       83 c0 01                add    $0x1,%eax
 8048361:       89 45 fc                mov    %eax,0xfffffffc(%ebp)
 8048364:       8d 45 f8                lea    0xfffffff8(%ebp),%eax
 8048367:       83 00 01                addl   $0x1,(%eax)
 804836a:       81 7d f8 e7 03 00 00    cmpl   $0x3e7,0xfffffff8(%ebp)
 8048371:       7e e5                   jle    8048358 <main+0x2c>
                }
return 0;
 8048373:       b8 00 00 00 00          mov    $0x0,%eax
}

```
C Code (Comment on it if it's not very good, it probably isn't)
```
/* A simple loop program that runs through 1000 times. 
Compile using gcc - loop -g -Wall loop.c and then dump to ASM (GAS x86)
using objdump loop -S */
int main ()
{
	int i;
	int j;
	j = 0;
	for (i =0; i < 1000; i++){
		j = i + 1 + j;
		}
return 0;
}
```

Ok, so my questions are these:
1. Where are the variables (i and j) declared?
2. Where can I find a list of *good* definitions of addl, mov and the rest of the (opcodes)?
3. When writing my own program in only ASM, do I need to manually assign a location in memory (0xffffff8 or whatever) my self, or would the assembler take care of this? If I do, how do I know what's free? (I don't think I would need to do it myself, as the memory locations change each time I run a program, correct?)
4. Where would I look for the meanings of (%ebp) and the like. I'd just google this but I'm not quite sure what they're called.

Yeah, I know. My book probably will go through all the things like this. But I'd rather get the hang of a few basics before reading a book. I just find it easier to do it like that. 

Also, is there any simple tutorials (I mean simple, too.... Just the basics of ASM like loops and what not) out there for GNU Linux x86 asm that you would recommend?

Thanks for looking at this and (hopefully) answering some of my questions.

P.S. As always, comment on my code if you think it's wrong.

---

### Post by smokey edgy on 2007-03-31
Hey darkness,

In my opinion, it might be a good idea for you to actually start with ASM first rather than making the relationship between C code and the output from the object files. Lots of tricks and optimizations are done which may obfuscate things quite a bit.

smokey

---

### Post by Wybiral on 2007-03-31
Compile the C program using the "-S" flag and it will generate an assembly file.

DON'T use a disassembler like that.

---

### Post by Darkness3477 on 2007-03-31
Wybrial: Ok, I've recompiled with the '-S' flag and now have a asm file, however. The asm file (when I open it in a text editor) makes even less sense to me. 

Also, why shouldn't I use a disassembler like that?

Smokey: I'd rather look at a C program in ASM for awhile so I can try to firgure out how it's doing what, then read the book I have. It just makes more sense for me to do it like that.

---

### Post by Wybiral on 2007-03-31
You shouldn't use a disassembler because you have access to the actual assembly code, NOT a disassemblers interpretation of the machine code.

The assembly produced by the "-S" flag is actually what the GCC assembler assembles, so you know that it is correct, functioning assembly code. Sometimes disassemblers produce funny things.

You should start off very simple... Compile something like...
```

int main()
{
   return 5;
}

```
And study that output.

But are are going to need a basic understanding of assembly first.

BTW, with GCC generated assembly files, you can assemble them using GCC!

gcc test.c -S

* Edit assembly here *

gcc test.s

* Now you have an executable! *

---

### Post by macogw on 2007-03-31
You shouldn't use the disassembler because GCC does "stuff" to the C when it compiles, and then the disassembler has to try to figure out what "stuff" it did.  It adds in optimizing code and reduces other things so that you don't have an exact representation of that C source (instead it's the binary) in ASM.

---

### Post by Darkness3477 on 2007-03-31
Righteo, then. I'll get a simple program and put it to asm to look at. This time with a reference open :D

Hopefully by the end of the day I'll have a very rudimentary understanding of ASM and perhaps be able to look at a few simple programs and figure out what they're doing. Somehow, I don't think i'll be able to today... but, it's good to hope.

---

### Post by rplantz on 2007-04-01
> **Darkness3477 said:**
> 
Also, is there any simple tutorials (I mean simple, too.... Just the basics of ASM like loops and what not) out there for GNU Linux x86 asm that you would recommend?


I think your general approach to learning assembly -- start from C -- is good. In fact, I am just writing the final chapter of my textbook that takes precisely this approach. (So I'm biased. :))

However, there is a fair amount of material that must be understood before just jumping into looking at the assembly code generated by gcc. To give you an idea, I start the process in Chapter 5 on page 87 in my book. And it takes me about 100 more pages to explain all the questions you have asked.

Anyway, I have used -S to generate the assembly language as has been suggested by others. Then I have commented the code according to my understanding of what's going on. (I did not write the compiler, so I can't be sure. :)) In my comments I end what could be C statements with the ';' character. Notice that it uses another C variable, "temp". The eax register is used for this variable.

```

main:
	leal	4(%esp), %ecx  # get address of return address
	andl	$-16, %esp     # put stack pointer on 16-byte boundary
	pushl	-4(%ecx)       # push return address onto stack
	pushl	%ebp           # save caller's base pointer
	movl	%esp, %ebp     # establish our base pointer
	pushl	%ecx           # save address of return address
	subl	$16, %esp      # allocate space for local variables (i and j)
	movl	$0, -8(%ebp)   # j = 0;
	movl	$0, -12(%ebp)  # i = 0;
	jmp	.L2            # goto bottom of loop
.L3:
	movl	-8(%ebp), %eax # temp = j;
	addl	-12(%ebp), %eax  # temp = i + j;
	addl	$1, %eax       # temp = temp + 1;
	movl	%eax, -8(%ebp) # j = temp;
	addl	$1, -12(%ebp)  # i++;
.L2:
	cmpl	$999, -12(%ebp) # compare i to 999
	jle	.L3            # if i <= 999, jump to top of loop
	movl	$0, %eax       # return 0;
	addl	$16, %esp      # delete local variables
	popl	%ecx           # retrieve address of return address
	popl	%ebp           # restore caller's base pointer
	leal	-4(%ecx), %esp # restore caller's stack pointer
	ret                    # back to caller

```
I think this code will convince you that the details are very tedious. I applaud your enthusiasm for wanting to learn this stuff. I hope you will be able to keep your enthusiasm going as you learn the (sometimes boring) basics that you will need later to really understand the new things you will be working on.

---

### Post by Darkness3477 on 2007-04-02
Hey, thanks for the encouragement. I'm not sure I'll get to the stage where I can just sit down and write a working (reasonably complex) program in Assembly, but I'd at least be able to understand it and write a few simple programs.

I also hope I'll be able to keep up my enthusiasm. Atleast this is the last week of the term, so I have very little homework to do, and none over the Holidays. Which means I should be able to pick up some stuff over my two week break... Whilst nursing a many a severe hangover.

Thanks for commenting the code for me, It's really helped a lot. Anyway, I'll just continue on reading the book and also looking at my programs. I'll recompile one of my more complex programs (Still not very complex.. mostly maths based stuff) and see exactly how much like gibberish that looks. :P

Anyway, thanks and bye.

---

