---
title: "Caller and Callee"
date: 2008-06-27
forum: Programming Talk
---

### Post by ladesidude on 2008-06-27
```

 assume callee needs three registers %ebx %edi %esi*/
   int func(int n1, int n2) {
   int temp = n1 * n2;
   return temp - (n1 + n2);
   }
   

   //caller %eax %edx %ecx
   int main()
   {
   int a = 4;
   int b = 8;
   int c = func(a, b);
   return 0;
   }


   /*

// my work here, can someone please help in verifying it?  //Basically, I dont want to overwrite the callee before saving 
// the values

pushl   %ebp                   
movl    %esp, %ebp         
movl    8(%ebp), %ecx      ;; addressing modes -- copy a into ecx 
movl    12(%ebp), %edx	   ;; addressing modes -- copy b into edx	
pushl   %edi						;; need to be pushed onto the stack before altering them
push    %esi						;; need to be pushed onto the stack before altering them
push    %ebx						;; need to be pushed onto the stack before altering them
movl    %edx,%edi				;; copy b on edi
movl		%ecx, %esi			;;	copy a on esi
imull  (%esi,%edi), %ebx  ;; multiply a * b and store value in ebx
subl   %esi, %ebx				;; subtract a from temp
subl   %edi, %ebx				;; subtract b from temp
movl  %ebx, %eax				;; set up return value
popl   %edi						;; return
popl   %esi						;; return
popl   %ebx						;; return
movl    %ebp, %esp         ;; reset the stack pointer
popl    %ebp               ;; reset the frame pointer
ret                        ;; return


```

Thanks for your help:)

---

### Post by NathanB on 2008-06-27
Ugh... (g)as is umm... smelly!  :)

Here's a version in NASM.

[php]
; nasm -f elf -o mathfunc.o mathfunc.asm
; ld -o mathfunc mathfunc.o

global _start

section .data

	resstr	db	"The result is: "
	reslen	equ	$ - resstr

section .bss

	buffer	resb	256

section .text
_start:

	; do a call to compute( 5, 6 )
	push 6
	push 5
	call compute

	; display text
	push eax
     mov eax, 4         ; __NR_write
     mov ebx, 1         ; stdout
	mov ecx, resstr
	mov edx, reslen
	int 80h
	pop eax

	; convert result to a decimal string
	call eax2dec

	; display result	
     mov eax, 4         ; __NR_write
     mov ebx, 1         ; stdout
	mov ecx, buffer
	int 80h

	mov eax, 1		; __NR_exit
	int 80h

compute:
	; INPUT:  two dword args on the stack
	; OUTPUT:  'eax' contains the result
	push	ebp
	mov	ebp, esp
	and	esp, 0xfffffffc
	push	edx
	push	ebx
	mov	eax, [ebp+12]
	mov	ebx, [ebp+8]
	imul	ebx
	add	ebx, [ebp+12]
	sub	eax, ebx
	pop	ebx
	pop	edx
	mov	esp, ebp
	pop	ebp
	ret	8

eax2dec:
	; INPUT:  'eax' contains number to convert
	; OUTPUT:  'edx' contains length of string
	push ecx
	push ebx
	mov ebx, 10
	xor ecx, ecx

.loop01:
	cdq
	div ebx
	push edx
	inc ecx
	cmp eax, 0
	jnz .loop01

	xor edx, edx
.loop02:
	pop eax
	add eax, 48
	mov [buffer + edx], al
	inc edx
	dec ecx
	jnz .loop02

	; add a 'newline' character
	mov BYTE [buffer + edx], 10
	inc edx
	pop ebx
	pop ecx
	ret
[/php]

Nathan.

---

### Post by slavik on 2008-06-27
I don't like the way you use registers ... why not use registers that are next to eachother in the alphabetical sense? (eax, ebx, ecx).

---

### Post by LaRoza on 2008-06-27
> **slavik said:**
> I don't like the way you use registers ... why not use registers that are next to eachother in the alphabetical sense? (eax, ebx, ecx).

Theres more than one way to do it.

---

### Post by ladesidude on 2008-06-27
This is a requirement that I have to follow, but..apart from that, have I done other things right?

---

### Post by NathanB on 2008-06-27
> **slavik said:**
> I don't like the way you use registers ... why not use registers that are next to eachother in the alphabetical sense? (eax, ebx, ecx).

???  What part of the code are you talking about?

Nathan.

---

### Post by NathanB on 2008-06-27
> **ladesidude said:**
> This is a requirement that I have to follow, but..apart from that, have I done other things right?

Depends on your goal.  Your subject line is "Caller and Callee", so are you trying to mimic the C calling convention where the Caller is responsible for cleaning up the stack?  If so, here a version of the above with ";<<<" to indicate the few lines that were modified to mimic a C-style call.

[php]
; nasm -f elf -o cmathfunc.o cmathfunc.asm
; ld -o cmathfunc cmathfunc.o

global _start

section .data

	resstr	db	"The result is: "
	reslen	equ	$ - resstr

section .bss

	buffer	resb	256

section .text
_start:

	; do a call to compute( 5, 6 )
	push 6
	push 5
	call compute

	; display text
	push eax
     mov eax, 4         ; __NR_write
     mov ebx, 1         ; stdout
	mov ecx, resstr
	mov edx, reslen
	int 80h
	pop eax

	; convert result to a decimal string
	call eax2dec
	add esp, 8			;<<<

	; display result	
     mov eax, 4         ; __NR_write
     mov ebx, 1         ; stdout
	mov ecx, buffer
	int 80h

	mov eax, 1		; __NR_exit
	int 80h

compute:
	; INPUT:  two dword args on the stack
	; OUTPUT:  'eax' contains the result
	push	ebp
	mov	ebp, esp
	and	esp, 0xfffffffc
	push	edx
	push	ebx
	mov	eax, [ebp+12]
	mov	ebx, [ebp+8]
	imul	ebx
	add	ebx, [ebp+12]
	sub	eax, ebx
	pop	ebx
	pop	edx
	;mov	esp, ebp		;<<<
	pop	ebp
	;ret	8				;<<<
	ret

eax2dec:
	; INPUT:  'eax' contains number to convert
	; OUTPUT:  'edx' contains length of string
	push ecx
	push ebx
	mov ebx, 10
	xor ecx, ecx

.loop01:
	cdq
	div ebx
	push edx
	inc ecx
	cmp eax, 0
	jnz .loop01

	xor edx, edx
.loop02:
	pop eax
	add eax, 48
	mov [buffer + edx], al
	inc edx
	dec ecx
	jnz .loop02

	; add a 'newline' character
	mov BYTE [buffer + edx], 10
	inc edx
	pop ebx
	pop ecx
	ret
[/php]

Nathan.

---

### Post by slavik on 2008-06-28
> **LaRoza said:**
> Theres more than one way to do it.
you obviously have not seen assembly in DOS and assembly in Linux.

In Linux, every system call in assembly contains the function call in eax, the first argument in ebx, then ecx, edx, and so on ...

in DOS though ... just to print a single character, you have to put the function number in eax, the character in edx, some other argument somewhere else and call 21h (or was it 10h? I don't remember).

There are many ways to do things, some are nicer than others.

---

### Post by NathanB on 2008-06-28
> **slavik said:**
> in DOS though ... just to print a single character, you have to put the function number in eax, the character in edx, some other argument somewhere else and call 21h (or was it 10h? I don't remember).

You used a 32-bit DOS??   :)

It sometimes was even more complicated than you remember.  Some functions had subfunctions.  You'd put the function number in 'ah' and the sub-function number in 'al', but if you're clever, you'd actually do a "mov ax, <number>" to satisfy both needs with a single instruction.

Nathan.

---

### Post by slavik on 2008-06-28
> **NathanB said:**
> You used a 32-bit DOS??   :)

It sometimes was even more complicated than you remember.  Some functions had subfunctions.  You'd put the function number in 'ah' and the sub-function number in 'al', but if you're clever, you'd actually do a "mov ax, <number>" to satisfy both needs with a single instruction.

Nathan.
I was referring to the print character as having a sub function, but when I saw a Linux assembly tutorial, I was like "WTF?! why didn't they teach THIS instead?!"

EDIT: I admit it, it was 16bit DOS under Windows XP ... :-\

---

### Post by jim_24601 on 2008-06-30
Hang on, hang on! Where does all this stuff about system calls come in? There's nothing in the original post that suggests any requirement to print things out--it seems to be exploring how a compiler would compile and call a simple function. System calls are a completely different beast, and you wouldn't normally see them in user code these days; they'd be squirreled away in some pre-built library.

To the OP: perhaps it would help if you gave us a bit more information on what you're actually trying to do. I take it you're effectively hand-compiling your callee "func"--your version will more or less do what the C says, but I'm not sure you've entirely grasped the point of the exercise.

There is one out-and-out error: you are restoring your registers in the wrong order. You must pop them in the reverse order that you pushed them or they will be swapped and the caller will likely crash. (If it expects them to be preserved, which I'm assuming that it does).

I'm going to make a wild guess that you're not supposed to apply any optimisation. You've made a few optimisations of the type that a human programmer will do instinctively but your first-pass naive compilation stage won't. Your function has a local variable which you're storing in ebx. This is fine, but if I were setting a question like this I'd be looking for an understanding of how a compiler sets up a local variable on the stack. Your function prologue looks a little odd--you load your parameters into scratch registers, then save the registers you need to save, then transfer them across. I'd expect your first pass from a real compiler to look like: (note I'm using nasm syntax as I agree that gas is nasty)

Set up the stack frame (push ebp; mov ebp, esp; you got this bit fine).
Reserve stack space for local variables ('temp').
Save registers (that the caller is expecting will be preserved).
Load the two parameters, and multiply them. Save the result in 'temp'. (The store to memory might later be optimised away.)
Load the two parameters, and add them. Load 'temp'. Subtract the result of the add from 'temp'. Save the result in 'temp'. (Most, if not all, of the memory accesses for this source line might later be optimised away.)
Load 'temp' into the return register (on x86, this will be al/ax/eax/rax, unless the compiler is VERY perverse). (A good optimiser might shuffle its register allocation so that the end result just happens to be in eax when it's needed.)
Restore the registers it saved (in the right order).
Pull the stack back over the local variables.
Restore the previous stack frame. (You have a redundant 'mov ebp, esp' here, since ebp is about to be popped from the stack anyway.)
Return.

---

### Post by slavik on 2008-06-30
> **jim_24601 said:**
> Hang on, hang on! Where does all this stuff about system calls come in? There's nothing in the original post that suggests any requirement to print things out--it seems to be exploring how a compiler would compile and call a simple function. System calls are a completely different beast, and you wouldn't normally see them in user code these days; they'd be squirreled away in some pre-built library.

To the OP: perhaps it would help if you gave us a bit more information on what you're actually trying to do. I take it you're effectively hand-compiling your callee "func"--your version will more or less do what the C says, but I'm not sure you've entirely grasped the point of the exercise.

There is one out-and-out error: you are restoring your registers in the wrong order. You must pop them in the reverse order that you pushed them or they will be swapped and the caller will likely crash. (If it expects them to be preserved, which I'm assuming that it does).

I'm going to make a wild guess that you're not supposed to apply any optimisation. You've made a few optimisations of the type that a human programmer will do instinctively but your first-pass naive compilation stage won't. Your function has a local variable which you're storing in ebx. This is fine, but if I were setting a question like this I'd be looking for an understanding of how a compiler sets up a local variable on the stack. Your function prologue looks a little odd--you load your parameters into scratch registers, then save the registers you need to save, then transfer them across. I'd expect your first pass from a real compiler to look like: (note I'm using nasm syntax as I agree that gas is nasty)

Set up the stack frame (push ebp; mov ebp, esp; you got this bit fine).
Reserve stack space for local variables ('temp').
Save registers (that the caller is expecting will be preserved).
Load the two parameters, and multiply them. Save the result in 'temp'. (The store to memory might later be optimised away.)
Load the two parameters, and add them. Load 'temp'. Subtract the result of the add from 'temp'. Save the result in 'temp'. (Most, if not all, of the memory accesses for this source line might later be optimised away.)
Load 'temp' into the return register (on x86, this will be al/ax/eax/rax, unless the compiler is VERY perverse). (A good optimiser might shuffle its register allocation so that the end result just happens to be in eax when it's needed.)
Restore the registers it saved (in the right order).
Pull the stack back over the local variables.
Restore the previous stack frame. (You have a redundant 'mov ebp, esp' here, since ebp is about to be popped from the stack anyway.)
Return.
you missed the point of the syscall example. like I've said in an earlier post, there is a right way to do things and a wrong way and the syscall example shows an example of each.

---

### Post by jim_24601 on 2008-06-30
> **slavik said:**
> you missed the point of the syscall example. like I've said in an earlier post, there is a right way to do things and a wrong way and the syscall example shows an example of each.

And there's a right and a wrong way to boil an egg--that doesn't necessarily mean they're relevant to a discussion of compiler techniques. :) :) The OP asked for a critique of his solution without actually specifying what the problem was. Nathan then came up with his own version, but added some extra sugar in the form of a syscall to print the results. We then went off on a discussion of syscalls. My point is, this is all very well, but it's the one bit of Nathan's example that doesn't relate to the original post. There's no syscall in the original C code, and they use a different calling mechanism anyway.

---

### Post by NathanB on 2008-06-30
> **jim_24601 said:**
> And there's a right and a wrong way to boil an egg--that doesn't necessarily mean they're relevant to a discussion of compiler techniques. :) :) The OP asked for a critique of his solution without actually specifying what the problem was. Nathan then came up with his own version, but added some extra sugar in the form of a syscall to print the results. We then went off on a discussion of syscalls. My point is, this is all very well, but it's the one bit of Nathan's example that doesn't relate to the original post. There's no syscall in the original C code, and they use a different calling mechanism anyway.

I think you are right that the OP wants to mimic a "first-pass" solution.  In that case, his posted code...
[php]movl    8(%ebp), %ecx      ;; addressing modes -- copy a into ecx 
movl    12(%ebp), %edx	   ;; addressing modes -- copy b into edx	
...
movl    %edx,%edi				;; copy b on edi
movl		%ecx, %esi			;;	copy a on esi
imull  (%esi,%edi), %ebx  ;; multiply a * b and store value in ebx
subl   %esi, %ebx				;; subtract a from temp
subl   %edi, %ebx				;; subtract b from temp
[/php]
...which trashes 6 registers (uses a local variable) is a lot closer to the correct answer than my code...
[php]    mov    eax, [ebp+12]
    mov    ebx, [ebp+8]
    imul    ebx
    add    ebx, [ebp+12]
    sub    eax, ebx
[/php]
...which trashes only 3 registers (no local variable) but doesn't represent a naive compiler production.

Nathan.

---

### Post by NathanB on 2008-06-30
> **jim_24601 said:**
> ....
Pull the stack back over the local variables.
Restore the previous stack frame. (You have a redundant 'mov ebp, esp' here, since ebp is about to be popped from the stack anyway.)
Return.

Uh... depends on which calling convention is used.

The above is correct for a Standard Call (where the 'Callee' is responsible for restoring the stack).

A CCall would adjust the stack to remove the local variables, but it would leave it to the 'Caller' to restore the stack frame.

Nathan.

---

### Post by jim_24601 on 2008-06-30
> **NathanB said:**
> Uh... depends on which calling convention is used.

The above is correct for a Standard Call (where the 'Callee' is responsible for restoring the stack).

A CCall would adjust the stack to remove the local variables, but it would leave it to the 'Caller' to restore the stack frame.


Sorry--by 'restore the stack frame' I just meant 'pop ebp'. I didn't mean that the callee should wind the stack back past its own actual parameters with a 'ret nnnn' instruction.

(And I confess, I had to read through your example a couple of times to confirm that it did the same as the C--you optimised a bit further than the compiled code I'm used to reading!)

---

