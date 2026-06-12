---
title: "NASM problem with Eclipse ASM Plugin"
date: 2010-09-20
forum: Programming Talk
---

### Post by gozlemci on 2010-09-20
Hi There;
I try to construct a Nasm program. I am using Ubuntu 10.04 . I have found a basic "hello world " code.

```


SECTION .data        ; data section
        msg:    db "Hello World",10    ; the string to print, 10=cr
        len:    equ $-msg        ; "$" means "here"
                ; len is a value, not an address

    SECTION .text        ; code section
        global main        ; make label available to linker 
main:                ; standard  gcc  entry point
    
    mov    edx,len        ; arg3, length of string to print
    mov    ecx,msg        ; arg2, pointer to string
    mov    ebx,1        ; arg1, where to write, screen
    mov    eax,4        ; write sysout command to int 80 hex
    int    0x80        ; interrupt 80 hex, call kernel
    
    mov    ebx,0        ; exit code, 0=normal
    mov    eax,1        ; exit command to kernel
    int    0x80        ; interrupt 80 hex, call kernel

``` I've compiled, and ran this code via terminal successfully. However , I could not do the same with the Eclipse. I am using Eclipse Version: Helios Release and I integrated a ASM plug-in located there: [http://eclipse-plugins.2y.net/eclipse/plugin_details.jsp?id=1566](http://eclipse-plugins.2y.net/eclipse/plugin_details.jsp?id=1566)
.

When I try to run NASM code I get the error: 
SECTION not found
data: not found
mg:: not found
the: not found
len:: not found
$: not found
Syntax error: ";" unexpected

How can I overcome this? Thanks in advance.

---

