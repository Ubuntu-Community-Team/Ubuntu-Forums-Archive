---
title: "Segfault in NASM program."
date: 2011-10-17
forum: Programming Talk
---

### Post by cgroza on 2011-10-17
Hello everyone. I am learning NASM so I challenged myself to write a program that print the first letter of the command line arguments.

So far, if I provide arguments, it prints the first letter of the first argument and then segfaults.
If I provide none, it does nothing.

So what is wrong with this code? Am I missing something?
```
section .text
    global _start
_start:
    pop esi            ;get number of args
    pop eax            ;remove the program name from the stack
    dec esi            ;decrement nr of args (we no longer have the progam name)

    jmp printArgs        ;start printing args
    
exit:                ;exit label
    mov eax,1        ;move exit in eax
    mov ebx,0        ;move return code 
    int 80h            ;kernel interrupt
    
printArgs:
    cmp esi, 0        ;compare esi and 0
    ja printNextArg        ;if esi above, jump printNextArg
    jmp exit        ;if not, jump exit
    
    
printNextArg:            ;printNextArg label
    jmp printArg        ;printArg
    dec esi            ;decrement esi
    jmp printArgs        ;loop
    
printArg:            ;printArg label
     mov eax, 4        ;move print in eax
     mov ebx, 1        ;move stdout in ebx
     pop ecx            ;move next argument on stack in ecx
     mov edx, 1        ;move string length
     int 80h            ;kernel interrupt

```

---

### Post by emiller12345 on 2011-10-17
> **cgroza said:**
> 
So what is wrong with this code? Am I missing something?
```
printArg:            ;printArg label
     mov eax, 4        ;move print in eax
     mov ebx, 1        ;move stdout in ebx
     pop ecx            ;move next argument on stack in ecx
     mov edx, 1        ;move string length
     int 80h            ;kernel interrupt

```

when you exec 'printArg', you don't automatically return from the function. try adding 'ret' to the end

And your only writing 1 Char to stdout with 'mov edx, 1'

---

### Post by lisati on 2011-10-17
"ret" works best if you've used something like "call" that pushes a return address on the stack. If I've understood the code properly, a little bit of rearranging as follows might work better:

```
printNextArg:            ;printNextArg label
  [s]jmp printArg        ;printArg
    dec esi            ;decrement esi
    jmp printArgs        ;loop
   [/s]
printArg:            ;printArg label
     mov eax, 4        ;move print in eax
     mov ebx, 1        ;move stdout in ebx
     pop ecx            ;move next argument on stack in ecx
     mov edx, 1        ;move string length
     int 80h            ;kernel interrupt

     dec esi            ;decrement esi
    jmp printArgs        ;loop

```

---

### Post by cgroza on 2011-10-17
Still getting the same result. I tried calling it instead of jumping into printArg, it just displayed an N and then segfaulted.

Here is the new printArg:
```
printArg:                       ;printArg label
        mov eax, 4              ;move print in eax
        mov ebx, 1              ;move stdout in ebx
        pop ecx                 ;move next argument on stack in ecx
        mov edx, 1              ;move string length
        int 80h                 ;kernel interrupt
        ret

```

---

### Post by cgroza on 2011-10-17
Thanks Lisati, your solution worked, although I still do not understand what was wrong and what is right now.
Here is the new full code:

```
section .text
        global _start
_start:
        pop esi                 ;get number of args
        pop eax                 ;remove the program name from the stack
        dec esi                 ;decrement nr of args (we no longer have the progam name)

        jmp printArgs           ;start printing args
        
exit:                           ;exit label
        mov eax,1               ;move exit in eax
        mov ebx,0               ;move return code 
        int 80h                 ;kernel interrupt
        
printArgs:
        cmp esi, 0              ;compare esi and 0
        ja printArg             ;if esi above, jump printNextArg
        jmp exit                ;if not, jump exit
        
printArg:            ;printArg label
     mov eax, 4        ;move print in eax
     mov ebx, 1        ;move stdout in ebx
     pop ecx            ;move next argument on stack in ecx
     mov edx, 1        ;move string length
     int 80h            ;kernel interrupt

     dec esi            ;decrement esi
     jmp printArgs        ;loop


```

---

