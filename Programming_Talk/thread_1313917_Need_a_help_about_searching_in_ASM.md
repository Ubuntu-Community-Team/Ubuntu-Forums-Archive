---
title: "Need a help about searching in ASM"
date: 2009-11-04
forum: Programming Talk
---

### Post by vietwow on 2009-11-04
Dear all,

I'm using WinXP SP2 32-bit OS on Intel processor with WinASM + masm compiler

I need to write a small app to find a file with path "C:\file.txt". If this file is exist, it will print a message like "File is exist", otherwise it will print "File is not exist"

This is my program but it doesn't work :

```
.MODEL	SMALL
.STACK	100h
.data
	vietwow db "File is exits$"
	vietwow1 db "File is not exits$"
	file db "C:\file.txt",0
.CODE

mov ax, @data
mov ds, ax

MOV DX, OFFSET file ; filename need to be search
mov cx, 3Fh ; attribute, any
mov ah, 4eh ; find first file
int 21h

;if not available, jmp to label "notavailable"
jc notavailable

;if avaiable

mov ah,9
mov dx, offset vietwow
int 21h

notavailable:
	mov ds, ax
	mov ah,9
	mov dx, offset vietwow1
	int 21h

;Exit
	MOV	AH, 4Ch
	INT	21h

	END
```

When I compile this code, everything is ok in compile progress. But when I run this program, it doesn't print the content as expect ("File is exits" or "File is not exits"). Anyboy help me ?

Thanx
Best Regards,

---

### Post by Arndt on 2009-11-04
> **vietwow said:**
> Dear all,

I'm using WinXP SP2 32-bit OS on Intel processor with WinASM + masm compiler

I need to write a small app to find a file with path "C:\file.txt". If this file is exist, it will print a message like "File is exist", otherwise it will print "File is not exist"

This is my program but it doesn't work :

```
.MODEL	SMALL
.STACK	100h
.data
	vietwow db "File is exits$"
	vietwow1 db "File is not exits$"
	file db "C:\file.txt",0
.CODE

mov ax, @data
mov ds, ax

MOV DX, OFFSET file ; filename need to be search
mov cx, 3Fh ; attribute, any
mov ah, 4eh ; find first file
int 21h

;if not available, jmp to label "notavailable"
jc notavailable

;if avaiable

mov ah,9
mov dx, offset vietwow
int 21h

notavailable:
	mov ds, ax
	mov ah,9
	mov dx, offset vietwow1
	int 21h

;Exit
	MOV	AH, 4Ch
	INT	21h

	END
```

When I compile this code, everything is ok in compile progress. But when I run this program, it doesn't print the content as expect ("File is exits" or "File is not exits"). Anyboy help me ?

Thanx
Best Regards,

Is a program for Windows XP supposed to work in Ubuntu?

---

### Post by vietwow on 2009-11-04
Dear Arndt,

It's just a program that written in ASM and run on on WinXP SP2, not related to Ubuntu

Regards,

---

### Post by Arndt on 2009-11-04
> **vietwow said:**
> Dear Arndt,

It's just a program that written in ASM and run on on WinXP SP2, not related to Ubuntu

Regards,

But you're posting on an Ubuntu forum.

---

### Post by vietwow on 2009-11-04
> **Arndt said:**
> But you're posting on an Ubuntu forum.

Yeah, I know it, but I was read clearly about this :D

> This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any programming language is allowed. 

Regards,

---

### Post by Arndt on 2009-11-04
> **vietwow said:**
> Yeah, I know it, but I was read clearly about this :D



Regards,

Fair enough, but it's very directly related to a completely different operating system.

But if someone else here knows the solution, I won't stand in the way :-)

---

### Post by mmix on 2009-11-04
Here, they are waiting for you. :)

[http://www.asmcommunity.net/board/](http://www.asmcommunity.net/board/)

---

### Post by Npl on 2009-11-04
using interrupts makes this a DOS program and not a Windows program (I never understand why someone would want to code ASM for DOS). those interrupts dont do the same thing in Windows(likely they are just ignored).

Maybe you need to tell masm to create a DOS executeable, cause Im sure it defaults to output a Win32 executeable.

---

### Post by rCXer on 2009-11-04
Hey guys be nice :p
Don't have masm but here's my best shot.  Get rid of "mov ds, ax" under notavailable because you modified ax before that. Also set al=0 before finding the file to be safe. And don't forget to jump if the file is available!
```

.MODEL	SMALL
.STACK	100h
.data
	vietwow db "File is exits$"
	vietwow1 db "File is not exits$"
	file db "C:\file.txt",0
.CODE

mov ax, @data
mov ds, ax

mov al, 0   ; Just to be safe
MOV DX, OFFSET file ; filename need to be search
mov cx, 3Fh ; attribute, any
mov ah, 4eh ; find first file
int 21h

;if not available, jmp to label "notavailable"
jc notavailable

;if avaiable

mov ah,9
mov dx, offset vietwow
int 21h
jmp ExitProgram

notavailable:
	mov ah,9
	mov dx, offset vietwow1
	int 21h

ExitProgram:
	MOV	AH, 4Ch
	INT	21h

	END

```

> **Npl said:**
> (I never understand why someone would want to code ASM for DOS)

...because it's fun ;)

---

