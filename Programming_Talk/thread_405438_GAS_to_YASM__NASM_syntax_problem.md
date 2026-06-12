---
title: "GAS to YASM / NASM syntax problem"
date: 2007-04-09
forum: Programming Talk
---

### Post by nfm on 2007-04-09
Hello everybody,

This is my second day working with assembly. My C is pretty good and I have a feeling that assembly will be pretty simple. I started out with with hello world and I'm pretty familiar with general purpose registers, I then went to try 'Programming from the Ground Up' and got stuck on page 31 that deals with 'Finding a Maximum Value' This my first time trying such a thing and I'm trying my best to translate gas to nasm syntax. This is what I have:
```
section .data

[B]data_items:
long 3,67,34,222,45,75,54,34,44,33,22,11,66,0[/B]

section .text
	global _start

_start
	mov edi, 0
	**mov data_items(,edi,4),**
	mov ebx, eax

start_loop:
	cmp eax, 0
	je loop_exit
	inc edi
	**mov data_items(,edi,4),**
	cmp eax, ebx
	**jlw start_loop**

	mov ebx, eax
	jmp start_loop

loop_exit:
	mov eax, 1
	int 0x80
```

**Edit:** Post 2 and 3 has the solutions, information on registers and instructions can be found in your cpu's manual.

---

### Post by Wybiral on 2007-04-10
> **nfm said:**
> Intel's and AMD's manuals look scary to me.

They are scary, but once you learn to read them they become more valuable then any other documents on assembly.

This solution works, I'm not sure if it's exactly what you're looking for, but maybe it will help:
```

section .data
   data_items: dd 3,67,34,222,45,75,54,34,44,33,22,11,66,0

section .text
	global _start

_start
	mov edi, 0
	mov eax, [data_items + edi * 4]
	mov ebx, eax

start_loop:
	cmp eax, 0
	je loop_exit
	inc edi
	mov eax, [data_items + edi * 4]
	cmp eax, ebx
	jle start_loop
	mov ebx, eax
	jmp start_loop

loop_exit:
	mov eax, 1
	int 0x80

```

You have to get used to the NASM (Intel syntax) indexing method:

In GAS, you have: memory(base, index, step)
In NASM, you have: [memory + base + index * step]

In this case, you aren't using a base, so it's: [memory + index * step]

And step is 4 since we're working with longs (btw, in NASM "dd" is your long) "data_items" is your memory address and "ESI" is your index. All together it's:

[data_items + esi * 4]

Getting used to switching between at&t and Intel syntax assembly is tough (especially since they're completely backwards from each other) but it's worth it.

Personally I prefer Intel syntax (like NASM) because it's so much cleaner and easier to read, but, you have to know GAS if you plan to work with compiler output (but you don't have to know GAS to simply write C libraries).

I've never used YASM, it's NASM's 64 bit brother right? I don't know if any of the syntax differs between them.

Anyway, good luck!

(wish I could help you with the 64 bit stuff, but I don't have a 64 bit machine to test it on)

---

### Post by nfm on 2007-04-10
This is exactly what I'm looking for, it's definitely a help to me. YASM is a total rewrite of NASM with support for 64-bit amd64 architecture and according to YASM's manual it can compile assembly with GAS syntax, but as you just have mentioned, NASM syntax is cleaner and easier to read. Also, YASM is 100% compatible with NASM syntax.

For anyone interested:
32-bit:
```
;PURPOSE: This program finds the maximum number of a
;         set of data items.
;
;VARIABLES: The registers have the following uses:
;
; %edi - Holds the index of the data item being examined
; %ebx - Largest data item found
; %eax - Current data item
;
; The following memory locations are used:
;
; data_items - contains the item data. A 0 is used
;                   to terminate the data
;

section .data
   data_items: dd 3,67,34,222,45,75,54,34,44,33,22,11,66,0

section .text
	global _start

_start
	mov edi, 0
	mov eax, [data_items + edi * 4]
	mov ebx, eax

start_loop:
	cmp eax, 0
	je loop_exit
	inc edi
	mov eax, [data_items + edi * 4]
	cmp eax, ebx
	jle start_loop
	mov ebx, eax
	jmp start_loop

loop_exit:
	mov eax, 1
	int 0x80
```
compile with:
nasm -f elf maxnum.asm
ld -s -o maxnum maxnum.o
./maxnum
echo $?

you should get 222.

64-bit, but I'm not **100%** sure if it is entirely correct.
```
;PURPOSE: This program finds the maximum number of a
;         set of data items.
;
;VARIABLES: The registers have the following uses:
;
; %rdi - Holds the index of the data item being examined
; %rbx - Largest data item found
; %rax - Current data item
;
; The following memory locations are used:
;
; data_items - contains the item data. A 0 is used
;                   to terminate the data
;

BITS 64

section .data
   data_items: dq 3,67,34,222,45,75,54,34,44,33,22,11,66,0

section .text
	global _start

_start
	mov rdi, 0
	mov rax, [data_items + rdi * 8]
	mov rbx, rax

start_loop:
	cmp rax, 0
	je loop_exit
	inc rdi
	mov rax, [data_items + rdi * 8]
	cmp rax, rbx
	jle start_loop
	mov rbx, rax
	jmp start_loop

loop_exit:
	mov rax, 1
	int 0x80
```
compile with:
yasm -f elf64 -m amd64 maxnum-amd64.asm
ld -s -o maxnum-amd64 maxnum-amd64.o
./maxnum-amd64
echo $?

you should get 222.

Thanks Wybiral!

---

### Post by Wybiral on 2007-04-10
Cool, so for AMD64 assembly you just prefix "r" instead of "e" to all of the registers to use the 8 byte ones?

I assume you can still use "e" for the 4 byte parts too, right? If that's the case, then NASM 32 bit assembly should be pretty portable.

---

### Post by nfm on 2007-04-10
Yes, "r' prefix is used on all general purpose registers. In 64-bit you can also utilise extra 8 GPR (R8-R15). This is what Intel says on 'General-Purpose Registers in 64-Bit Mode':
> In 64-bit mode, there are 16 general purpose registers and the default operand size
is 32 bits. However, general-purpose registers are able to work with either 32-bit or
64-bit operands. If a 32-bit operand size is specified: EAX, EBX, ECX, EDX, EDI, ESI,
EBP, ESP, R8D - R15D are available. If a 64-bit operand size is specified: RAX, RBX,
RCX, RDX, RDI, RSI, RBP, RSP, R8-R15 are available. R8D-R15D/R8-R15 represent
eight new general-purpose registers. All of these registers can be accessed at the
byte, word, dword, and qword level. REX prefixes are used to generate 64-bit
operand sizes or to reference registers R8-R15. Intel® 64 and IA-32 Architectures Software Developer’s Manual Vol. 1 Section 3-16

---

### Post by IronAvatar on 2007-04-13
Just a few (probably unecessary) optimisation notes when coding in assembler;

[LIST]
[*]When setting a register to zero you can simply do something like *xor reg, reg* or sub *reg, reg*. This saves on the extra possible load for the operand, reducing code size and helping to aid i-cache coherency.
[*] I'm a bit rusty on this, but I think moving a value of zero into a register will set the zero flag.  So instead of *mov reg, reg[offsett]; cmp reg, 0; je label* you can just do  *mov reg, reg[offsett]; jz label* 
[*] Related to the last item; when looping and using a loop counter, it's preferable to count down so the end of your loop can do something like *dec counter_reg; jnz loop_start* avoding the need for a compare.
[/LIST]

---

### Post by phossal on 2007-04-13
Wybiral, I got a jailed post for teasing you (and an infraction). lol The mods can't tell the difference between friendly teasing, and harassment. Everything I do is unsupported by the mods! ;) Anyway, I can't find my CPU manual. (I teased you in my previous post for mentioning the manual, as if everyone has it laying around. The one for the AMD is something like 1200 pages.) I found what I thought was a good tutorial for NASM (coming from MASM), but it was full of bad links. Any suggestions for a good place to pick up the syntax. The manual at MIT's website doesn't seem helpful enough, although I haven't been able to really read through it yet.

From now on, I might write all my posts in binary so you can XOR them to decode the secret messages.

---

### Post by Wybiral on 2007-04-13
> **phossal said:**
> Wybiral, I got a jailed post for teasing you (and an infraction). lol The mods can't tell the difference between friendly teasing, and harassment. Everything I do is unsupported by the mods! ;) ...

lol... Yeah, I got an infraction for a sarcastic post of mine not too long ago either. I don't think they can tell the difference between friendly joking and serious being-an-***-ness.

Anyway, I couldn't tell if you were mentioning a NASM or MASM manual.... NASM's documentation can be found: [http://sourceforge.net/docman/display_doc.php?docid=47247&group_id=6208](http://sourceforge.net/docman/display_doc.php?docid=47247&group_id=6208)

EDIT:

Wait... That one seems to have some link problems too... lol, it was probably the one you had!

---

### Post by phossal on 2007-04-13
I'm new to NASM. I've used GAS, if you remember, and MASM (on MS), but I'd like to move to NASM. But I can't find documentation quite like I expected to learn the syntax.

---

