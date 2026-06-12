---
title: "What assembler is this for"
date: 2012-02-24
forum: Programming Talk
---

### Post by alegomaster on 2012-02-24
Title says all.  Can someone tell me what assembler to use for this code.
```

section .data

    ; Messages

    msg1        db        10,'-Calculator-',10,0
    lmsg1        equ        $ - msg1

    msg2        db        10,'Number 1: ',0
    lmsg2        equ        $ - msg2

    msg3        db        'Number 2: ',0
    lmsg3        equ        $ - msg3

    msg4        db        10,'1. Add',10,0
    lmsg4        equ        $ - msg4

    msg5        db        '2. Subtract',10,0
    lmsg5        equ        $ - msg5

    msg6        db        '3. Multiply',10,0
    lmsg6        equ        $ - msg6

    msg7        db        '4. Divide',10,0
    lmsg7        equ        $ - msg7

    msg8        db        'Operation: ',0
    lmsg8        equ        $ - msg8

    msg9        db        10,'Result: ',0
    lmsg9        equ        $ - msg9

    msg10        db        10,'Invalid Option',10,0
    lmsg10        equ        $ - msg10

    nlinea        db        10,10,0
    lnlinea        equ        $ - nlinea

section .bss
    
    ; Spaces reserved for storing the values &#8203;&#8203;provided by the user.

    opc            resb     2
    num1        resb    2
    num2        resb     2
    result        resb     2

section .text

    global _start

_start:

    ; Print on screen the message 1
    mov eax, 4
    mov ebx, 1
    mov ecx, msg1
    mov edx, lmsg1
    int 80h

    ; Print on screen the message 2
    mov eax, 4
    mov ebx, 1
    mov ecx, msg2
    mov edx, lmsg2
    int 80h

    ; We get num1 value.
    mov eax, 3
    mov ebx, 0
    mov ecx, num1
    mov edx, 2
    int 80h

    ; Print on screen the message 3
    mov eax, 4
    mov ebx, 1
    mov ecx, msg3
    mov edx, lmsg3
    int 80h

    ; We get num2 value.
    mov eax, 3
    mov ebx, 0
    mov ecx, num2
    mov edx, 2
    int 80h

    ; Print on screen the message 4
    mov eax, 4
    mov ebx, 1
    mov ecx, msg4
    mov edx, lmsg4
    int 80h

    ; Print on screen the message 5
    mov eax, 4
    mov ebx, 1
    mov ecx, msg5
    mov edx, lmsg5
    int 80h

    ; Print on screen the message 6
    mov eax, 4
    mov ebx, 1
    mov ecx, msg6
    mov edx, lmsg6
    int 80h

    ; Print on screen the message 7
    mov eax, 4
    mov ebx, 1
    mov ecx, msg7
    mov edx, lmsg7
    int 80h

    ; Print on screen the message 8
    mov eax, 4
    mov ebx, 1
    mov ecx, msg8
    mov edx, lmsg8
    int 80h

    ; We get the option selected.
    mov ebx,0
    mov ecx,opc
    mov edx,2
    mov eax,3
    int 80h

    mov ah, [opc]    ; Move the selected option to the registry ah
    sub ah, '0'        ; Convert from ascii to decimal

    ; We compare the value entered by the user to know what operation to perform.

    cmp ah, 1
    je add
    cmp ah, 2
    je subtract
    cmp ah, 3
    je multiply
    cmp ah, 4
    je divide

    ; If the value entered by the user does not meet any of the above 
    ; conditions then we show an error message and we close the program.
    mov eax, 4
    mov ebx, 1
    mov ecx, msg10
    mov edx, lmsg10
    int 80h

    jmp exit

add:
    ; We keep the numbers in the registers eax and ebx
    mov eax, [num1]
    mov ebx, [num2]

    ; Convert from ascii to decimal
    sub eax, '0'
    sub ebx, '0'

    ; Add
    add eax, ebx

    ; Conversion from decimal to ascii
    add eax, '0'

    ; We move the result
    mov [result], eax

    ; Print on screen the message 9
    mov eax, 4
    mov ebx, 1
    mov ecx, msg9
    mov edx, lmsg9
    int 80h

    ; Print on screen the result
    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 1
    int 80h

    ; We end the program
    jmp exit

subtract:
    ; We keep the numbers in the registers eax and ebx
    mov eax, [num1]
    mov ebx, [num2]

    ; Convert from ascii to decimal
    sub eax, '0'
    sub ebx, '0'

    ; Subtract
    sub eax, ebx

    ; Conversion from decimal to ascii
    add eax, '0'

    ; We move the result
    mov [result], eax

    ; Print on screen the message 9
    mov eax, 4
    mov ebx, 1
    mov ecx, msg9
    mov edx, lmsg9
    int 80h

    ; Print on screen the result
    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 1
    int 80h

    ; We end the program
    jmp exit

multiply:
    
    ; We store the numbers in registers ax and bx
    mov ax, [num1]
    mov bx, [num2]

    ; Convert from ascii to decimal
    sub ax, '0'
    sub bx, '0'

    ; Multiply. AL = AX x BX
    mul bx

    ; Conversion from decimal to ascii
    add al, '0'

    ; We move the result
    mov [result], al

    ; Print on screen the message 9
    mov eax, 4
    mov ebx, 1
    mov ecx, msg9
    mov edx, lmsg9
    int 80h

    ; Print on screen the result
    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 1
    int 80h

    ; We end the program
    jmp exit

divide:
    ; IN THIS LABEL IS THE ERROR!
    
    ; We store the numbers in registers ax and bx
    mov dx, 0
    mov ax, [num1]
    mov bx, [num2]

    ; Convert from ascii to decimall
    sub ax, '0'
    sub bx, '0'
    ; Division. AX = DX:AX / BX
    div bx

    ; Conversion from decimal to ascii
    add ax, '0'
    ; We move the result
    mov [result], ax

    ; Print on screen the message 9
    mov eax, 4
    mov ebx, 1
    mov ecx, msg9
    mov edx, lmsg9
    int 80h

    ; Print on screen the result
    ; ALWAYS PRINTS 1
    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 1
    int 80h

    ; We end the program
    jmp exit
    
exit:
    ; Print on screen two new lines
    mov eax, 4
    mov ebx, 1
    mov ecx, nlinea
    mov edx, lnlinea
    int 80h
    ; End the program
    mov eax, 1
    mov ebx, 0
    int 80h

```

---

### Post by cgroza on 2012-02-24
It looks very similar to the little NASM I have played with in the past.

You can download it from the repos.

---

### Post by alegomaster on 2012-02-24
Thanks. It is NASM

---

