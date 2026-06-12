---
title: "[Nasm] Segmentation fault"
date: 2009-07-29
forum: Programming Talk
---

### Post by 2words4uready on 2009-07-29
Basically I'm just trying new things in assembly. I'm just manipulating strings/addresses and i got a segmentation fault that i can't seem to debug.
Here is my code:
```
jmp short var
doit:
pop ecx
xor eax,eax
mov [ecx+4],eax
lea ecx,[ecx+1]
mov eax,4
mov ebx,1
mov edx,8
int 0x80
mov eax,1
mov ebx,0
int 0x80
var:
call doit
db 'testXing'
```
Any help?

---

### Post by rCXer on 2009-07-29
I'm not sure but here goes...
Make sure this is the right type of call.  Near calls only push (e)ip on to the stack but far calls push (e)ip and then cs.  Therefore the value popped into ecx might not be address you want.

btw a better place to ask this would be at the [nasm forums]("http://sourceforge.net/forum/?group_id=6208"). They would probably have a better answer than mine :P

An easier way to do this is...
```

section .data
	String: db "testXing",0xA
	StringLen: equ $-String

section .text
	global _start

_start:
	;Print String
	mov eax,4	
	mov ebx,1
	mov ecx,String		;Same as lea ecx,[String]
	mov edx,StringLen
	int 0x80

	;End program
	mov eax,1
	mov ebx,0
	int 0x80

```

---

### Post by Zugzwang on 2009-07-30
@OP: You are first of all assuming that the code segment is equal to the data segment (i.e. what can be found in the code segment at address X can also be found at address X in the data segment). I don't think that this is necessarily the case. In all circumstances, this is however bad style and will also fool any execution prevention monitor running in the background. 

So follow rCXer's style of writing for less problems.

---

