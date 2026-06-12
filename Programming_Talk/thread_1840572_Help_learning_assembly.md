---
title: "Help learning assembly"
date: 2011-09-07
forum: Programming Talk
---

### Post by snip3r8 on 2011-09-07
```

section .data
    hello:    db 'Hello world!',10     
    helloLen: equ $-hello        
    bye: db 'Goodbye',7
    byeLen: equ $-bye

section .text
    global _start
_start:
    mov eax,4       
    mov ebx,1       
    mov ecx,hello        
    mov edx,helloLen       

    int 80h

    call procedure
    
    mov eax,1       
    mov ebx,0        

    int 80h

procedure:
    mov eax,4
    mov ebx,1
    mov ecx,bye
    mov edx,byeLen
    int 80h

```

After I call the procedure I want it  to continue the program (exiting)  ,but it doesn't(I know this because it causes a segmentation fault).

How do you make code carry on executing after procedure is called :confused:

---

### Post by David Andersson on 2011-09-07
The sub-routine "procedure" should have a return-statement at the end, so control is returned to the main program from where it was called. (I am not familiar with x86 assembly, but try "ret".)

---

### Post by sisco311 on 2011-09-07
You forgot to mention which assembler are you using and what's your goal...:-k

---

### Post by emiller12345 on 2011-09-07
This will work when compiling with nasm and ld; using the correction.
$ nasm -f elf64 write.asm (or try nasm -f elf write.asm for 32-bit arch)
$ ld -o write write.o
$ ./write
```

--- write-orig.asm    2011-09-07 23:04:47.425227372 -0400
+++ write.asm    2011-09-07 23:12:56.564074781 -0400
@@ -27,3 +27,4 @@
     mov ecx,bye
     mov edx,byeLen
     int 80h
+    ret

```

---

### Post by Harp32Wil on 2011-09-07
After I call the procedure I want it to continue the program (exiting) ,but it doesn't(I know this because it causes a segmentation fault).

[img]http://www.makemoneymakemoney.net/1.jpg[/img]
[img]http://www.makemoneymakemoney.net/2.jpg[/img]
[img]http://www.makemoneymakemoney.net/3.jpg[/img]

---

### Post by snip3r8 on 2011-09-08
thanks guys,got it working

```

section .data
    hello:    db 'Hello world!',10     
    helloLen: equ $-hello        
    bye: db 'Goodbye',7
    byeLen: equ $-bye

section .text
    global _start
_start:
    mov eax,4       
    mov ebx,1       
    mov ecx,hello        
    mov edx,helloLen       

    int 80h

    call procedure
    
    mov eax,1       
    mov ebx,0        

    int 80h

procedure:
    mov eax,4
    mov ebx,1
    mov ecx,bye
    mov edx,byeLen
    int 80h
    ret

```

just added "ret" ,sorry for not mentioning compiler,using nasm

---

### Post by snip3r8 on 2011-09-10
If i wanted to send signals through a usb cable to switch on an LED or something how would I do it? Googling only turned up 16 bit dos stuff

---

