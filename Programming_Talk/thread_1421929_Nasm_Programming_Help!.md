---
title: "Nasm Programming Help!"
date: 2010-03-04
forum: Programming Talk
---

### Post by manyu29 on 2010-03-04
This program asks for a string of 5 characters and see if it contains any special characters and prints out if it does and if it doesnt. Plz tel me wats wrong with my code because it seems to only read and compare the fifth character.

section .data
    m1: db "Enter a String: ", 0
    m1len: equ $ - m1
    m2: db "The following string does not contain any special characters.", 0
    m2len: equ $ - m2
    m3: db "The following contain(s) (a) special character(s).", 0
    m3len: equ $ - m3section .data

section .bss
    string: resb 5

section .text
    global _start
_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, m1
    mov edx, m1len
    int 80h

    mov eax, 3
    mov ebx, 0
    mov ecx, string
    mov edx, 5
    int 80h

    mov ecx, 5       
    mov ebx, string

next:
    mov eax, [ebx]
    cmp eax, 0x41
    jb special
    cmp eax, 0x5a
    jbe nextletter
    cmp eax, 0x61
    jb special
    cmp eax, 0x7a
    jbe nextletter

nextletter:
    inc ebx
    loop next
    jmp nosp

nosp:
    mov eax, 4
    mov ebx, 1
    mov ecx, m2
    mov edx, m2len
    int 80h
    jmp exit

special:
    mov eax, 4
    mov ebx, 1
    mov ecx, m3
    mov edx, m3len
    int 80h
    jmp exit

exit:
    mov eax, 1
    mov ebx, 0
    int 80h

---

### Post by Zugzwang on 2010-03-05
What do you observe when running this code in a debugger step-by-step?

---

