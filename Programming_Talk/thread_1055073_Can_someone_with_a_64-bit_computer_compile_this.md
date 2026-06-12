---
title: "Can someone with a 64-bit computer compile this"
date: 2009-01-30
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-30
ok heres the code:

```
%DEFINE OFFSET 48
[BITS 64]
section .data
    fmt db 'eax=%d',10,0
section .bss
    input resb 10
section .text
extern printf
global main
    
main:
    call debug
    ;push qword 5
    ;push fmt
    ;call debug
    ;call printf
    ;add rsp,8
    ;call exit
print:
    mov rax,4
    mov rbx,1
    int 80h
    ret    
exit:
    mov rax,1
    mov rbx,0
    int 80h
    ret
read:
    mov rax,3
    mov rbx,1
    int 80h
    ret
debug:
    push rax
    push rbx
    push rcx
    push rdx
    mov rax,4
    mov rbx,1
    mov rcx,'debuging...\n'
    mov rdx,13
    int 80h
    pop rdx
    pop rcx
    pop rbx
    pop rax
    ret
```

i was messing around with NASM and wrote this...it breaks the terminal (i get weird characters) that its run in on my machine and want to see if the same happens with you guys if you have a second

---

### Post by jimi_hendrix on 2009-01-30
forgot...make sure you link with gcc

---

### Post by Zugzwang on 2009-01-30
Haven't ran it, but since you commented out "call exit", after "debug" has returned, the function "print" is called next. This will cause your "strange" characters. Then "ret" should somehow terminate the program.

---

### Post by jimi_hendrix on 2009-01-30
heh didnt notice i commented out exit...thanks

---

### Post by NathanB on 2009-01-30
Looks like you are attempting to use 32-bit syscall style in 64-bit mode.  That will not work because 64-bit syscalls have changed both the function constants as well as the parameter-passing conventions.

Annotated:
```

%DEFINE OFFSET 48

// What is the purpose of the OFFSET constant??

[BITS 64]
section .data
    fmt db 'eax=%d',10,0
section .bss
    input resb 10
section .text
extern printf

// Okay, this 'extern' declaration gives us access to the clib function,
but you don't use it in your program because you are making
syscalls instead.  Therefore, you can delete this declaration.
Also, you can link using 'ld' rather than gcc.

global main
    
main:

// The 'main' symbol is only needed when linking against the clib
with gcc -- if you are not using clib (as in this program), then
use the "_start:" symbol because that is what 'ld' will be looking for.

    call debug
    ;push qword 5
    ;push fmt
    ;call debug
    ;call printf
    ;add rsp,8
    ;call exit
print:
    mov rax,4

// Okay, "4" is sys_write only on a 32-bit Kernel.
On a 64-bit Kernel, you will want a "1" here.

    mov rbx,1
    int 80h
    ret    
exit:
    mov rax,1
    mov rbx,0
    int 80h
    ret
read:
    mov rax,3

// Okay, "3" is sys_read only on a 32-bit Kernel.
On a 64-bit Kernel, you will want a "0" here.

    mov rbx,1
    int 80h
    ret
debug:
    push rax
    push rbx
    push rcx
    push rdx
    mov rax,4

// ditto...

    mov rbx,1
    mov rcx,'debuging...\n'
    mov rdx,13
    int 80h
    pop rdx
    pop rcx
    pop rbx
    pop rax
    ret

```

---

### Post by wmcbrine on 2009-01-31
I just want to add that, when speaking of assembly language, the correct term is "assemble" rather than "compile".

---

