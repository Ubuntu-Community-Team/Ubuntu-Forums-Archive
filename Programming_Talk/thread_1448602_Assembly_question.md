---
title: "Assembly question"
date: 2010-04-06
forum: Programming Talk
---

### Post by nmccrina on 2010-04-06
Hi, this isn't really a problem, but I could use some clarification.

Basically, why won't this work:

```

SECTION .data

SECTION .bss
char: resb 1

SECTION .text
	global _start

_start:
	; mov byte [char],30h ; store 48 in variable char
	mov eax,04h ; system write call
	mov ebx,01h ; STDOUT file descriptor
	mov ecx,30h ; NEITHER THIS NOR '0' WILL GET WRITTEN
	mov edx,01h ; length of text is one byte
	int 80h ; make the system call
	
	mov byte [char],0Ah ; store 10 in variable char
	mov eax,04h ; system write call
	mov ebx,01h ; STDOUT file descriptor
	mov ecx,char ; write ASCII character '\n'
	mov edx,01h ; length of text is one byte
	int 80h ; make the system call
	
	mov eax,01h ; system exit call
	mov ebx,00h ; return value (0)
	int 80h ; system call

```

If I move a constant value (such as 30h, ASCII for '0') into a variable and then mov that variable into a register, the character will be output when I make the write system call. But if I just move the constant directly into the register as in the above code nothing will get printed (though no error will be shown either). I'm thinking it has something to do with storing memory addresses vs. storing actual data, but I can't work it out. Can someone explain what's happening?

---

### Post by NathanB on 2010-04-06
You need to put the string address into ECX.  Here is an example:
[PHP]; nasm -f elf32 -o display.o display.asm
; ld -o display display.o

global _start

segment .data
announce db 'Your character: '
ann_len equ $ - announce
newline db 10

segment .bss
buff resb 1

segment .text
_start:
	mov eax, 4 ; __NR_WRITE
	mov ebx, 1 ; STDOUT
	mov ecx, announce ; address of string
	mov edx, ann_len ; length of string
	int 80h

	mov al, 30h
	mov [buff], al ; store '30h' in buffer

	mov eax, 4 ; __NR_WRITE
	mov ebx, 1 ; STDOUT
	mov ecx, buff ; address of string
	mov edx, 1 ; length of string
	int 80h

	mov eax, 4 ; __NR_WRITE
	mov ebx, 1 ; STDOUT
	mov ecx, newline ; address of string
	mov edx, 1 ; length of string
	int 80h

	mov eax, 1 ; __NR_EXIT
	int 80h
[/PHP]

Hope that helps!

---

### Post by nmccrina on 2010-04-06
Ok, so write needs the **address** of a string, and I was giving it a value; when I did 

```
mov ecx,30h
```

that was the equivalent of

```

mov buff,30h
mov ecx,[buff] ; FAIL

```

That makes sense. Thanks for your help!

---

### Post by NathanB on 2010-04-06
Actually, 'mov buff, 30h' would be a memory-to-memory move, therefore it would be illegal.  And 'mov ecx,[buff]' would store unknown quantities into the upper bytes of ECX.

So, actually, your code
[PHP]mov ecx,30h[/PHP]
is equivalent to
[PHP]mov al, 30h
mov [buff], al
movzx ecx, [buff][/PHP]

Hope that clarifies things.

---

### Post by nmccrina on 2010-04-06
Haha, thanks for your help! I'm just stabbing in the dark right now :(. I can get things to work after trying every combination of brackets and not brackets, but if you asked me to explain it I'd be like ???. I guess I know just enough to be dangerous. :P

I'll keep plugging away, hopefully it starts to sink in through osmosis or something.

---

