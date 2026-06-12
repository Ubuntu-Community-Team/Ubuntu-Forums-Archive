---
title: "I need some help with NASM..."
date: 2008-01-23
forum: Programming Talk
---

### Post by Yes on 2008-01-23
I'm trying to learn NASM and I need some help with a program I'm writing.  All it'll do is write "Hello world" five times and then "goodbye" five times.  When I run it, all it does is start a newline and then the cursor just blinks.  Here's the code...

```
section .data
	hello_msg:   db "Hello World!", 10
	goodbye_msg: db "Goodbye World!", 10

section .text
	global _start

	
_start:
   mov esi, 11 ;counter
   dec esi ;decrement counter
   
   cmp esi, 5 ;if the counter is greater than 5
   jg writeHello ;jump to write hello
   
   cmp esi, 5 ;if counter is less than or equal to five
   push esi ;put coutner on stack
   jle writeGoodbye ;jump to writeGoodbye

writeMsg: ;writes the message
	pop edi 
	mov eax, 4 
	mov ebx, 1
	pop ecx
	pop edx
	int 0x80
	push edi
ret

writeHello: ;calls writeMsg and puts the appropiate message and size on the stack
	pop edi
	
	push hello_msg
	push 12
	call writeMsg
	
	push edi
ret

writeGoodbye: ;calls writeMsg and puts the appropiate message and size on the stack
	pop edi
	pop esi
	
	push goodbye_msg
	push 15
	call writeMsg
	
	cmp esi, 0
	je endPrgm
	
	push edi
ret

endPrgm: ;ends the program
	mov eax, 1
	int 0x80
```

 Can anyone help?

Thanks!

e:  I know it won't loop, but I'd just like to know why it doesn't print anything.

---

