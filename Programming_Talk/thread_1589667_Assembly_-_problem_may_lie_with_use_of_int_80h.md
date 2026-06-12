---
title: "Assembly - problem may lie with use of int 80h?"
date: 2010-10-06
forum: Programming Talk
---

### Post by BioBiro on 2010-10-06
Hi all - i've just written my first proper Assembler program (just a simple arithmetic thing), and it does nothing when I run it in a terminal. The strange thing is - i've loaded the code into Kdbg and stepped through the instructions while watching the registers, and everything works perfectly! Therefore, I assume it to be something wrong with the 'int 80h' call in the middle of the loop. It seems that 'ecx' must contain the (start) address of where the data to print is stored - can this not be a CPU register?

[PHP]
_start:
    mov eax,3    ; first number
    mov ebx,5    ; second number
    
loopx:
    lea ecx,[eax+ebx]    ; put sum of eax+ebx in ecx
    cmp ecx,1000
    jge quit
    push eax    ; save dword multiple on stack
    push ebx
    mov eax,4    ; setup int 80h for write
    mov ebx,1    ; specify stdout - ecx still has sum of eax+ebx
    mov edx,3    ; result will be no longer than three chars
    int 80h
    pop ebx    ; pop values off in reverse
    pop eax
    mov eax,ebx    ; put higher multiple into eax
    mov ebx,ecx    ; put the previous sum into ebx
    jmp loopx

quit:    
    mov eax,1    ; setup int 80h for exit
    mov ebx,0    ; zero exit code means a-ok
    int 80h[/PHP]

---

### Post by worksofcraft on 2010-10-07
> **BioBiro said:**
> It seems that 'ecx' must contain the (start) address of where the data to print is stored - can this not be a CPU register?


In answer to your question... **categorically NOT**: you cannot take the address of a cpu register. Registers are identified implicitly in the op-codes and you can only address proper memory locations... well ok on x86 processors there is also I/O space but registers are not part of hat either!

---

### Post by BioBiro on 2010-10-07
Thanks for clearing that up! Much appreciated. :)

---

