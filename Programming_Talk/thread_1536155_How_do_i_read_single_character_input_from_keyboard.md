---
title: "How do i read single character input from keyboard using nasm (assembly) under ubuntu"
date: 2010-07-21
forum: Programming Talk
---

### Post by qteks200 on 2010-07-21
Hi, I'm using nasm under ubuntu. By the way i need to get single input  character from user's keyboard (like when a program ask you for y/n ?)  so as key pressed and without pressing enter i need to read the entered  character. I googled it a lot but all what i found was somehow related  to this line (int 21h) which result in "Segmentation  Fault". Please help me to figure it out how to get single character or  how to over come this segmentation fault.
  Thanks a lot,

---

### Post by rCXer on 2010-07-21
Not sure how to do this under Ubuntu but int 21h is for MS-DOS.  Try looking at int 80h.

---

### Post by jimi_hendrix on 2010-07-21
Using the sys_read system call with stdin as the file descriptor is one way of doing it.  [Here]("http://asm.sourceforge.net//syscall.html#3") is the prototype.

---

### Post by nvteighen on 2010-07-22
This is an example... Of course it's silly to do this kind of stuff in ASM, but well... I've divided it into subroutines using the so-called "C calling convention". For your interest, inputTo is probably what you need.

```

section .data
        prompt db "Yes or no?", 10
        promptLen equ $ - prompt

section .bss
        ;; Using bss to simplify things, but you better use stack locals.

        inputData resb 2       ; 2 bytes... so the newline gets also there

section .text
        global _start           ; Required by ELF

printWhatever:
        ;; ebp + 8: message; ebp + 12: message length.
        
        push ebp
        mov ebp, esp

        mov eax, 4
        mov ebx, 1              ; 1 = stdout
        mov ecx, [ebp + 8]
        mov edx, [ebp + 12]
        int 80h                 ; fire the kernel up.

        pop ebp
        ret

inputTo:
        ;; ebp + 8: place to write; ebp + 12: length

        push ebp
        mov ebp, esp

        mov eax, 3
        mov ebx, 0              ; 0 = stdin
        mov ecx, [ebp + 8]
        mov edx, [ebp + 12]
        int 80h

        pop ebp
        ret
    
_start:
        ;; print the prompt
        push promptLen
        push prompt
        call printWhatever
        add esp, 8

        ;; get the data
        push dword 2
        push inputData
        call inputTo
        add esp, 8

        ;; do something silly
        push dword 2        
        push inputData
        call printWhatever
        add esp, 12
        
        ;; exit
        mov eax, 1
        mov ebx, 0
        int 80h

```

Are you sure C wouldn't be useful? If you see yourself using ASM just to call OS routines (int 80h)... it's quite possible that C makes more sense. ASM should be restricted to devices, bootloaders and stuff where you're implementing the foundations of an OS yourself...

---

