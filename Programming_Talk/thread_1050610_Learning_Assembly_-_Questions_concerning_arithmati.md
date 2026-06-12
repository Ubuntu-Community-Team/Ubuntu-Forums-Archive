---
title: "Learning Assembly - Questions concerning arithmatic and I/O"
date: 2009-01-25
forum: Programming Talk
---

### Post by spudgunner on 2009-01-25
I'm currently taking a assembly programming course and I'm having a little trouble with my first assignment. I've been looking for information on Google and using the ebooks "The Art of Assembly" and "Introduction to 80x86 Assembly Language and Computer Architecture".

My first question deals with multiplication. When you multiply two number together, the answer is at most double the number of bits of the numbers you multiplied. So for 8 bits, answer is 16; 16 bits, answer is 32; 32 bits, answer is 64. If I have an answer that requires more than 32 bits (ie. must span 2 32-bit registers (64-bit) or more), how would I go about multiplying it?

My second question concerns I/O. Almost all of the examples I've seen include header files for I/O, which I don't think I'm allowed to do. However, I've found the commands:

in register,port 
out register,port

My question for this is, can I directly read input / display output from the terminal, and what port would I have to use?

Thanks for any help... I'll probably need more about different things as the semester progresses.

---

### Post by snova on 2009-01-25
> **spudgunner said:**
> My first question deals with multiplication. When you multiply two number together, the answer is at most double the number of bits of the numbers you multiplied. So for 8 bits, answer is 16; 16 bits, answer is 32; 32 bits, answer is 64. If I have an answer that requires more than 32 bits (ie. must span 2 32-bit registers (64-bit) or more), how would I go about multiplying it?

I think you check for overflow, and then operate on the second register in the case that you need to. How, I don't know.

> My second question concerns I/O. Almost all of the examples I've seen include header files for I/O, which I don't think I'm allowed to do.

No, you aren't.

> However, I've found the commands:

in register,port 
out register,port

Why would they put that in? Any sane kernel would kill your program for attempting that.

> My question for this is, can I directly read input / display output from the terminal, and what port would I have to use?

A "port" has nothing to do with I/O, at least not this kind. Ports are a hardware-level abstraction provided by the motherboard/CPU/something (not sure) for the operating system to communicate with hardware. Unless you're writing device drivers in this course of yours, you'll never use them.

But, to perform input/output, you'd probably just call into the C library- plain old printf() would do.

---

### Post by spudgunner on 2009-01-25
I think I should re-phrase my question: how do you print a character/string to the terminal using assembly? And how to do you read character/string from the terminal only using assembly? I've read about using an interrupt that's provided by the OS, but the places I saw it only talked about Windows machines... is there a similar method for Linux?

---

### Post by NathanB on 2009-01-25
> **spudgunner said:**
> I'm currently taking a assembly programming course and I'm having a little trouble with my first assignment. I've been looking for information on Google and using the ebooks "The Art of Assembly" and "Introduction to 80x86 Assembly Language and Computer Architecture".

My first question deals with multiplication. When you multiply two number together, the answer is at most double the number of bits of the numbers you multiplied. So for 8 bits, answer is 16; 16 bits, answer is 32; 32 bits, answer is 64. If I have an answer that requires more than 32 bits (ie. must span 2 32-bit registers (64-bit) or more), how would I go about multiplying it?

The standard CPU multiplication instructions make use of two 32-bit registers to hold the 64-bit number.  For instance,  'mul ebx' would multiply the value in EBX with the value of EAX and return the result in the EDX:EAX pair (EAX holding the low-order dword and EDX holding the high-order).

Alternatively, you could just use the FPU to perform the operation.  Or... learn the new SSE instructions.

> My second question concerns I/O. Almost all of the examples I've seen include header files for I/O, which I don't think I'm allowed to do. However, I've found the commands:

in register,port 
out register,port


Can't do that from a *user-mode* program in Linux.

> My question for this is, can I directly read input / display output from the terminal, and what port would I have to use?

Use 'system calls' to read/write to/from the system's STDIN/STDOUT file handles.

All of this is explained (with examples) at [http://linuxassembly.org](http://linuxassembly.org) and, I am sure, in your class's textbook and classroom hand-outs.

---

### Post by NathanB on 2009-01-25
> **spudgunner said:**
> I think I should re-phrase my question: how do you print a character/string to the terminal using assembly? And how to do you read character/string from the terminal only using assembly? I've read about using an interrupt that's provided by the OS, but the places I saw it only talked about Windows machines... is there a similar method for Linux?

Yes, Linux 'syscalls' are very similar to how it was done in Windows (well, DOS, actually).  "INT 80h" is the only interrupt used.  The particular API function is selected by the constant you store into EAX.  A short example:

[PHP]
section .data
	hello:     db 'Hello world!',10    ; 'Hello world!' plus a linefeed character
	helloLen:  equ $-hello             ; Length of the 'Hello world!' string
	                                   ; (I'll explain soon)

section .text
	global _start

_start:
	mov eax,4            ; The system call for write (sys_write)
	mov ebx,1            ; File descriptor 1 - standard output
	mov ecx,hello        ; Put the offset of hello in ecx
	mov edx,helloLen     ; helloLen is a constant, so we don't need to say
	                     ;  mov edx,[helloLen] to get it's actual value
	int 80h              ; Call the kernel

	mov eax,1            ; The system call for exit (sys_exit)
	mov ebx,0            ; Exit with return code of 0 (no error)
	int 80h
[/PHP]

However, you may find it easier to avoid syscalls and just use the C library as **snova** has suggested.  Here is an example of that:

[PHP]
; For Linux:  
; nasm -f elf32 -o prime.o prime.asm  
; gcc -o prime prime.o  
 
section .data  
msg: db 'Enter an integer: ', 0  
chr: db '%d', 0  
ispmsg: db 10, 'The integer %d is prime!', 10, 0  
nopmsg: db 10, 'The integer %d is not prime.', 10, 0  
 
section .text  
global main  
extern printf, scanf  
 
main:  
 
push ebp  
mov ebp, esp  
sub esp, $0c  
 
mov dword [ebp-8], 1  
push msg  
call printf  
add esp, 4  
 
lea eax, [ebp-4]  
push eax  
push chr  
call scanf  
add esp, 8  
 
cmp dword [ebp-4], 2  
jge next  
mov dword [ebp-8], 0  
jmp continue  
 
next:  
jne nextt  
jmp continue  
 
nextt:  
mov eax, [ebp-4]  
cdq  
mov ebx, 2  
idiv ebx  
cmp edx, 0  
je nexttt  
 
finit  
fild dword [ebp-4]  
fsqrt  
fistp dword [ebp-$0c]  
 
mov ecx, 3  
jmp ccheck  
floop:  
mov eax, [ebp-4]  
cdq  
idiv ecx  
cmp edx, 0  
jne check  
mov dword [ebp-8], 0  
jmp continue  
check:  
add ecx, 2  
ccheck:  
cmp ecx, [ebp-$0c]  
jle floop  
jmp continue  
 
nexttt:  
mov dword [ebp-8], 0  
 
continue:  
xor eax, eax  
cmp eax, [ebp-8]  
jne isprime  
mov eax, [ebp-4]  
push eax  
push nopmsg  
call printf  
add esp, 8  
jmp endit  
 
isprime:  
mov eax, [ebp-4]  
push eax  
push ispmsg  
call printf  
add esp, 8  
 
endit:  
add esp, $0c  
pop ebp  
xor eax, eax  
ret 
[/PHP]

---

### Post by spudgunner on 2009-01-26
Thanks for your help, that's exactly what I was looking for. My only question about this concerns the first code bit... what does the 80h interrupt do at the very end of that peice of code?

---

### Post by snova on 2009-01-26
> **spudgunner said:**
> Thanks for your help, that's exactly what I was looking for. My only question about this concerns the first code bit... what does the 80h interrupt do at the very end of that peice of code?

**int 0x80** makes a syscall. In this instance, it's the exit() syscall.

---

### Post by spudgunner on 2009-01-26
Thanks, I understand now. How would I read input from the terminal?

---

### Post by NathanB on 2009-01-26
Well, first step is to provide some buffer space to store the incoming string.  There are a few different ways to do this.  One way is to add a '.bss' section to the executable:

[php]section .bss
buffer: resb 128[/php]

*{assuming we intend to read 128 characters from stdin}*

Another way is to mimic the way that High Level Languages (obviously talking about C and C++ here) allocate variables on the stack.  This is called a stack frame.  The following stack frame setup would suffice for our current needs:

[php]push ebp  ;save the current value of ebp
mov ebp, esp  ;save current stack pointer
sub esp, 128  ;allocate our buffer space

;; We subtract because the stack
;; grows "downward" in memory as we
;; add data to it.[/php]

The constant representing the 'read' function is 3.  (This is not stable across Kernel versions, so check "unistd.h" in the "/usr/include/asm" directory for the correct number if it isn't three.)  The constant, 0, represents STDIN.  So our "read from console" code will look something like:

[php]mov ecx, esp  ;pointer to our buffer
mov edx, 128  ;number of characters to read
mov ebx, 0  ;STDIN handle
mov eax, 3  ;sys_read
int 80h  ;call operating system services[/php]

And, of course, we would finish our program by restoring the stack frame:

[php]mov esp, ebp
pop ebp
[/php]

Hope to have helped!

---

### Post by spudgunner on 2009-02-19
I have another assignment, and I've having trouble figuring out how arrays are passed from C to assembly. I know that if you pass single variables into an assembly program, they get stored in the stack. If you directly pass an array (ie. not passing a pointer), would each array entry get stored in the stack or would only the first one get stored (or an address to the first one, or something like that)?

Thanks for your help.

---

### Post by snova on 2009-02-19
As far as I know, arrays are passed as pointers to the array...

---

### Post by spudgunner on 2009-02-19
Thanks for that. I'll probably come back for help debugging...

---

### Post by spudgunner on 2009-02-19
I'm having problems getting it to work... my program compiles fine, but gives a segmentation fault when I try to run it. I'm pretty sure it's memory management issues, but I can't figure it out. Here's all the code I'm using.

Any suggestions for me.

Assembly (what I have to make myself. Note that it's not the complete code, because until I get this memory thing working, nothing else really matters):

[PHP];array address is passed into stack

;eax stores current number (imul stretches edx:eax)
;ebx holds current character to be parsed
;ecx automatically decrements in loop instruction
;edx is a short-term buffer

;how it works:
;stack is filled with character array
;if it's a negative number, sign is set -1, then rest of array is parsed
;by looping 19 more times
;if it's a positive number, sign is set 1, the first number of the array
;read into eax, and rest of array is parsed by looping 19 times

;return is automatically read from eax

segment .data:

segment .bss:
sign	resd	1			;holds sign of number

segment .text:
	global string2int

string2int:

	push ebp			;save C program's stack
	mov ebp,esp			;start new stack

	mov eax,0			;start number off at zero

	;determine sign of the number
	add ebp,8			;increment 2 spaces on stack
	mov ebx,[ebp]			;load address of first entry of string from stack
	mov ebx,[ebx]			;load content from memory address in ebx
	cmp ebx,45			;checks the ascii code
	je set_positive			;jump if first character is not '-'
		mov edx,-1		;number is negative
		mov [sign],edx
		mov ecx,19		;loop 19 times
		jmp parse

	set_positive:
		mov edx,1		;number is positive
		mov [sign],edx
		mov eax,ebx		;set first digit in eax
		mov ecx,19		;loop 19 times
		jmp parse

	;parses the string
	parse:
		add ebp,1		;increment 1 memory address
		mov ebx,[ebp]		;move address next character to be parsed
		mov ebx,[ebx]		;load content from memory address in ebx
		cmp ebx,0		;check for null character
		je finish		;jump if the end of string is present
		add ebx,-48		;use ascii code to obtain number
		mov edx,10
		mul edx			;muliply number by 10
		add eax,ebx		;add next digit	
	loop parse

	finish:
		imul eax,[sign]			;sign the number

	mov esp,ebp			;return to stack
	pop ebp				;get original stack pointer
	ret				;return to C function
[/PHP]

C Code (this is not to be modified):
[PHP]// file main.c
#include <stdlib.h>
#include <stdio.h>
//#include "string2int.asm"

/*
int string2int(const char *s)
{
	return atoi(s);
}
*/
char string[20];
int main()
{
	int d;
	printf("Enter a number: ");
	scanf("%s", string);
	d = string2int(string);
	printf("The number is %d\n", d);
 	return 0;
}[/PHP]

Makefile (because it's handy... and slightly screwy, but I can figure that out later)
[PHP]# Assignment 2 Makefile

.SUFFIXES: .asm .c .o

AS=nasm
ASFLAGS= -f elf

.asm.o:
	$(AS) $(ASFLAGS) $*.asm

a2: main.o string2int.o
	cc -o a2 *.o

clean:
	rm *.o[/PHP]

---

### Post by spudgunner on 2009-02-23
Ok, I've talked to some people at school, I got in compiling without segmentation faults during operation (and it was due to the stack set-up, like I guessed), however, it worked completely wrong so I basically started from scratch. What I've done so far is pushed ebx,ecx,edx to preserve them, read the address of the stack, got a number, saved it. Now I'm trying to add a second number to it correctly by multiplying the first number and adding the second (for parsing a base 10 number). The mul instruction is supposed multiple either a register, immediate, or memory location by eax and save it there. So I've got my current number in eax, try to execute "mul 10" and it says the operands are invalid. I've tried moving 10 to a register and doing from there, same thing. Any ideas?

Edit: I got it to work by using an alternative to the mul instruction (which is apparently faster), but I'd still like to know why the mul wouldn't work here. Thanks. (use main.c and makefile from above)

```
segment .data

segment .bss
sign	resd	1			;holds sign of number
next	resd	1			;holds the next character/number

segment .text
	global string2int

string2int:

	enter 0,0

	push ebx
	push ecx
	push edx

	mov eax,0			;start number off at zero

	mov ebx,[ebp+8]			;get address of first array entry
	mov edx,[ebx]			;get first array entry
	add edx,-48			;convert character to number
	mov [next],edx			;store number
	mov eax,[next]			;put the number in eax
	mul 10				;multiple eax by 10

	pop edx
	pop ecx
	pop ebx

	leave
	ret
```

---

### Post by Frank Kotler on 2009-02-23
Hi Spudgunner,

The reason "mul 10" doesn't work is that "mul" doesn't take an "immediate" operand - only register or memory. "imul" takes an immediate operand... "imul" is actually two different instructions. The "one operand" form is similar to "mul" - it does a 32-bit by 32-bit = 64-bit result multiply -only it preserves the sign. The three operand form does a 32-bit by 32-bit multiply, but stores only a 32-bit result. The two operand form is only a special case of the three operand form, in which the first two operands are the same. (the one operand form won't take an immediate, either) That's potentially confusing, so if you've got a "better way", forget mul/imul. I assume the "better way" involves "lea"? There's a "cute" way to do it using "lea" - I'd show it to you, but I don't want to "do your homework". (glad to help you learn asm, not interested in helping you avoid learning it :)

Pity we can't alter the C code - there's a potential buffer overflow in it. Might as well have used "gets()"! Heck of a thing to be teachin' newbies! You can tell your instructor I said so! Mmmm... better not... But don't *you* write code with buffer overflows in it... Please!!!

Back to your code... I see a potential problem:

mov edx,[ebx] ;get first array entry

This in fact gets the first *four* characters in your string into edx. Adding -48 to it isn't going to make it the "digit" you want to add into the "result so far". At the risk of adding an instruction you're probably "not supposed to know" yet, you could use:

movzx edx, byte [ebx]

That will get just the one character we want, and fill the upper bytes of edx with zeros.

An alternative would be to use just dl:

mov dl, [ebx]

... but when we get to the "add", we're going to want to use all of edx. "add eax, dl" isn't going to work (no such instruction). The workaround to that could be to "pre-clear" the upper bits of edx:

mov edx, 0
mov dl, [ebx]

Before doing the "add edx, -48" you might want to verify that dl is actually a valid decimal character - those pesky users will type anything that comes into their head, y'know!

now...

add edx,-48 ;convert character to number
mov [next],edx ;store number
mov eax,[next] ;put the number in eax

Using "[next]" isn't really doing anything for ya. You could have done "mov eax, edx" with the same result. But the single number we've got (a character converted to a digit), is *not* the number we want to multiply by ten! We want to multiply the "result so far" by ten, and then add in our "new digit".

mul 10 ;multiple eax by 10

As we discussed, this isn't an instruction. "mul dword [ten]" would do it, if you had "ten dd 10" someplace. Or use a register... But that's still going to trash edx before we're done using it! Easiest thing might be to use some register other than edx to hold the character/digit we're working on. Maybe ecx/cl... In your original code, you were using ecx as a loop counter... I don't know where the number 19 came from. Your more recent code didn't do it - you shouldn't need it. Might want *some* kind of maximum on your loop - just in case the string *isn't* zero-terminated - but if you quit on "any invalid character", that ought to cover it.

Anyway... don't forget to increment ebx before you go back for another character... you're on the right track! (you might want to get an "all positive" version working first, before you tangle with signed numbers)

Just to clear up an earlier misconception in this thread, we *can* do in/out to the ports. We need to get "permission" first. To get permission, we have to be "root". There may be other reasons we wouldn't get permission, but I haven't encountered 'em. It is generally "not the way to do it" in Linux, but we *can*. I have an example that beeps the speaker, and another that blinks the keyboard LEDs to prove it. But it's not what you want.

Carry on... And let us know how it comes out.

Best,
Frank

---

### Post by spudgunner on 2009-02-23
Frank Kotler, you are the man! You just saved me hours of fiddling with code!

Everything was working fine until I tried to parse more than one character... and the movzx completely fixed it. Thanks!

For the multiplication, I kept search for info after I posted, and actually found a way that is supposed to be shorter for multiplying constants (it works by decomposing the constant numbers of the form 2^n, then shifting the number your trying to multiply, saving it when your 2^n factors come up, and adding it all together at the end).

I will be using ecx to control my loop. I'm using eax to hold the current "up until now" number, ebx holds the address and edx is a buffer register for whatever.

The negative sign shouldn't be a huge problem. But... I need supper. I will post up if I have more problems.

Thanks so much!

Josh

---

### Post by spudgunner on 2009-03-04
I have another assignment... a part of it involves comiling a C program to GAS assembly and commenting the assembly... there's one type of instruction that keeps coming up that I can't seem to find anything about:
It is:

movl	%eax, v(,%edx,4)

In this case, I know that eax is getting moved into the contents of something... but v(,%edx,4) is confusing me... what does it mean?

Thanks for any help,
Josh

---

### Post by Frank Kotler on 2009-03-04
I think this is it...

[http://sources.redhat.com/binutils/docs-2.12/as.info/i386-Memory.html#i386-Memory](http://sources.redhat.com/binutils/docs-2.12/as.info/i386-Memory.html#i386-Memory)

Looks like, in Nasm syntax:

mov [v + edx * 4], eax

Does that make sense, in context? Is "v" some sort of an array of dwords (long)? And (%)edx a potential index into 'em?

You may get "more familiar" results by adding "-masm=intel" to gcc's command line along with "-S"...

Best,
Frank

---

### Post by spudgunner on 2009-03-05
I don't have the code with me right now (I'm not at home), but I'm sure it'll help. Thanks for that.

---

### Post by spudgunner on 2009-03-10
I have another question about my current assignment. The code p2align 4,,7 and p2align 3 has popped up and I have no idea what it does. I looked here: [http://ftp.gnu.org/old-gnu/Manuals/gas-2.9.1/html_node/as_111.html]("http://ftp.gnu.org/old-gnu/Manuals/gas-2.9.1/html_node/as_111.html"), as well as other places, but I do not understand the explainations. Can anyone help me out?

Thanks,
Josh

---

### Post by Frank Kotler on 2009-03-10
Maybe the first thing you'll want to know is that it doesn't do anything as far as the "logic" of your code goes. Might not run as fast without it, but it'll "do" the same thing.

What it does is to insert some padding, to put the next byte on an "even numbered" address. The meaning of "even numbered" is determined by the first parameter - it's a power of two, not a number of bytes. Put another way, it's the number of zeros we want at the end of the address. The number of bytes of padding needed to get this alignment is fixed, once the code is fixed, of course - p2align adjusts the number of bytes of padding to keep us "nicely aligned" as we modify the code - that's the "point" of the thing.

The second parameter is the byte to use for padding - zero for data sections and nop for code sections, if none is specified. (nop - 0x90 - actually decodes to xchg eax, eax) Rare that you'd want anything different, usually. I think p2align actually uses some "multi-byte nops" - lea esi, [esi], lea esi, [esi + 0], etc. (the manual says "on some systems", nop is used in code sections - I'm pretty sure we're such a system)

The third parameter specifies the maximum number of bytes of padding to use. I'm not sure I see the point of this one. We want it aligned or we don't, right? But your example "p2align 4,,7" says: "align us to a 16 byte boundary (using any byte you like), unless it would take more than 7 bytes, then don't bother". I guess it's a tradeoff between size and speed???

I assume gcc is inserting these things into your code. If you need to figure out where you want 'em, you'll need to read some optimization manuals - the manufacturer's manuals, or Agner Fog's tutorial - [http://www.agner.org](http://www.agner.org) Function entrypoints and loop tops are commonly aligned... targets of jumps, and (I guess) sometimes the jump instruction itself(?). The rules are complex, and vary from one CPU to another.

If your assignment is to comment the code, you'll probably want to note what's being aligned - if you can figure it out. The good news is, the code'll work without it...

Best,
Frank

---

### Post by spudgunner on 2009-03-29
I have one last assignment for my assembly course. This time we must re-write a function to implement a shell sort but it must take the same inputs as the C library function qsort(). Since one question in the last assignment I had involved attempting to write a shell sort in assembly, I have the code done and only need to modify it to accept the inputs. Here's my problem: qsort() looks like this:

```
qsort(void *base , size_t nel , size_t width ,int (* compar )( const void *, const void *))
```

It will not be hard to modify the function for hte first three inputs, however, the last input is a function. My question is, what gets passed onto the stack in place of this function, and how do I call this function using assembly code when I need to?

Thanks for any help,

Josh

---

### Post by Frank Kotler on 2009-03-30
Just push the address (name) of the function on the stack, like any other parameter...

(Nasm syntax)
push my_compare_function
push width
push nel
push base
call qsort

For (G)as syntax, you'll want "$my_compare_function", I think. (etc.)

In your qsort function, presumably you've got "cmp ???, ???" in there somewhere. Replace it with:

push ???
push ??? ; pointers to your data
call [ebp + 20]
(check my arithmetic on that "20"!!!) (Gas: *20(%ebp) ???? Not sure of that!)

Your "my_compare_function" will want to get the two pointers off the stack, and do any kind of a comparison you like. Sort on the second character of the third word, if you like. The man page on qsort says "in ascending order", but we can reverse the sense of the compare to get "descending". In an "all asm" program, we could just return flags, but to be "qsort-compatible", we'd better return -1/0/1 in eax...

This business of having a function take a "callback" function (I think that's the correct name) as one of its parameters is a very powerful technique, so figure it out enough to be "comfortable" using it, if you can!

Best,
Frank

---

### Post by spudgunner on 2009-03-30
It would seem now that I wasn't quite clear on my question, but you answered it perfectly. I'm actually calling the assembly function from C code and the compare function I am to use is also in C code (written in the same program that calls the assembly sorting). Now that I understand how to call it, I can get on with this assignment.

Thanks,

Josh

---

### Post by spudgunner on 2009-03-30
I'm having some trouble calling the C function from the assembly. Here's the C code the prof gave us to work with:

[PHP]#include <stdio.h>
#include <stdlib.h>

int compare (const void *a , const void *b)
{
	return *(int*)a-*(int*)b ;
}
# define N 10

int main()
{
	int i;
	int array[N];
	int x;
	/* initilize array with random numbers */
 	for (i=0;i<N;i++) array[i]=rand();

	/* Sort array */
	if(shellsort(array,N,sizeof(int),compare)==1) printf("Error sorting\n");

	/* output the sorted array */
	for (i=0;i<N;i++) printf("%d\n",array[i]);
  	return 0;
}
[/PHP]

And here's my assembly code:

[PHP];registers eax,ebx,ecx,edx free for operations
;registers esi,edi free for operations as long as they
;first pushed and popping after (and no memory ops)

;when function called:
;ebp+8 = array base pointer
;ebp+12 = length of array
;ebp+16 = length of data in array
;ebp+20 = pointer to compare function

;Initalized data
segment .data

segment .bss
array	resd	1	;pointer to first array element
gap	resd	1	;gap size
size	resd	1	;how long the array is
i	resd	1	;i
width	resd	1	;how big the data is (bytes)
compare	resd	1	;pointer to compare function

segment .text
	global shellsort

shellsort:
	enter 0,0

	;push important registers
	push ebx
	push ecx
	push edx

	;store array address
	mov eax,[ebp+8]		;get array address off stack
	mov [array],eax		;store array address
	;note: must put [array] into a register and add
	;4x the offset to get to an entry

	;store size
	mov eax,[ebp+12]	;get size off stack
	mov [size],eax		;store size in memory
	mov [gap],eax		;store gap in memory

	;store data size
	mov eax,[ebp+16]	;get data size from stack
	mov [width],eax		;store data size

	;store compare function pointer
	mov eax,[ebp+20]	;get pointer from stack	
	mov [compare],eax	;store pointer

;for (gap = SIZE/2; gap > 0; gap /=2)
;set up loop to handle gap, eax is i
gaploop:
	mov eax,[gap]	;move the size to eax
	shr eax,1	;divide size by two (now storing gap)
	mov [gap],eax	;save new gap in memory
	cmp eax,0	;check for 0 condition
	jle near checkset
	add eax,-1	;decrement gap so i adds properly
	mov [i],eax	;move gap-1 to i

;for (i = gap; i < SIZE; i++)
;second embedded for loop
i_counter:
	mov eax,[i]	;mov i to eax
	inc eax		;increment i
 	mov [i],eax	;move i back to memory
 	cmp [size],eax	;check i for boundry condition
 	jle gaploop 	;jump to previous loop if condition met
 	mov edx,eax	;edx is now i (which will equal j+gap)
	mov ecx,[array]	;move array index to ecx

;for (j = i - gap; j >= 0 && v[j] > v[j + gap]; j -= gap)
;{
;	temp = v[j];
;	v[j] = v[j + gap];
;	v[j + gap] = temp;
;}
;third embedded loop (i = j + gap)
;edx, eax start out as i (i is stored)
;ecx store array pointer
j_counter:
	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov ebx,[ecx+4*edx]	;set v[i] into ebx
	mov ebx,esi		;set address of v[i] into ebx

	sub edx,[gap]		;subtract gap from edx
	cmp edx,0		;insure j is not lower than zero
	jl i_counter		;else move to upper loop

	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov eax,[ecx+4*edx]	;set v[j] into ebx
	mov eax,esi		;set addresss of v[j] into ebx

	push ebx		;push address of v[i] into ebx
	push eax		;push address of v[j] into ebx
	call [compare]		;call compare

	cmp eax,0		;compare v[j], v[j+gap]
	jl i_counter		;else move to upper loop

	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov [ecx+4*edx],ebx	;switch ebx
	mov [esi],ebx		;switch ebx

	add edx,[gap]		;add edx and gap to get higher index

	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov [ecx+4*edx],eax	;switch eax
	mov [esi],eax		;switch eax

	sub edx,[gap]		;set j proper
	jmp j_counter		;check next index
	

; for (i = 0; i < SIZE-1; i++)
; 	if (v[i] > v[i+1])
; 	{
; 		printf(" Error in the sorting\n");
; 		return 1;
; 	}
checkset:
	mov edx,[array]	;keep array base pointer
	xor ecx,ecx	;keep track of index offset and loop count

check:
	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov eax,[edx+4*ecx]	;move contents of array+ecx to ebx
	mov eax,esi		;move contents of array+ecx to eax

	inc ecx			;increment ecx

	;alogithm for calculating array entry address
	;and moving value at address into register
	xor esi,esi		;zero esi
	mov esi,[width]		;move width into esi
	imul esi,edx		;find shift value
	add esi,ecx		;find total memory address
	;mov ebx,[edx+4*ecx]	;move contents of array+ecx to edx
	mov ebx,esi		;move contents of array+ecx to edx

	cmp ecx,[size]		;ensures array bounds are good
	ja good			;jumps to good if at the end of the array
 	cmp eax,ebx		;compare entries
 	jg error		;error if lower is larger than higher
 	jmp check		;restarts if not at end of array

;clean for successful sort
good:	
 	xor eax,eax	;zero eax
 	jmp end		;go to terminating sequence

;handles errors
error:
 	xor eax,eax	;zero eax
 	add eax,1	;eax = 1

;closes down the function, returns control to C
end:
 	pop edx
 	pop ecx
 	pop ebx
 	
 	leave
 	ret	[/PHP]

Basically, what I'm doing in the assembly is putting the address of the compare function into memory and calculating memory addresses to use in the compare. I know my calculation works because the sorting will work with a normally assembly cmp function when I use the values stored at the memory that's pointed to by the address calculation. I've also narrowed down the segmentation fault to exactly when I use "call [compare]". Any suggestions?

Thanks,

Josh

---

