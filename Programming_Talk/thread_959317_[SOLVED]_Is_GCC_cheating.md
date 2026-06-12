---
title: "[SOLVED] Is GCC cheating?"
date: 2008-10-26
forum: Programming Talk
---

### Post by cl333r on 2008-10-26
Hi folks,
I just found out that the code below takes a blink of an eye to execute, do you think GCC is cheating under the hood? How can it possible do that that fast (much less than a second)? I tested same code in Java and it goes on and on until I shut down the process which is the behavior I expected.

What's interesting is that the C code actually prints in the end "2000000000" for the "k" variable which kinda proves that it actually did execute loop.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char **argv) {

	int iCount = 2000000000;
	int x = 0;
	int i, j, k;
	puts( "starting");

	for( i=0; i<iCount; i++ ) {
		for( j=0; j<iCount; j++ ) {
			for( k=0; k<iCount; k++ ) {
				x = i-i-j+j-k+k;
				x++;
			}
		}
	}

	printf( "done, x=%d, k=%d\n", x, k );
	return 0;
}


```

---

### Post by ssam on 2008-10-26
it is probably optimising it out. what optimise options are you using?
[http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html) for lots of details.

i'd guess that "x = i-i-j+j-k+k;" gets drops, as it has no effect ever. then it must work out the effect of 2000000000^3 loops.

what happens if you read iCount from the user at run time?

---

### Post by cl333r on 2008-10-26
I dropped all math operations from inside the loop and all is left is the loops themselves and yet Java still can't run code till the end.
I think GCC just somehow skips the loop, it can't possible execute 2000000000*2000000000*2000000000 loops in a blink of an eye.. which makes me think gcc is a lot better optimized for loops (than Java).

---

### Post by Npl on 2008-10-26
IF you call optimization cheating,then yes GCC is a cheater.
The easiest way to keep GCC from optimizing away the loop is to add some inline asm. insert that in your inner loop: ```
asm volatile ( "nop" );
```

---

### Post by kknd on 2008-10-26
Maybe you can try to compile without optimizations (-O0) and compare the results.

---

### Post by Game_Ender on 2008-10-26
I ran and compiled both with and without optimizations.  GCC complete removes the loop from program if you crank up the optimizations all the way.  Basically its smart enough to determine the result of the loop without running it.

No optimizations:```

0x080483a4 <main+0>:	lea    0x4(%esp),%ecx
0x080483a8 <main+4>:	and    $0xfffffff0,%esp
0x080483ab <main+7>:	pushl  -0x4(%ecx)
0x080483ae <main+10>:	push   %ebp
0x080483af <main+11>:	mov    %esp,%ebp
0x080483b1 <main+13>:	push   %ecx
0x080483b2 <main+14>:	sub    $0x34,%esp
0x080483b5 <main+17>:	movl   $0x77359400,-0x8(%ebp)
0x080483bc <main+24>:	movl   $0x0,-0xc(%ebp)
0x080483c3 <main+31>:	movl   $0x8048510,(%esp)
0x080483ca <main+38>:	call   0x804830c <puts@plt>
0x080483cf <main+43>:	movl   $0x0,-0x10(%ebp)
0x080483d6 <main+50>:	jmp    0x8048411 <main+109>
0x080483d8 <main+52>:	movl   $0x0,-0x14(%ebp)
0x080483df <main+59>:	jmp    0x8048405 <main+97>
0x080483e1 <main+61>:	movl   $0x0,-0x18(%ebp)
0x080483e8 <main+68>:	jmp    0x80483f9 <main+85>
0x080483ea <main+70>:	movl   $0x0,-0xc(%ebp)
0x080483f1 <main+77>:	addl   $0x1,-0xc(%ebp)
0x080483f5 <main+81>:	addl   $0x1,-0x18(%ebp)
0x080483f9 <main+85>:	mov    -0x18(%ebp),%eax
0x080483fc <main+88>:	cmp    -0x8(%ebp),%eax
0x080483ff <main+91>:	jl     0x80483ea <main+70>
0x08048401 <main+93>:	addl   $0x1,-0x14(%ebp)
0x08048405 <main+97>:	mov    -0x14(%ebp),%eax
0x08048408 <main+100>:	cmp    -0x8(%ebp),%eax
0x0804840b <main+103>:	jl     0x80483e1 <main+61>
0x0804840d <main+105>:	addl   $0x1,-0x10(%ebp)
0x08048411 <main+109>:	mov    -0x10(%ebp),%eax
0x08048414 <main+112>:	cmp    -0x8(%ebp),%eax
0x08048417 <main+115>:	jl     0x80483d8 <main+52>
0x08048419 <main+117>:	mov    -0x18(%ebp),%eax
0x0804841c <main+120>:	mov    %eax,0x8(%esp)
0x08048420 <main+124>:	mov    -0xc(%ebp),%eax
0x08048423 <main+127>:	mov    %eax,0x4(%esp)
0x08048427 <main+131>:	movl   $0x8048519,(%esp)
0x0804842e <main+138>:	call   0x80482fc <printf@plt>
0x08048433 <main+143>:	mov    $0x0,%eax
0x08048438 <main+148>:	add    $0x34,%esp
0x0804843b <main+151>:	pop    %ecx
0x0804843c <main+152>:	pop    %ebp
0x0804843d <main+153>:	lea    -0x4(%ecx),%esp
0x08048440 <main+156>:	ret
```

Now notice how short the "-O3" version is: (with no jl jumping instructions):```
0x080483b0 <main+0>:	lea    0x4(%esp),%ecx
0x080483b4 <main+4>:	and    $0xfffffff0,%esp
0x080483b7 <main+7>:	pushl  -0x4(%ecx)
0x080483ba <main+10>:	push   %ebp
0x080483bb <main+11>:	mov    %esp,%ebp
0x080483bd <main+13>:	push   %ecx
0x080483be <main+14>:	sub    $0x14,%esp
0x080483c1 <main+17>:	movl   $0x80484c0,(%esp)
0x080483c8 <main+24>:	call   0x804830c <puts@plt>
0x080483cd <main+29>:	movl   $0x77359400,0x8(%esp)
0x080483d5 <main+37>:	movl   $0x1,0x4(%esp)
0x080483dd <main+45>:	movl   $0x80484c9,(%esp)
0x080483e4 <main+52>:	call   0x80482fc <printf@plt>
0x080483e9 <main+57>:	add    $0x14,%esp
0x080483ec <main+60>:	xor    %eax,%eax
0x080483ee <main+62>:	pop    %ecx
0x080483ef <main+63>:	pop    %ebp
0x080483f0 <main+64>:	lea    -0x4(%ecx),%esp
0x080483f3 <main+67>:	ret
```

---

### Post by cl333r on 2008-10-26
Thanks! how do you get these assembly dumps?

ps: looks like I was right in my suspicion that GCC somehow skips the loop(s)

---

### Post by nvteighen on 2008-10-26
> **cl333r said:**
> Thanks! how do you get these assembly dumps?

ps: looks like I was right in my suspicion that GCC somehow skips the loop(s)
There are two ways. The easiest is to tell gcc to stop before entering the Assembler step (asm -> object code).

```

gcc -S *source*.c

```

That will output a file called *source*.s, which is the assembly code for your source. The other way is to compile your code with debugging symbols and then disassembling through gdb.

---

### Post by jimi_hendrix on 2008-10-26
just for the heck of it i compiled your code with the M$ Visual Studio compiler when i booted into windows and it sill has not given me the output

---

### Post by Bichromat on 2008-10-26
> **cl333r said:**
> Thanks! how do you get these assembly dumps?

ps: looks like I was right in my suspicion that GCC somehow skips the loop(s)

Use the -S option when compiling with gcc.

---

