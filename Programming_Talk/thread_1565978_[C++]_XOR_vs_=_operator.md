---
title: "[C++] XOR vs = operator"
date: 2010-09-01
forum: Programming Talk
---

### Post by xnerdx on 2010-09-01
I've got a question, I'm learning ASM and found out that XOR is a faster method of setting a variable = to 0. Does the same go for C++? CPU wise, which of the following is faster?
int foo;
1) foo = 0;
or
2) foo ^= foo;

Thanks :D

---

### Post by dv3500ea on 2010-09-01
I'd say the difference in speed was negligible, especially in real life programming where input/output tends to be the bottleneck.

---

### Post by trent.josephsen on 2010-09-01
Maybe, but don't do it.  It's ugly, saves no real time (nanoseconds if any), and any decent optimizing compiler should take advantage of such an operation if it exists.  Higher level languages exist so that you don't have to resort to stupid tricks like this.

---

### Post by splicerr on 2010-09-01
Yeah the compiler will take care of that. Not something you have to worry about.

---

### Post by xnerdx on 2010-09-01
Thanks for the replies! Looking to speed up a large C++ program and thought that may be a possible way to do so.

---

### Post by ibuclaw on 2010-09-01
> **xnerdx said:**
> Thanks for the replies! Looking to speed up a large C++ program and thought that may be a possible way to do so.

There are much more elegant ways to do so...


If you really must know which areas are slowing you down the most. Ever tried profiling?
Compile your project with the -pg flag, then run it with gprof.
```
gprof ./myapp -- [OPTIONS]
```

---

### Post by xnerdx on 2010-09-01
Just to make sure I'm understanding you correctly, would the following be appropriate syntax to do that:
```

g++ -pgo foo foo.cpp
gprof ./foo

```

---

### Post by ibuclaw on 2010-09-01
Separate -pg and -o
```

g++ -pg -o foo foo.cpp
gprof ./foo

```

---

### Post by xb12x on 2010-09-01
How do you know that the XOR instruction is a faster method of setting a variable = to 0? 

Way back when games were written for DOS (16bit real mode) you could get Intel's 'Instruction Set Reference' and look up the amount of CPU clocks for instructions. And way back then the XOR instruction was a few clocks quicker. And that could make a difference when games were written in assembly to run on the processors of that era (when the world was new). 

Years of intense research and design have made modern processors tremendously more complex and _magnitudes_ faster. Intel no longer makes the effort to make clock counts available. It would be a waste of time as nobody would make use of the information. Nothing practical is written in assembly anymore. And even if something were written in  assembly, unless it's running in 16bit real mode there is way to much other stuff going on. It would be like one less grain of sand on a beach.

Even the PC BIOS, written in assembly since the beginning, is currently being replaced by EFI which is written in 'C'. 

Learning assembly might be fun but for the most part it serves no practical purpose anymore.

---

### Post by schauerlich on 2010-09-01
> **trent.josephsen said:**
> Maybe, but don't do it.  It's ugly, saves no real time (nanoseconds if any), and any decent optimizing compiler should take advantage of such an operation if it exists.  Higher level languages exist so that you don't have to resort to stupid tricks like this.

+1

> **xnerdx said:**
> Thanks for the replies! Looking to speed up a large C++ program and thought that may be a possible way to do so.

0) Make sure your program works. If not, make it work. Don't skip this step.
1) Decide if you really need to optimize (you probably don't)
2) Decide where you need to optimize (use a profiler, look for tight loops)
3) Think for a while about the problem
4) Find a better algorithm
5) If it's not significantly faster and you still care, GOTO 3
6) If you're bored and have nothing better to do, or you're writing performance critical code, try some micro-optimizations like this. But be warned, a lot of it will probably be wasted effort, as decent modern compilers already make these sorts of optimizations better than you can.

---

### Post by worksofcraft on 2010-09-01
Alas I turfed out my old x86 processor reference manual as it was out of data, but keep in mind that you may be wasting your time because compilers do their own optimization.

Besides fetching the instruction, an exclusive-or requires to read the data from memory do the operation then write it back.

To write a constant value (like 0) requires reading the address where the number is stored, reading the value of that number, then writing it to the variable, so it is potentially slower.

OTOH I think x86 processors have a 'clr' instruction and that simply writes the zero to your memory location and so it is fastest.

It depends if the compiler is clever enough to realize it can use a clr instruction because in this case the value is zero, or if it uses a generic code of setting a location to a specified value that could be zero or something else.

---

### Post by xnerdx on 2010-09-01
> **xb12x said:**
> Learning assembly might be fun but for the most part it serves no practical purpose anymore.

The purpose to learning ASM is to gain a better understand of low-level instructions. Therefore making programming in a high-level language much easier and easier to understand. To quote the article I'm reading:
"What is the Purpose of Learning Assembly?

This is a very important question and subject to a lot of discussion. My answer to this question is a list of reasons, really. Better understanding of what goes on at the lowest level can make you a better programmer at a higher level. It allows you to see what goes on behind the scenes and it often gives you a totally new perspective on things. It has its uses in writing high performance parts of high level language programming where you need to use features of your processor that are not easily accessible in that high level language. Knowing assembly is obviously also necessary to be able to write compilers for a particular microprocessor architecture which convert high level language code to machine instructions."
Source: [http://siyobik.info/index.php?document=x86_32bit_asm](http://siyobik.info/index.php?document=x86_32bit_asm)

---

### Post by xb12x on 2010-09-01
Well, you might be correct about learning assembly, Xnerdx. 

But I view learning assembly the same way I would view learning to use a slide rule. I'm sure you could find a college professor that would tell you all the great things you would learn when learning to use a slide rule. But I really do believe it's of no practical use today, really from a bygone era, and my time could be much better spent.

I spent a career writing code, much of it assembly.

---

### Post by lisati on 2010-09-01
My $0.02:
In the interests of program clarity, don't use XOR in a [HLL]("http://en.wikipedia.org/wiki/High-level_programming_language") to set a varibale to zero. Some day, a programming noob might come by and want to maintain, adapt or learn from your code, and have a "What the.....?" moment. 

As others have said, any optimizing compiler that's worth its salt will take advantage of such a trick if its warranted, and might actually have better ways of achieving the same result.

---

### Post by NovaAesa on 2010-09-02
> **schauerlich said:**
> +1



0) Make sure your program works. If not, make it work. Don't skip this step.
1) Decide if you really need to optimize (you probably don't)
2) Decide where you need to optimize (use a profiler, look for tight loops)
3) Think for a while about the problem
4) Find a better algorithm
5) If it's not significantly faster and you still care, GOTO 3
6) If you're bored and have nothing better to do, or you're writing performance critical code, try some micro-optimizations like this. But be warned, a lot of it will probably be wasted effort, as decent modern compilers already make these sorts of optimizations better than you can.

I would put your number 4 point after point number 1. No amount of (constant speed up) optimization is going to deliver better performance compared to a better algorithm for large N. And it's often much much easier to come up with a better algorithm (especially if someone has already invented it!) than it is to perform optimizations.

---

### Post by schauerlich on 2010-09-02
> **NovaAesa said:**
> I would put your number 4 point after point number 1. No amount of (constant speed up) optimization is going to deliver better performance compared to a better algorithm for large N. And it's often much much easier to come up with a better algorithm (especially if someone has already invented it!) than it is to perform optimizations.

Well, you need to know where you're optimizing and think about the problem a little bit in order to find that better algorithm. Or in lieu of thinking about it, google it (more likely, people are lazy)

---

### Post by nvteighen on 2010-09-02
> **xnerdx said:**
> The purpose to learning ASM is to gain a better understand of low-level instructions. Therefore making programming in a high-level language much easier and easier to understand. To quote the article I'm reading:
"What is the Purpose of Learning Assembly?

This is a very important question and subject to a lot of discussion. My answer to this question is a list of reasons, really. Better understanding of what goes on at the lowest level can make you a better programmer at a higher level. It allows you to see what goes on behind the scenes and it often gives you a totally new perspective on things. It has its uses in writing high performance parts of high level language programming where you need to use features of your processor that are not easily accessible in that high level language. Knowing assembly is obviously also necessary to be able to write compilers for a particular microprocessor architecture which convert high level language code to machine instructions."
Source: [http://siyobik.info/index.php?document=x86_32bit_asm](http://siyobik.info/index.php?document=x86_32bit_asm)

It's untrue because the higher-level you get, the less important is how things are implemented and the more important is to know what each element's purpose is.

A simple example: Do you really care if in C the = operator is implemented using XOR the way you say or not? No, you just want it to assign some value to something and you don't care how it does that.

---

### Post by Shippou on 2010-09-02
I do believe this is very related to this:

[http://en.wikipedia.org/wiki/XOR_swap_algorithm](http://en.wikipedia.org/wiki/XOR_swap_algorithm)

See the section "Reasons for avoidance in practice".

---

### Post by lisati on 2010-09-02
> **Shippou said:**
> I do believe this is very related to this:

[http://en.wikipedia.org/wiki/XOR_swap_algorithm](http://en.wikipedia.org/wiki/XOR_swap_algorithm)

**See the section "Reasons for avoidance in practice".**

Good call.

---

### Post by pbrane on 2010-09-02
for what it's worth:
```

(gdb) list
1	#include <cstdio>
2	
3	int main(void)
4	{
5		int foo;
6		foo ^= foo;
7		
8		printf("FOO: %d\n", foo + 1);
9		
10		return 0;
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000400604 <+0>:	push   rbp
   0x0000000000400605 <+1>:	mov    rbp,rsp
   0x0000000000400608 <+4>:	sub    rsp,0x10
   0x000000000040060c <+8>:	mov    DWORD PTR [rbp-0x4],0x0
   0x0000000000400613 <+15>:	mov    eax,DWORD PTR [rbp-0x4]
   0x0000000000400616 <+18>:	add    eax,0x1
   0x0000000000400619 <+21>:	mov    esi,eax
   0x000000000040061b <+23>:	mov    edi,0x40072c
   0x0000000000400620 <+28>:	mov    eax,0x0
   0x0000000000400625 <+33>:	call   0x4004f0 <printf@plt>
   0x000000000040062a <+38>:	mov    eax,0x0
   0x000000000040062f <+43>:	leave  
   0x0000000000400630 <+44>:	ret    
End of assembler dump.
(gdb) list
1	#include <cstdio>
2	
3	int main(void)
4	{
5		int foo;
6		foo ^= foo;
7		
8		printf("FOO: %d\n", foo + 1);
9		
10		return 0;
(gdb)

(gdb) list
1	#include <cstdio>
2	
3	int main(void)
4	{
5		int foo = 0;
6		
7		printf("FOO: %d\n", foo + 1);
8		
9		return 0;
10	}
(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000400604 <+0>:	push   rbp
   0x0000000000400605 <+1>:	mov    rbp,rsp
   0x0000000000400608 <+4>:	sub    rsp,0x10
   0x000000000040060c <+8>:	mov    DWORD PTR [rbp-0x4],0x0
   0x0000000000400613 <+15>:	mov    eax,DWORD PTR [rbp-0x4]
   0x0000000000400616 <+18>:	add    eax,0x1
   0x0000000000400619 <+21>:	mov    esi,eax
   0x000000000040061b <+23>:	mov    edi,0x40072c
   0x0000000000400620 <+28>:	mov    eax,0x0
   0x0000000000400625 <+33>:	call   0x4004f0 <printf@plt>
   0x000000000040062a <+38>:	mov    eax,0x0
   0x000000000040062f <+43>:	leave  
   0x0000000000400630 <+44>:	ret    
End of assembler dump.
(gdb)

```

on Lucid 64-bit it appears to generate the same assembly regardless. The source was compiled with 
```

g++ -Wall -W -g -o foo main.cxx

```

when the source is compiled with
```

g++ -Wall -W **-O2** -o foo main.cxx

```
```

(gdb) disassemble main
Dump of assembler code for function main:
   0x0000000000400630 <+0>:	sub    rsp,0x8
   0x0000000000400634 <+4>:	mov    edx,0x1
   0x0000000000400639 <+9>:	mov    esi,0x40074c
   0x000000000040063e <+14>:	mov    edi,0x1
   0x0000000000400643 <+19>:	**xor    eax,eax**
   0x0000000000400645 <+21>:	call   0x400510 <__printf_chk@plt>
   0x000000000040064a <+26>:	xor    eax,eax
   0x000000000040064c <+28>:	add    rsp,0x8
   0x0000000000400650 <+32>:	ret    
End of assembler dump.

```

---

