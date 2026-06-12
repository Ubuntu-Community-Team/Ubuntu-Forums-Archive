---
title: "Whats up here? 8 byte normal integers?"
date: 2009-04-02
forum: Programming Talk
---

### Post by SubNetMask on 2009-04-02
Did something change here?
that now if I do:

int i;

without a long or long long preset before it, it still counts it as an 8 Byte number?

If I objdump and look into the EIP register it reserves 0x8 Bytes,

0x80483d5:-----c7 45 f8 00 00 00 00-----mov----DWORD PTR [ebp-0x8],0x0

!?!?

how is it a 8 byte DWORD?


This in Ubuntu 8.10, C language btw.

---

### Post by lisati on 2009-04-02
I think it can depend on the compiler. Does outputting the value of sizeof() yield any clues?

---

### Post by SubNetMask on 2009-04-02
> **lisati said:**
> I think it can depend on the compiler. Does outputting the value of sizeof() yield any clues?

WTH ?!?!?!?

The 'int' data type is		 4 bytes
The 'unsigned int' data type is	 4 bytes
The 'short int' data type is	 2 bytes
The 'long int' data type is	 4 bytes
The 'long long int' data type is 8 bytes
The 'float' data type is	 4 bytes
The 'char' data type is		 1 bytes

I'm using gcc, and i used ggc to compile both this and the last program I objdump'ed. 


it reserves 8 bytes for a normal int, but sizeof() declares a normal int is 4.

---

### Post by lisati on 2009-04-02
> **lisati said:**
> I think it can depend on the compiler. Does outputting the value of sizeof() yield any clues?

Methinks I misunderstood but glimmer of understanding is seeping in....

If you compile and run the following you will get the answer 4 (a "normal") integer.
```
#include <stdio.h>
int main(void)
	{
	int i;
	i=sizeof(i);
	printf("Size is %i\n",i);
	return i;
	}

```
I'm very rusty on 32-bit assembler but suspect that it's the pointer (i.e. address) that's the DWORD.

---

### Post by lisati on 2009-04-02
> **SubNetMask said:**
> WTH ?!?!?!?

The 'int' data type is		 4 bytes
The 'unsigned int' data type is	 4 bytes
The 'short int' data type is	 2 bytes
The 'long int' data type is	 4 bytes
The 'long long int' data type is 8 bytes
The 'float' data type is	 4 bytes
The 'char' data type is		 1 bytes

I'm using gcc, and i used ggc to compile both this and the last program I objdump'ed. 


it reserves 8 bytes for a normal int, but sizeof() declares a normal int is 4.
I might have to call a "pass" so someone else more skilled can help....

---

### Post by SubNetMask on 2009-04-02
> **lisati said:**
> Methinks I misunderstood but glimmer of understanding is seeping in....

If you compile and run the following you will get the answer 4 (a "normal") integer.
```
#include <stdio.h>
int main(void)
	{
	int i;
	i=sizeof(i);
	printf("Size is %i\n",i);
	return i;
	}

```
I'm very rusty on 32-bit assembler but suspect that it's the pointer (i.e. address) that's the DWORD.

I know what a pointer is lol, but DWORD is the Data soo hmm...

But why would it reserve 8 bytes when I never told it to do so, with the last distribution of Linux I had, it gave me that ebp only took 4 bytes not 8.

and before you ask what dist. I have no idea, I got it from an assembly programming book, it was a Ubuntu variant.

---

### Post by lisati on 2009-04-02
> **SubNetMask said:**
> I know what a pointer is lol, but DWORD is the Data soo hmm...

But why would it reserve 8 bytes when I never told it to do so, with the last distribution of Linux I had, it gave me that ebp only took 4 bytes not 8.

and before you ask what dist. I have no idea, I got it from an assembly programming book, it was a Ubuntu variant.

It has kinda got me baffled too........ Anyone else out there able to shed some light on what's going on....

---

### Post by SubNetMask on 2009-04-02
> **lisati said:**
> It has kinda got me baffled too........ Anyone else out there able to shed some light on what's going on....

Lol, yes, if anyone knows why please help, it's messing up all of my memory segmentation code.

UPDATE:

well, it definitely has the characteristics of a 4 Byte number, as it will only go up to about 2,000,000,000 before 0'ing out.

So why would it reserve 4 more addresses than it needs?

---

### Post by beatbm on 2009-04-02
what is your cpu?
if it is an x64 i believe the answer is this

---

### Post by SubNetMask on 2009-04-02
> **beatbm said:**
> what is your cpu?
if it is an x64 i believe the answer is this

I have a Dual core X64 AMD 6000+, but I'm using 32 bit Ubuntu.

---

### Post by jomiolto on 2009-04-02
> **SubNetMask said:**
> Did something change here?
that now if I do:

int i;

without a long or long long preset before it, it still counts it as an 8 Byte number?

If I objdump and look into the EIP register it reserves 0x8 Bytes,

0x80483d5:-----c7 45 f8 00 00 00 00-----mov----DWORD PTR [ebp-0x8],0x0

!?!?

how is it a 8 byte DWORD?


This in Ubuntu 8.10, C language btw.

It's been quite a  long while since I've looked at gcc generated assembler, and I can't quite remember how it arranges its memory on function calls, but are you sure that it does not use 4 bytes for the old stack pointer?

---

### Post by beatbm on 2009-04-02
using 32bit ubuntu doesn't mean that the physical size of the register is 4 bytes.
it uses 8bytes registers but emulates 4bytes registers.thats why in the assembly seems to be 8byte but in C program shows as 4bytes.

---

### Post by jomiolto on 2009-04-02
> **beatbm said:**
> using 32bit ubuntu doesn't mean that the physical size of the register is 4 bytes.
it uses 8bytes registers but emulates 4bytes registers.thats why in the assembly seems to be 8byte but in C program shows as 4bytes.

x86-64 processors use regular 32-bit assembler with 32-bit registers in 32-bit mode.

---

### Post by beatbm on 2009-04-02
the hardware registers are 64bit. then you put a 32bit data in the register thats why the last 32bits are zeros.of course the assembler the registers and the mode is 32bit.
x86-64 is fully compatible with 32bit mode and programming model. 
 i have amd X2 5200+ and ubuntu 8.10 x64. when i run the previous small program says that the int is 4byte too

---

### Post by kpatz on 2009-04-02
My assembler is a bit rusty but IIRC a "DWORD" is 4 bytes, as a WORD is 2 bytes.  At least back in the old days... haven't done any 32-bit assembler. I think the 8 byte integers are called quadwords or maybe "QWORD".

---

### Post by Zugzwang on 2009-04-02
You do know that the "-8" is the address relative to the current stack pointer, right? What makes you think that there's no value on top of your int. For example, take the program given in this thread:
```

#include <stdio.h>
int main(void)
	{
	int i;
	i=sizeof(i);
	printf("Size is %i\n",i);
	return i;
	}

```
GCC will produce the following source for the main function here:
```

main:
.LFB2:
	leal	4(%esp), %ecx
.LCFI0:
	andl	$-16, %esp
	pushl	-4(%ecx)
.LCFI1:
	pushl	%ebp
.LCFI2:
	movl	%esp, %ebp
.LCFI3:
	pushl	%ecx
.LCFI4:
	subl	$36, %esp
.LCFI5:
	movl	$4, -8(%ebp)
	movl	-8(%ebp), %eax
	movl	%eax, 4(%esp)
	movl	$.LC0, (%esp)
	call	printf
	movl	-8(%ebp), %eax
	addl	$36, %esp
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret

```

As you can see, something like the old stack pointer is put onto it by the compiler. Then you integer lies obviously below it and therefore is at position -0x8 on the stack, so the "int" is 4 bytes.

BTW: "int" is 4 bytes long on both 32-bit GCC and 64-bit GCC.

---

### Post by beatbm on 2009-04-02
Zugzwang has right!! i missunderstood the problem :( . sorry for the mess

---

### Post by SubNetMask on 2009-04-02
> **Zugzwang said:**
> 

As you can see, something like the old stack pointer is put onto it by the compiler. Then you integer lies obviously below it and therefore is at position -0x8 on the stack, so the "int" is 4 bytes.

BTW: "int" is 4 bytes long on both 32-bit GCC and 64-bit GCC.

I see, the architecture must be different as the other linux dist. i had did not do this, and the variable calls and loop calls were structured very differently.

P.S.

I see why now!!
Load Effective Address (lea) loads it into esp, on my last dist, it did not do that, so it did not need to use the pointer to set the memory address back 4 bytes more.

---

### Post by Krupski on 2009-04-03
> **SubNetMask said:**
> I see, the architecture must be different as the other linux dist. i had did not do this, and the variable calls and loop calls were structured very differently.

P.S.

I see why now!!
Load Effective Address (lea) loads it into esp, on my last dist, it did not do that, so it did not need to use the pointer to set the memory address back 4 bytes more.

For what it's worth... I was just looking at the sizeof various data types when I came across this thread.

If I compile a program as 32 bit (using the -m32 option), I get this:

```

size of char     : 1
size of int      : 4
size of long int : 4
size of float    : 4
size of double   : 8
size of long dbl : 12

```

If compiled with no switch (i.e. 64 bit output on a 64 bit machine and 64 bit Linux) I get:

```

size of char     : 1
size of int      : 4
size of long int : 8
size of float    : 4
size of double   : 8
size of long dbl : 16

```

Strange... but there it is.

-- Roger

---

### Post by SubNetMask on 2009-04-03
> **Krupski said:**
> For what it's worth... I was just looking at the sizeof various data types when I came across this thread.

If I compile a program as 32 bit (using the -m32 option), I get this:

```

size of char     : 1
size of int      : 4
size of long int : 4
size of float    : 4
size of double   : 8
size of long dbl : 12

```

If compiled with no switch (i.e. 64 bit output on a 64 bit machine and 64 bit Linux) I get:

```

size of char     : 1
size of int      : 4
size of long int : 8
size of float    : 4
size of double   : 8
size of long dbl : 16

```

Strange... but there it is.

-- Roger

I did the same thing and sizeof() gave me the same results lol, it just confused me more...

---

