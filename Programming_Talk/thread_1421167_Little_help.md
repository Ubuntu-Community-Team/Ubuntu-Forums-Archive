---
title: "Little help"
date: 2010-03-03
forum: Programming Talk
---

### Post by Lord DEA on 2010-03-03
Hello every1,
I'm trying to learn how parameter passing works between C and asm.
what I'm trying to do is a simple program in C that creates an integer variable and calls an assembly function that multiplies the number by 2 and then uses printf to print the result and then go back to C.
Here's what I've got:

The C code:
```

#include <stdio.h>

void duplicate() __attrib__ ((cdecl));

int main(){
    int a = 5;
    duplicate(a);
    return 0;
}

```

and the assembly code:
```

extern printf

SECTION .data
fmt:   db "%d",10,0

SECTION .bss
number:  resd 1

SECTION .text
    push   ebp
    mov    ebp,esp

    ;this is the part I'm missing...
    ;where do i get the number from?
    
    push   number
    push   fmt
    call   printf

    leave
    ret


```

Any help + suggestions about would be very appreciated...

---

### Post by Zugzwang on 2010-03-05
Have a look at some information about [calling conventions]("http://en.wikipedia.org/wiki/Calling_convention"). Then try to find out what calling conventions are used by GCC for your 32-bit application.

If you can't find it out, use the "-s" (or was it "-S"?) parameter to GCC to get some assembler source code for the main function printed out. Examine it to see how the parameters are passed.

---

### Post by pbrane on 2010-03-05
You can also compile with debug on and run it in gdb. The command *disassemble main* will show you the assembly. I would recommend passing more that one argument to learn about C calling conventions.

Take Zugzwang's suggestion and learn about calling conventions and how parameters are passed on the stack in C. You've saved you stack pointer so you're on the right track.

---

### Post by Lord DEA on 2010-03-05
Thanks a lot
now I know that in my x86 parameters are passed in the stack,
already finished these pieces of code.

this eases my life a lot.

And another question I forgot to post:
¿Does anyone know about a good front-end degubber that allows me to view the registers while the program is executed one instruction at a time?
I already have DDD, but haven't managed to get it to do what I want, or simply I haven't RTFM.... :S

---

### Post by MadCow108 on 2010-03-05
you can view the registers with info register (or i r)
the floating point registers with info float

info frame prints information on the current frame and step single instructions with si and ni
$pc holds the program counter register

you can use the display command to display all kinds of stuff (also in ddd)
its worth reading about

ddd should be a fine debugger for assembly
it has loads of features like the register window (status-> registers) or the machine code window (view-> machine code window)
and of course everything gdb provides too

---

### Post by pbrane on 2010-03-06
> **Lord DEA said:**
> 

And another question I forgot to post:
¿Does anyone know about a good front-end degubber that allows me to view the registers while the program is executed one instruction at a time?
I already have DDD, but haven't managed to get it to do what I want, or simply I haven't RTFM.... :S

Have you looked at Nemiver? It's a graphical debugger for GNOME. It might do what you want. It's in the repos, easy to install - easy to remove.

---

### Post by Lord DEA on 2010-03-11
Thanks a lot, you guys sure help a lot :D
And for the record, I'm happy with Insight, it opens an asm executable, and shows the source, plus, it allows me to open different windows that show: the stack, registers, memory, and many  more...
I strongly recommend it.

---

