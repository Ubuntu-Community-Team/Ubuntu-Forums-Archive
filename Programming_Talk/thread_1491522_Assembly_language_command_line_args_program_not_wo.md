---
title: "Assembly language command line args program not working"
date: 2010-05-23
forum: Programming Talk
---

### Post by Quarg on 2010-05-23
Hello, I'm new to assembly language, and I'm trying to make a program (in NASM, on a 64-bit machine) that prints out arguments to the command line. I can't figure out why the following does not work:
```

section .data
	empty db "The pointer was null",10,0

section .text
 global _start
 _start:
	mov rcx, [rsp + 16]
	mov rbx, 1
	mov rdx, 40
	mov rax, 4
	int 80h
end:
	mov rax, 1

	int 80h
error_message:               ;just an error message in case there were
                             ;no arguments
	mov rcx, empty
	mov rbx, 1
	mov rdx, 22
	mov rax, 4
	int 80h
	jmp end	

```
The above code will run and exit, no segfault, no nothing. But it doesn't print out the first argument. 

when I declare some sort of buffer(say, text: resb 40) and use rep movsb to put the string that rcx points to (after loading rcx with [rsp + 16]  into the buffer like this:
```

 mov rsi, rcx
 mov rdi, text ;buffer named 'text'
 mov rcx, 40   ;just a random number, that's larger than the string
 rep movsb
 mov text, rcx

```
It works without a hitch - the first argument prints out onto the command line. Does anyone know why this won't work without using rep movsb?
Thanks in advance

---

