---
title: "Oh great programmers, heed my call.."
date: 2010-03-18
forum: Programming Talk
---

### Post by manyu29 on 2010-03-18
i have been trying to write a program which tells if a given string is a palindrome or not. As you can see its nasm. The code below is what i have written so far. The string input is fixed. 
* Can anybody teach me how to write a code which reads the inputted string and tell how many chars there is and put it as the counter for the loop?
*Another thing is that, does anybody know how to put together an inputted string such that when i put in ABCDE, it will duplicate and add it to itself like this ABCDEABCDE?
i would appreciate concepts but i would appreciate it more if you will teach me the actual codes.
*if its not too much, please teach me the code that reverses text inputted.
here is my proto program for the palindrome to prove that im not asking for a free program. Improvements will be made given that you give me the answers to my questions. Please leave me reply. thank you very much.


section .data
    string: db "abccba", 10
    
    m2: db "It is a palindrome!", 10
    m2len: equ $ - m2
    m3: db "It is not a palindrome!", 10
    m3len: equ $ - m3
    
section .text
    global _start
_start:    
    mov ecx, 6    
    mov esi, string
    mov edi, string
    inc edi
    inc edi
    inc edi
    inc edi
    inc edi
check:
    mov al, [esi]
    mov ah, [edi]
    cmp al, ah
    je check1
    
    jne notpal

check1:
    inc esi
    dec edi
    loop check
    jmp pal

pal:
    mov eax, 4
    mov ebx, 1
    mov ecx, m2

    mov edx, m2len
    int 80h
    jmp exit

notpal:
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

### Post by Can+~ on 2010-03-18
Why does it sound like homework?

---

### Post by manyu29 on 2010-03-18
nope..its a bet..

---

### Post by lisati on 2010-03-18
Hint #1: What is a palindrome? 
Hint #2: How would you check it yourself?
Hint #3: There's a quicker way of pointing at the end of the string.....

---

### Post by manyu29 on 2010-03-18
how do i point to the end of the string?

---

### Post by falconindy on 2010-03-18
> **manyu29 said:**
> how do i point to the end of the string?
You know the address at which the string starts, and you how long it is...

---

### Post by Can+~ on 2010-03-18
> **falconindy said:**
> You know the address at which the string starts, and you how long it is...

And there's a reason most assembly versions have it in a "base+offset" notation (MIPS was like "offset(base)" if my memory serves me well).

---

### Post by soltanis on 2010-03-19
This bet sounds strangely like homework.

---

### Post by Some Penguin on 2010-03-19
And, in fact, the same poster already asked people to simply "give him the code" for this very same problem a few days ago.

"Could anybody give me a palindrome code written in nasm?plzzzzzzz do  help me!i am so in trouble!"
[http://ubuntuforums.org/showthread.php?t=1429372](http://ubuntuforums.org/showthread.php?t=1429372)

---

### Post by cariboo on 2010-03-19
Homework again? Closed.

---

