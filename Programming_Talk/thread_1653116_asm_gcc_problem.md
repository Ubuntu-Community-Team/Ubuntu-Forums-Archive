---
title: "asm gcc problem"
date: 2010-12-26
forum: Programming Talk
---

### Post by VyegreS on 2010-12-26
I have the code:
 
 > 
 char scanCode, inpChar;
 asm {
       mov ah,0          ;
       int 16h           ;
       mov scanCode,ah   ;
       mov inpChar,al    ;
    }

Can somebody translate this to AT&T style.
I try something like this:
>      asm("movb $0,%ah \n\t"
        "int $0x16 \n\t" 
        "movb %%ah, %0": "=g"(scanCode) :"0" (scanCode) 
        );
but it is don't work.

I must to do something like this [http://cs.haifa.ac.il/courses/com_org/2006/int16.htm](http://cs.haifa.ac.il/courses/com_org/2006/int16.htm)  on gcc

help me please!

---

### Post by Zugzwang on 2010-12-26
You do know that the functions provided by the "interrupt 16h" are *not* available in Linux, right? So your code wouldn't run in Linux anyway (except in a dosbox, but then, you won't use gcc for compiling).

---

### Post by VyegreS on 2010-12-26
Yes, I know about this. I write my own system (OS), this is my laboratory work at University.

I use gcc only for compiling. (gcc -ffreestanding -c -o file.o file.c)

Can you help me?

---

### Post by Arndt on 2010-12-26
> **VyegreS said:**
> Yes, I know about this. I write my own system (OS), this is my laboratory work at University.

I use gcc only for compiling. (gcc -ffreestanding -c -o file.o file.c)

Can you help me?

I haven't used this myself before, but I get the code to pass the compiler if I use %% in the first line, just as in the third line.

---

### Post by VyegreS on 2010-12-26
> **Arndt said:**
> I haven't used this myself before, but I get the code to pass the compiler if I use %% in the first line, just as in the third line.


> 
     asm("movb $0,%%ah \n\t"
        "int $0x16 \n\t" 
        "movb %%ah, %0": "=g"(scancode) :"0" (scancode)
        );

ktty.c: Assembler messages:
ktty.c:80: Error: too many memory references for `mov'
ktty.c:85: Error: suffix or operands invalid for `mov'


Please write example.

---

### Post by Arndt on 2010-12-26
> **VyegreS said:**
> ktty.c: Assembler messages:
ktty.c:80: Error: too many memory references for `mov'
ktty.c:85: Error: suffix or operands invalid for `mov'


Please write example.

I just did this:

```
int foo()
{
    char scanCode;

asm("movb $0,%%ah\n\t"
"int $0x16\n\t"
"movb %%ah, %0": "=g"(scanCode) :"0" (scanCode)
);
}
```

---

### Post by VyegreS on 2010-12-26
It's cool. Thanks you very much!

---

### Post by VyegreS on 2010-12-27
If processor works in protected mode use this:
```

char getch(void) {
    char x;
    asm(
        "inb $0x60, %%al\n\t"
        "movb %%al, %0 \n\t": "=g"(x) 
    );
return x;
}

```

---

