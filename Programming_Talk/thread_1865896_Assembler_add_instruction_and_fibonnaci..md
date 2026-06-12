---
title: "Assembler: add instruction and fibonnaci."
date: 2011-10-20
forum: Programming Talk
---

### Post by cgroza on 2011-10-20
Hello everyone. 
I am learning nasm and I have a question.
I have this following code:
```
section .text
    global _start

_start:
    mov ecx, 0        ;will keep the before last fibonnaci number
    mov edx, 1        ;will keep the last fibonnaci number
    mov eax, 0        ;will keep a fibonnaci index counter
    
    jmp fibonaci        ;start fibonnaci

exit:
    mov eax, 1
    mov ebx, edx
    int 80h

fibonaci:
    cmp eax, 5         ;have we reached the max counter?
    jle nexfib             ;no? go again
    jmp exit               ;yes? output and exit

nexfib:
    inc eax            ;increment counter
    inc eax
    add edx, ecx        ;add last fib with before last fib
    add ecx, edx        ;add before last fib with last fib. before last fib changes value
    push edx
    push ecx
    jmp fibonaci        ;loop

```
This code calculates the nth fibonnaci number (hard coded into the progam).
It outputs the right answer as long as the fibonnaci number is equal or lower than 233, otherwise I think it overflows.
This is pretty close to 255, which is the maximum value that can be stored in 8 bits.
But as far as I know, eax ... edx are 32 bit registers. So why is my output messed up when I do this?
I could also reproduce this problem outside my fibonnaci program.

So is there something I am unaware of?

---

### Post by lisati on 2011-10-20
I notice that you're pushing ecx and edx onto the stack. Perhaps I'm missing something - the last lot of asm coding I did was for a 16-bit MS-DOS program - but where are they being popped off the stack?

---

### Post by Bachstelze on 2011-10-20
> **cgroza said:**
> 
So is there something I am unaware of?

Yup. ;)

[http://pubs.opengroup.org/onlinepubs/9699919799/functions/exit.html](http://pubs.opengroup.org/onlinepubs/9699919799/functions/exit.html)

> The value of status may be 0, EXIT_SUCCESS, EXIT_FAILURE, or any other value, **though only the least significant 8 bits (that is, status & 0377) shall be available to a waiting parent process.**

*EDIT:* And yes, why are you pushing everything onto the stack?

---

### Post by cgroza on 2011-10-20
Oh, so my calculations are right, it's the exit call that messes up my result.
Thanks! :D

---

### Post by cgroza on 2011-10-20
> **lisati said:**
> I notice that you're pushing ecx and edx onto the stack. Perhaps I'm missing something - the last lot of asm coding I did was for a 16-bit MS-DOS program - but where are they being popped off the stack?
I was pushing them on the stack because I was thinking to make the program print all the fibonnaci numbers up until that index. And since I needed a place to store them, the stack seemed a good place to do it in.

But to do that, I still need to learn how to convert those numbers to strings.

---

