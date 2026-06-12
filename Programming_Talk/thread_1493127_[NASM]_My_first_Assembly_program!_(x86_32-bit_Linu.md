---
title: "[NASM] My first Assembly program! (x86 32-bit Linux)"
date: 2010-05-25
forum: Programming Talk
---

### Post by nvteighen on 2010-05-25
Here's my first Assembly program. A very stupid one but a bit more complex that "Hello world"... I actually don't like Assembly very much, the only reason I went for it was because of curiosity. Also, I wanted to experiment using sys_calls instead of calling libc, so that's why this is using **int 80h** to call the kernel :)

I'm sure this can be corrected and prettified. For example, it'd be great to get rid of the **name** global... So, I'm open to suggestions!

```

;; NASM x86 32-bit Linux Assembly

section .data
        prompt db "Tell me your name!", 10
        promptLength equ $-prompt
        bufStdSize equ 256
        nameReply db "Ah! Your name is:", 10
        nameReplyLength equ $-nameReply
        
section .bss
        name resb bufStdSize

section .text
        global _start

_start:
        call promptForName
        call printName

        jmp exit

printWhatever:
        push ebp
        mov ebp, esp
        
        mov eax, 4
        mov ebx, 1
        mov ecx, [ebp+8]
        mov edx, [ebp+12]
        int 80h

        pop ebp
        ret
        
promptForName:
        push ebp
        mov ebp, esp
        
        push dword promptLength
        push dword prompt
        call printWhatever
        add esp, 8

        push dword name
        call getName
        add esp, 4

        pop ebp
        ret

getName:
        push ebp
        mov ebp, esp
        
        mov eax, 3
        mov ebx, 0
        mov ecx, [ebp+8]
        mov edx, bufStdSize
        int 80h
        
        pop ebp
        ret

printName:
        push ebp
        mov ebp, esp

        push dword nameReplyLength
        push dword nameReply
        call printWhatever
        add esp, 8
        
        push dword bufStdSize
        push dword name
        call printWhatever
        add esp, 8

        pop ebp
        ret
        
exit:
        mov eax, 1
        mov ebx, 0
        int 80h

```

---

