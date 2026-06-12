---
title: "[SOLVED] My MASM code doesn't work inside of NASM?"
date: 2008-09-14
forum: Programming Talk
---

### Post by tuffguy45 on 2008-09-14
Short story, college has a deal with microsoft so for my Assembly Programming class he told us we could either use MASM or TASM and he uses MASM in class and the only reason I say anything about TASM is because he mentions it as being able to be used in his syllabus but, I don't really see why since both of them more or less do the same thing with the same operating system compatibility.

Anyway, the MASM code he gave us to mess around with over the weekend doesn't work when I try to use it under NASM, is that supposed to happen?

here is my code

[PHP] DOSSEG
.STACK 100h
.DATA
cat	DW 5
dog	DW 4
mouse	DB 1

.CODE
startup:
mov ax,@data
mov ds,ax

mov ax,dog
add cat,ax

mov b1,mouse

mov al,01h
mov bh,0ch

mov ah,4ch
int 21h
END startup[/php]

and here is the errors I get from NASM

sam@sam-laptop:~/Documents/Assembley$ nasm -f elf prog1.asm
prog1.asm:2: error: parser: instruction expected
prog1.asm:23: error: parser: instruction expected

---

### Post by slavik on 2008-09-14
Linux doesn't have int 21h, it uses int 80h ... not only that, but the actual syscalls are different and the arguments have to be put into a different register.

look up Linux assembly tutorials.

---

### Post by tuffguy45 on 2008-09-14
Well that kind of kills it for me... since having to learn two different sets of assembly programming when I only need one certainly isn't going to work for me... Guess I could run a virtual machine or something inside of ubuntu...

Think it would be worthing trying to run masm through wine?

---

### Post by LaRoza on 2008-09-14
> **tuffguy45 said:**
> 
Think it would be worthing trying to run masm through wine?

Probably not, but it couldn't hurt.

---

### Post by Zugzwang on 2008-09-15
Note that the difference between the interrupts 21h and 80h reflect the difference between DOS and Linux.

*Additionally*, the NASM and MASM *syntax* is different. So in order to use MASM syntax, you might want to use Wine for running MASM and run your results in Dosbox. :-)

---

### Post by tuffguy45 on 2008-09-15
Interestingly enough, masm does work in wine. However, the linker he gave us did not and for some reason the gnu linker doesn't like .obj files. Are those windows specific? If not, can someone point me in the direction of a linux linker that will?

---

### Post by LaRoza on 2008-09-15
> **tuffguy45 said:**
> Interestingly enough, masm does work in wine. However, the linker he gave us did not and for some reason the gnu linker doesn't like .obj files. Are those windows specific? If not, can someone point me in the direction of a linux linker that will?

A linker links. When you assembly something it is easy, but it doesn't do anything without being linked. The reason why the linker won't work is because you are not using the same OS, ie. nothing to link to.

I suggest using DOSBox for this.

---

### Post by tuffguy45 on 2008-09-15
Thanks, that works good enough. Now I just need a debugger that displays the registers like debug.exe does. Any suggestions?

---

### Post by LaRoza on 2008-09-15
> **tuffguy45 said:**
> Thanks, that works good enough. Now I just need a debugger that displays the registers like debug.exe does. Any suggestions?

Don't write any bugs.

(Sorry, can't think of anything. Perhaps you could use debug.exe?)

---

### Post by tuffguy45 on 2008-09-15
I tried running it through wine AND dosbox and neither of them work...

Edit: Actually I lied, it does work, it was just waiting for me to give it a command.

---

### Post by Zugzwang on 2008-09-16
> **LaRoza said:**
> The reason why the linker won't work is because you are not using the same OS, ie. nothing to link to.


Hmmm, I guess that might not be right in this context. DOS programs are often not linked against any libraries and OS functions are simply called using the interrupts.

However, the object file format is different for the GNU tool chain and Microsoft's one, so they don't mix.

@OP: Did you try the internal debugger of Dosbox? It does display register contents.

---

### Post by tuffguy45 on 2008-09-16
Someone else in another topic suggested that to me and masm, link, and debug all work inside of dosbox. I had actually used dosbox to run some older computer games and physics simulations in physics 111/112.

---

