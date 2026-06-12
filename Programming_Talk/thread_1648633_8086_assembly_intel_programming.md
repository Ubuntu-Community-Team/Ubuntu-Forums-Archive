---
title: "8086 assembly intel programming"
date: 2010-12-19
forum: Programming Talk
---

### Post by yuiop on 2010-12-19
Hi

So i have a work to do in this language, assembly, intel type. I'm using CAS, gcc and i have to use ncurses too.

I've been searching for info about this language, because we are supposed to learn it at our own...
Anyway i've found few things of what i wanted to find. It seems there are a lot of different ways to write in assebmly language. What i'm seeking is something that is done in the ubunto, assembly for 8086, intel type.

I need to know a place where i can find examples of simple programs in this language. Programs about reading from input, comparing numbers and caracters and do simple aritmethic operations, printing it back in a output file. This because the program i must do is one that gets the min terms from a karnaugh map. I need to analyse a input file, with the entries of the karnaugh map and then get the min terms..

Btw, here is a program that i've been trying to make, but something is failing. I cant link it right when i type " ld -o file file.o". I should be using the cmp instruction wrong in the code

The program is expected to ask the user to insert the "f" character, read the input that is given by the user and recognise if it is or it is not the "f" character. 

Here it is:

.intel_syntax noprefix

.data

fstring:    .ascii  "Insert F:\n"
        len1 = . - fstring

sstring:    .ascii  "Success!\n"
        len2 = . - sstring

tstring:        .ascii "Fail!!\n"
        len3 = . - tstring

str:    .space 10, 0



.text

    .global _start

_start:

# stack initialization
    # sp points to the last used position
    # and decreses with each push



    mov edx, len1            #First string imprinted
    mov ecx, offset fstring
    mov ebx, 1
    mov eax, 4
    int 0x80



    mov edx, 1            #Reads the output
    mov ecx, offset str
    mov ebx, 1
    mov eax, 3
    int 0x80


    
        cmp ecx, f
        jne wrong

        mov edx, len2            #Recognizes F
        mov ecx, offset sstring        #
        mov ebx, 1
        mov eax, 4
        int 0x80

        jmp end

wrong:
    
    mov edx, len3            #Wrong character
    mov ecx, offset tstring
    mov ebx, 1
    mov eax, 4
    int 0x80

    jmp end

end:

    mov    ebx, 0       #first syscall argument: exit code
        mov     eax, 1     #system call number (sys_exit)
        int     0x80       #call kernel

---

### Post by Npl on 2010-12-19
My guess is that you need to do something like
cmp ecx, 'f'

or use the ascii code directly

cmp ecx, 66

and regarding asm and linux in general:[Click here]("http://lmgtfy.com/?q=asm+linux")

---

### Post by nvteighen on 2010-12-19
There are some issues here.

0) Use [noparse]```

```[/noparse] tags to post code.

1) I hope you understand ASM is highly platform-dependent, so that well... if your course is using Windows, your program won't run as "int 80h" interfaces to the Linux kernel. Windows ASM programming takes a radically different approach to system calls.

2) You're using GAS's Intel syntax, but GAS's "native" syntax is actually AT&T. Usually, people relate Intel syntax to the MS Assembler (MASM), which is Windows-specific, or to NASM, which is cross-platform and FOSS. Ask your teacher what particular implementation he wants you to use if there is one in particular, as you may fail your assignment because of using something his assembler won't recognize. 

NASM is available at the repos, if you happen to need it. It works perfectly, but doesn't have automagical gcc support... so, if you want to link code assembled by NASM with C code compiled by gcc (assembled by GAS), you'll have to do it manually.

3) Now, if you know C, you'll probably know that stdin is line-buffered and that the string you actually get as input also includes the '\n' you insert when hitting enter. This is the reason why your program will always show "fail" even if 'f' is input by the user, because it's doing the comparison wrong... I leave it to you to implement the solution.

---

