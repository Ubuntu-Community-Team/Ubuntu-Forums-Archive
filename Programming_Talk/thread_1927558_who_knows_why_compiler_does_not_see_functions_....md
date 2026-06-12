---
title: "who knows why compiler does not see functions ..."
date: 2012-02-18
forum: Programming Talk
---

### Post by topscore on 2012-02-18
;declared in extern directive
 
 global main
 main:
  extern XOpenDisplay
  extern XDefaultScreen
  extern XRootWindow
  extern XCreateSimpleWindow
  extern XMapWindow
  extern XFlush
  extern XCloseDisplay

 section .data
   schirm dd 0
     film dd 0
  fenster dd 0
 ereignis: times 96 db 0
     GK   dd 0

 section .text     
    mov rdi, 0
   call XOpenDisplay
    mov [schirm], rax
    mov rdi, rax
   call XDefaultScreen
    mov [film], rax
    mov  rdi, [schirm]
    mov  rsi, [film]
   call XRootWindow
    mov rdi, [schirm]
    mov rsi, [rax]
    mov rdx, 60
    mov rcx, 100
    mov  r8, 600 
    mov  r9, 300
    push 0x009900
    push 10
    push 10
   call XCreateSimpleWindow
    add rsp, 8
    mov [fenster], rax
    mov rdi, [schirm]
    mov rsi, [fenster]
   call XMapWindow
    mov rdi, [schirm]
   call XFlush     

 zyklus: 
   mov r10, 1000
    dec r10
    cmp r10, 0
  jne zyklus   

   mov rdi, [schirm]
   call XCloseDisplay
   mov rax, 60
   xor rdi, rdi
  syscall

 the code above is compiled well

---

### Post by Zugzwang on 2012-02-18
To get meaningful answers, I would suggest that you do the following:
[LIST=1]
[*]Post a complete source code that witnesses the problem. Make sure that it is in some sense a minimal example.
[*]Copy&Paste the commands you are using for compilation
[*]Copy&Paste the *precise* error messages.
[/LIST]

---

### Post by r-senior on 2012-02-18
4. Remember to use code tags

---

### Post by Zugzwang on 2012-02-18
@OP: The code you pasted doesn't seem to capture your problem.

```

me@here:/tmp$ cat test.asm 
global main

extern XopenDisplay
extern XDefaultScreen
extern XRootWindow

.data
dd schirm 0
dd film 0
dd fenster

.text
push rdi, 0
call XopenDisplay
mov [schirm], rax
me@here:/tmp$ nasm test.asm 
test.asm:7: error: attempt to define a local label before any non-local labels
test.asm:8: error: comma expected after operand 1
test.asm:9: error: comma expected after operand 1
test.asm:12: error: attempt to define a local label before any non-local labels

```

Please provide a snippet that witnesses your actual problem.

---

### Post by Zugzwang on 2012-02-18
@OP: You will need to answer question no. 2 from my previous post to get a useable answer. Your code still doesn't compile for me with errors that are different to yours.

```

test.asm:17: error: instruction not supported in 16-bit mode
test.asm:18: error: binary output format does not support external references
test.asm:19: error: instruction not supported in 16-bit mode

```

Note that modifying your original post all the time will confuse new readers of this thread, essentially preventing them from giving answers to your problem.

---

### Post by Zugzwang on 2012-02-18
> **Zugzwang said:**
> 
Note that modifying your original post all the time will confuse new readers of this thread, essentially preventing them from giving answers to your problem.

Looks like you did it again. It is still unclear what command you are using when compiling your code. Just running "nasm test.asm" gives me:
```

test.asm:19: error: instruction not supported in 16-bit mode
test.asm:20: error: binary output format does not support external references
test.asm:21: error: instruction not supported in 16-bit mode
test.asm:22: error: instruction not supported in 16-bit mode
test.asm:23: error: binary output format does not support external references
test.asm:24: error: instruction not supported in 16-bit mode
test.asm:25: error: instruction not supported in 16-bit mode
test.asm:26: error: instruction not supported in 16-bit mode
test.asm:27: error: binary output format does not support external references
test.asm:28: error: instruction not supported in 16-bit mode
test.asm:29: error: instruction not supported in 16-bit mode
test.asm:30: error: instruction not supported in 16-bit mode
test.asm:31: error: instruction not supported in 16-bit mode
test.asm:32: error: instruction not supported in 16-bit mode
test.asm:33: error: instruction not supported in 16-bit mode
test.asm:37: error: binary output format does not support external references
test.asm:38: error: instruction not supported in 16-bit mode
test.asm:39: error: instruction not supported in 16-bit mode
test.asm:40: error: instruction not supported in 16-bit mode
test.asm:41: error: instruction not supported in 16-bit mode
test.asm:42: error: binary output format does not support external references
test.asm:43: error: instruction not supported in 16-bit mode
test.asm:44: error: binary output format does not support external references
test.asm:47: error: instruction not supported in 16-bit mode
test.asm:48: error: instruction not supported in 16-bit mode
test.asm:49: error: instruction not supported in 16-bit mode
test.asm:52: error: instruction not supported in 16-bit mode
test.asm:53: error: binary output format does not support external references
test.asm:54: error: instruction not supported in 16-bit mode
test.asm:55: error: instruction not supported in 16-bit mode

```

---

### Post by Zugzwang on 2012-02-18
@OP: You just changed the last line of your code to 
"the code above is compiled well" - what are you trying to tell us here? That your problem has been solved by yourself in the meantime.

---

### Post by topscore on 2012-02-18
now i want to know if it works on other computers


andre@andrePC:~$ nasm -f elf64 /home/andre/fishki.asm  -o /home/andre/fishki.o

andre@andrePC:~$ gcc -Wl,-s fishki.o -lX11 -L/usr/X11R6/lib -o fishki

./fishki

the window appears but don't close after the loop 
probably in r10 register the value is not 1000 but much more

---

### Post by Zugzwang on 2012-02-18
> **topscore said:**
> now i want to know if it works on other computers


What does "it" mean here? Compilation&Linking or executing the program?

The compilation&Linking process will work on all x64 Linux computers that have gcc&nasm and the development version of the library installed.

The executable you created works on all x64 Linux computers that use the same version of libX11 as you. In order to make running the executable independent from the X11 version, add the "-static" flag to your linking command (in front, afaik). Note that the executable gets much bigger this way.

> **topscore said:**
> 
probably in r10 register the value is not 1000 but much more

I would advise you to use your favourite debugger to find out if this is really the problem.

---

