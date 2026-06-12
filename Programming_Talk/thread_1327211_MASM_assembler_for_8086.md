---
title: "MASM assembler for 8086"
date: 2009-11-15
forum: Programming Talk
---

### Post by shababhsiddique on 2009-11-15
Is there any assembler with identical syntax as MASM as used in emu8086 to use in Ubuntu. I am looking for a very basic assembler to use in linux in my university lab. NASM seems a little hazy .. can any one teach me its syntax by pointing out the differnce of NASM and MASM??

Thanks in advance. And plz try to cover the basic i am new to assembly.

---

### Post by 0cton on 2009-11-15
If you are new you could easily try NASM's syntax you will get used to it.
this site will help you:
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)
and here is a program of mine a echo clone in asm (linux of course :P)
```

;try it with one arguments!!!
section .data
	space	 :  db 32	;32 is a space in ascii
	eol      :  db 10	;10 is \n in ascii
	arg_len  :  dd 0
section .text
	global _start
_start:
	pop eax 		;get the number of arguments (the arguments are on the stack)
	dec eax			;since we won't print the programs name witch is an argument as well
	pop ecx			;arg[0] is the program name we don't need it
	mov [arg_len],eax 	;put the number of arguments in arg_len
	.mloop:
	pop ecx 		;get next arg
	call _get_len 		;_get_len puts the len in edx and expects the string in ecx
	call _print_stdout	;since _get_len already has the string in ecx and it's length in edx
	call _print_space	;print a space :P    
	dec dword [arg_len]	;one less
	cmp [arg_len],dword 1 	;we stop at 1 since we don't want to print a space at the end do we :P
	jne .mloop
	pop ecx 		;get next arg
	call _get_len 		;_get_len puts the len in eax and expects the string in ebx
	call _print_stdout	;print last arg (without a space like in the loop)
	call _print_eol		;prints an end of line
	mov eax,1            	; The system call for exit (sys_exit)
	mov ebx,0            	; Exit with return code of 0 (no error)
	int 80h			;call the kernel (linux)
	ret
_print_stdout: ; already expects ecx to contain the string and edx it's length
	mov eax,4 	; The system call for write (sys_write)
	mov ebx,1	; File descriptor 1 - standard output
	int 80h		; call the kernel
	ret
_print_eol:		;prints a newline
	mov ecx,eol
	mov edx,1
	call _print_stdout
	ret
_print_space:		;prints a space
	mov ecx,space
	mov edx,1
	call _print_stdout
	ret
_get_len: 		;gets the length of a string return in eax expects the string in eax
	mov edx,0
	push ecx
	.get_len_loop:
	cmp [ecx],byte 0 ;0 terminates a string
	jne .get_len_inc ;if it's not the end go to .get_len_inc
	pop ecx		;get original adress from the stack
	ret		 ;if jne fails it means the string ended therefore we must return
	.get_len_inc:
	inc edx ;increment the length
	inc ecx ;go to next character/byte
	jmp .get_len_loop	;continue the loop

```
Remember it still has a few bugs and stuff :P

---

### Post by Zugzwang on 2009-11-15
If you really want to do 8086 assembly, forget about NASM or even programming for Linux (with it). You do need to use the 32-bit registers for this, which do not exist on the 8086. Also the memory model is totally different. Especially if you are a beginner, you should seriously consider sticking to the tools and processor model that you know as digging into the more complicated stuff is almost guaranteed to confuse you as a beginner.

I would say that you might want to try to get the "free evaluation version" of emu8086 running in Wine.

---

### Post by shababhsiddique on 2009-11-15
> **Zugzwang said:**
> If you really want to do 8086 assembly, forget about NASM or even programming for Linux (with it). You do need to use the 32-bit registers for this, which do not exist on the 8086. Also the memory model is totally different. Especially if you are a beginner, you should seriously consider sticking to the tools and processor model that you know as digging into the more complicated stuff is almost guaranteed to confuse you as a beginner.

I would say that you might want to try to get the "free evaluation version" of emu8086 running in Wine.

thanks .. Can you tell me which wine is most compatible with it. I faced problem when using wine to run emu8086 in Intrepid . havent tried in karmic yet. I will be also happy if you can tell me where can i learn to work with AASM..

---

### Post by shababhsiddique on 2009-11-15
> **0cton said:**
> If you are new you could easily try NASM's syntax you will get used to it.
this site will help you:
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)
and here is a program of mine a echo clone in asm (linux of course :P)
 Remember it still has a few bugs and stuff :P

Thanx Octon for the reply.......Unfortunately I am not in a stage to understand your script!. Can you help me out by defining a few comparisons of MOV,  INT ,LEA, in NASM and MASM??

---

### Post by rCXer on 2009-11-15
You may also be interested in [jwasm](http://www.japheth.de/JWasm.html), a masm clone that runs in linux.  I havn't tried it yet...

---

### Post by shababhsiddique on 2009-11-15
> **rCXer said:**
> You may also be interested in [jwasm]("http://www.japheth.de/JWasm.html"), a masm clone that runs in linux.  I havn't tried it yet...

Thanks rCxer I was looking for something like that...Can you illustrate how to use it? I have my masm code in test.asm in my home folder what should i write in the terminal?

---

### Post by Zugzwang on 2009-11-16
> **shababhsiddique said:**
> thanks .. Can you tell me which wine is most compatible with it. I faced problem when using wine to run emu8086 in Intrepid . havent tried in karmic yet. I will be also happy if you can tell me where can i learn to work with AASM..

The application is listed as working well with Wine, probably it is really your Wine version and/or configuration that doesn't work:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11711](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11711)

---

### Post by shababhsiddique on 2009-11-17
> **Zugzwang said:**
> The application is listed as working well with Wine, probably it is really your Wine version and/or configuration that doesn't work:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11711](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11711)

Yes may be it was . ... its working fine in Karmic. Thanks for the suggestion agian.....Stil if you know any open source GUI assembler i would be happy to know.

---

