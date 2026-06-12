---
title: "Trying to learn assembly"
date: 2009-09-12
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-09-12
So I've tried Assembly for time now, and has just been way over my head, until I starting learning more about C, C++, and computer architecture, it is not starting to click.  How ever, I'm still having a bit of hard time.  I finally found a good online tutorial & I understand all of the programs that I've gotten to so far.  As every one knows, the best way to do it yourself (it's no help just to copy an example, compile link and run it), so I made a variation on the infamous hello world program, called hello.asm  I decided to make it print out another string, but it wont print out the full string!  Here is what I got:
```

section data:
    hello:        db 'Hello World!',10
    helloLen:   equ $-hello
    myStr:        db 'This is my string',14   ;not sure if it should be 14


section text:
    global _start

_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, hello
    mov edx, helloLen
    
    int 80h

    mov eax, 4
    mov ebx, 1
    mov ecx, myStr

    int 80h

    ;quit the program

    mov eax, 1
    mov ebx, 0
    int 80h

```

Pretty simple right?  Although the output is this:
```

Hello World!
This is my st

```

How come it wont print the full world "string"?  Any other flaws with my program any one could help me with?

Thank you for your time.

---

### Post by Can+~ on 2009-09-13
The number after the string is a concatenation:

[http://www.et.byu.edu/groups/ece425web/stable/labs/NASM.html](http://www.et.byu.edu/groups/ece425web/stable/labs/NASM.html)

```
db 'Hello World!',10
```

So that "10" indicates newline, but there's no 0 (NULL terminator).

Same goes for your other line.

---

### Post by falconindy on 2009-09-13
In section data where you make your declarations, the number after a string is a value in hex. In this case, 10 is a newline character. 

You also need to create a second declaration for the length of myStr -- follow the naming convention and call it myStrLen. In assembly, strings are passed by reference. You need the length of the string so the assembler knows how far it needs to read past the base address.

I'm really having a lot of fun with assembly. I only started looking at it recently as well.

---

### Post by Can+~ on 2009-09-13
It took me a while to get it, I never learnt [FONT="Courier New"]nasm[/FONT], I actually learnt MIPS assembly, because it was easier to execute and debug in the MIPS emulator (SPIM).

If you want to check out MIPS, it's on the repository.

---

### Post by c0mput3r_n3rD on 2009-09-13
```

section data:
    hello:        db 'Hello World!',10
    helloLen:   equ $-hello
    myStr:        db 'This is my string',10
    myStrLen:   equ $-myStr


section text:
    global _start

_start:
    mov eax, 4
    mov ebx, 1
    mov ecx, hello
    mov edx, helloLen
    
    int 80h

    mov eax, 4
    mov ebx, 1
    mov ecx, myStr
    mov edx, myStrLen

    int 80h
    
    mov eax, 1
    mov ebx, 0
    int 80h

```Got it! Thank you guys, knowing that the 10 after the string is a new line character made all the difference.

Thanks again for all the help!

EDIT: That's why it's so hard to find good tutorials online, they don't explain EVERYTHING, which is really needed to be able to program.  All of those, "Just copy, paste, and look", or learn "[insert language here] in 24 hours" suck.  Good thing I have all of you though ;)

---

### Post by lisati on 2009-09-13
> **falconindy said:**
> You need the length of the string so the assembler knows how far it needs to read past the base address.
Minor niggle: AFAIK, it's not the assembler that will need to figure out or be told the length of the string, but the system call that actually outputs the string that will need to know when to stop. The assembler should be able to work it out for itself by using what's between the quotes.

---

### Post by falconindy on 2009-09-13
> **lisati said:**
> Minor niggle: AFAIK, it's not the assembler that will need to figure out or be told the length of the string, but the system call that actually outputs the string that will need to know when to stop. The assembler should be able to work it out for itself by using what's between the quotes.
That actually makes a surprising amount of sense.

---

### Post by c0mput3r_n3rD on 2009-09-13
> **lisati said:**
> Minor niggle: AFAIK, it's not the assembler that will need to figure out or be told the length of the string, but the system call that actually outputs the string that will need to know when to stop. The assembler should be able to work it out for itself by using what's between the quotes.


That's why the number after the string was confusing me, I thought it needed the length of the string.  But then after looking over the code again, I saw the "helloLen:  equ $-hello", and realized that THAT was what told the processor how many bytes to print.

---

### Post by wmcbrine on 2009-09-13
> **falconindy said:**
> In section data where you make your declarations, the number after a string is a value in hex. In this case, 10 is a newline character.Not in hex -- in decimal. Newline is 10 decimal, 0A hex.

---

### Post by c0mput3r_n3rD on 2009-09-14
> **wmcbrine said:**
> Not in hex -- in decimal. Newline is 10 decimal, 0A hex.

Right, because DOS uses hexadecimal and you must use 0A as the new line.

---

### Post by glickboy on 2009-09-19
Google for the free online book "Programming from the Ground Up"  Its a great intro/tutorial on Assembly.

---

