---
title: "An os with a menu. Assembly"
date: 2009-11-04
forum: Programming Talk
---

### Post by AlexZaim on 2009-11-04
hello people. I am doing an "os" (small) that's mainly a menu. It just prints some strings and highlights some words when you pres 1,2 or 3. And by pressing enter while a option is selected, it has to do something.
The problem is that the program gets stuck in the beginning ... and i don't know where is the problem. Can't run a debug because it's a bootable bin file. Can some one please tell me where is the error?
I'm using linux+ nasm
[code=asm]
[BITS 16]      
jmp 07C0h:start
	snd     db  'Sound'
	lsnd	equ	$-snd
	abt	db	'About'
	labt	equ	$-abt
	hlp	db	'Help'
	lhlp	equ	$-hlp

    start:

is1:
	call init
	;print "sound"
	mov	ax,1300h
	mov	bh,0
	mov	bl,2
	mov	cx,lsnd
	mov	dx,0
	push cs
	pop es
	mov bp,snd
	int 10h
wait_:
	mov	ah,00h
	int	16h

	cmp 	ah,13
	je	make_sound

	cmp	ah,49
	je	is1

	cmp	ah,50
	je	is2

	cmp	ah,51
	je	is3

	jmp	wait_
is2:	
	call init
	;print "About"
	mov	ax,1300h
	mov	bh,0
	mov	bl,2
	mov	cx,labt
	mov	dl,5
	push cs
	pop es
	mov bp,abt
	int 10h
	jmp	wait_

is3:	jmp	wait_
	
make_sound:
	mov	ax, 0E07h
	xor	bx, bx
	int	10h
	jmp	wait_
	
init:
	;print "sound"
	mov	ax,1300h
	mov	bh,0
	mov	bl,5
	mov	cx,lsnd
	mov	dx,0
	push cs
	pop es
	mov bp,snd
	int 10h
	;print "About"
	mov	ax,1300h
	mov	bh,0
	mov	cx,labt
	mov	dl,5
	push cs
	pop es
	mov bp,abt
	int 10h
	;print "Help"
	mov	ax,1300h
	mov	bh,0
	mov	cx,lhlp
	mov	dl,10
	push cs
	pop es
	mov bp,hlp
	int 10h
	ret


    times 510-($-$$) db 0
    dw 0AA55h
[/code]

The attachment shows the result of the execution. To me, it looks like he executes *init* then *;print "sound"* then gets stuck. Maybe the function that i use to wait for a char isn't the right one?

---

### Post by StunnerAlpha on 2009-11-04
I don't know much about assembly but it will be easier to help you if you fixed your code tags. Use [php] [/php] if you are trying to make it color coded.

---

### Post by Arndt on 2009-11-04
> **StunnerAlpha said:**
> I don't know much about assembly but it will be easier to help you if you fixed your code tags. Use [ php ] [ /php ] if you are trying to make it color coded.

I think you wanted to mention the php tags, not actually use them: they ended up as just space.

---

### Post by rCXer on 2009-11-04
Replace this
> **AlexZaim said:**
> 
wait_:
	mov	ah,00h
	int	16h


...with...
```

wait_:
	;Check if key was pressed.
	mov ah,1
	int 16h   ;Sets zf if a key wasn't pressed
	jz KeyNotPressed
		;Get it's value
		mov ah,0
		int 16h		
		jmp KeyPressed

	KeyNotPressed:
		xor ax,ax	;ax = 0
	KeyPressed:


```
This is an old hack but it should work. First you use check if a key was pressed.  If so then get it's value. If not then clear ax.  There's a good ASM forum at [http://www.asmcommunity.net/board/](http://www.asmcommunity.net/board/) .  It even has an OS development section.

---

