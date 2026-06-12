---
title: "Calculator in Assembly Language - Linux x86 &amp; NASM"
date: 2012-02-24
forum: Programming Talk
---

### Post by nicoobe on 2012-02-24
Hello,
My name is Nicholas and I am making a calculator in assembly language to be executed on an x86 processor.

Basically,  my calculator asks the user to enter two numbers and then to indicate  which operation (addition, subtraction, multiplication and division)  want to do with them.

My calculator adds, subtracts and  multiplies correctly but is unable to divide. In making a division, I  always get 1 as the result.

Then I leave my application code complete:
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

```The error must be found inside the tag "divide".

I hope that someone on the forum with more experience can help me with this.  [IMG]http://forum.nasm.us/Smileys/default/smiley.gif[/IMG]
Thanks you

---

### Post by alegomaster on 2012-02-24
I might be able to help you though it might take time. I didn't work with x86 assembly for a while (I am mostly doing risc assembly right now), but I might find the issue.

Edit: I need KDE!!!! I decided to install kubuntu onto virtual, so I am waiting for the download to finish and once it is done, I will start testing your code

Edit: what assembler are you using

---

### Post by alegomaster on 2012-02-26
Your code seems to be great so I am not sure what is wrong with it. You seemed to follow proper conventions when multiplying so I am unable to figure it out (I use GAS so I am not familiar with NASM). I will try to forward this to some people who have more experience with x86 assembly so that they can help you.

---

### Post by alegomaster on 2012-02-26
So after going on IRC and consulting with Jester01 who decided to make me figure it out, I finally got the answer. Here it is:
```

divide:
    ; IN THIS LABEL IS THE ERROR!
    
    ; We store the numbers in registers ax and bx
    mov dx, 0
    mov ax, [num1]
    mov bx, [num2]

    sub ax, 0xa00 ;New line HERE
    sub bx, 0xa00

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

```

The issue was that the system calls to record the text was also picking up the newline, so if you subtract 0xa00 from ax, then your problem is solved. Please mark the thread solved if you are finished or you can ask another question.

---

### Post by nicoobe on 2012-02-26
Thank you very much. My calculator finally works.

Here is my final code:

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

    opc:        resb     2
    num1:        resb    2
    num2:        resb     2
    result:        resb     2

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

    mov ah, [opc]        ; Move the selected option to the registry ah
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
    ; We keep the numbers in the registers al and bl
    mov al, [num1]
    mov bl, [num2]

    ; Convert from ascii to decimal
    sub al, '0'
    sub bl, '0'

    ; Add
    add al, bl

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
    mov edx, 2
    int 80h

    ; We end the program
    jmp exit

subtract:
    ; We keep the numbers in the registers al and bl
    mov al, [num1]
    mov bl, [num2]

    ; Convert from ascii to decimal
    sub al, '0'
    sub bl, '0'

    ; Subtract
    sub al, bl

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

multiply:

    ; We store the numbers in registers al and bl
    mov al, [num1]
    mov bl, [num2]

    ; Convert from ascii to decimal
    sub al, '0'
    sub bl, '0'

    ; Multiply. AX = AL x BL
    mul bl

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
    mov eax, 4
    mov ebx, 1
    mov ecx, result
    mov edx, 1
    int 80h

    ; We end the program
    jmp exit

divide:

    ; We store the numbers in registers ax and bx
    mov al, [num1]
    mov bl, [num2]

    mov dx, 0
    mov ah, 0

    ; Convert from ascii to decimall
    sub al, '0'
    sub bl, '0'

    ; Division. AL = AX / BX
    div bl

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

