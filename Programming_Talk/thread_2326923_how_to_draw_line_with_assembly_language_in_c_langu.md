---
title: "how to draw line with assembly language in c language?"
date: 2016-06-06
forum: Programming Talk
---

### Post by zerop2 on 2016-06-06
how to draw line with assembly language in c language in both terminal and xwindow?

```
martin@ubuntu:~/Downloads$ gcc -o main main.c
main.c: Assembler messages:
main.c:4: Error: too many memory references for `mov'
main.c:5: Error: too many memory references for `mov'
main.c:6: Error: junk `h' after expression
main.c:6: Error: operand size mismatch for `int'
main.c:7: Error: too many memory references for `mov'
main.c:8: Error: too many memory references for `mov'
main.c:9: Error: too many memory references for `mov'
main.c:11: Error: invalid char '[' beginning operand 1 `[bx]'
main.c:12: Error: no instruction mnemonic suffix given and no register operands; can't size instruction
main.c:13: Error: too many memory references for `cmp'




```
```

#include<stdio.h>
 
void main() {
__asm("mov ah,00h");
__asm("mov al,13h");
__asm("int 10h");
__asm("mov ds,40960");
__asm("mov ax, 44h");
__asm("mov bx,0000");
__asm("START:");
__asm("mov [bx],ax");
__asm("inc bx");
__asm("cmp bx,20");
__asm("JL START");
}

```

---

### Post by T.J. on 2016-06-08
> **zerop2 said:**
> how to draw line with assembly language in c language in both terminal and xwindow?

```
martin@ubuntu:~/Downloads$ gcc -o main main.c
main.c: Assembler messages:
main.c:4: Error: too many memory references for `mov'
main.c:5: Error: too many memory references for `mov'
main.c:6: Error: junk `h' after expression
main.c:6: Error: operand size mismatch for `int'
main.c:7: Error: too many memory references for `mov'
main.c:8: Error: too many memory references for `mov'
main.c:9: Error: too many memory references for `mov'
main.c:11: Error: invalid char '[' beginning operand 1 `[bx]'
main.c:12: Error: no instruction mnemonic suffix given and no register operands; can't size instruction
main.c:13: Error: too many memory references for `cmp'




```
```

#include<stdio.h>
 
void main() {
__asm("mov ah,00h");
__asm("mov al,13h");
__asm("int 10h");
__asm("mov ds,40960");
__asm("mov ax, 44h");
__asm("mov bx,0000");
__asm("START:");
__asm("mov [bx],ax");
__asm("inc bx");
__asm("cmp bx,20");
__asm("JL START");
}

```

When you say "Draw a line" what do you mean, exactly?  Assuming I understand what you are trying to do, how you are doing it makes no sense to me.  You're using old PC style BIOS calls for old EGA/VGA standards.  Why do that?  Not only will they not work if your firmware is incompatible somewhere, but it is un-portable code and hard to debug. 

 What I would suggest is that if you want to draw lines in terminal windows or on a standard text terminal that you stick with C instead of assembly; and then take a look at the NCurses library.  It should do everything you need on a text level.  If you are looking for full blown graphics abilities in X11, you should consider something like the GTK or Qt using OpenGL instead.

Assembly should only be used as a "last resort" and if you will forgive me for saying so - it should NEVER be used in user applications, as it makes porting and software maintenance a severe PITA.

---

