---
title: "compile assembly code"
date: 2010-07-31
forum: Packaging and Compiling Programs
---

### Post by pooya_mr2009 on 2010-07-31
hi every body.
i want to compile the assembly code but i don't know any compiler for linux and i don't know how can i use it
please introduce me the good assembly compiler and describe how can i use it.
tnx a lot

---

### Post by SevenMachines on 2010-07-31
There are a lot of different assemblers available on linux but two, 'as' and 'nasm' are the ones you'll hear about by far the most. Which one you use will depend on which assembly syntax you use...

1) Nasm - Intel Syntax 
    Intel is the one you'll see most of, since its used on windows and linux it's the one i'd recommend for learning (if thats what you're doing), theres a few simple rules to change code between at&t and intel and once you know one it should only take a short time to be able to program just as easily in either one. There a description of the main differences in syntax [here]("http://asm.sourceforge.net/articles/linasm.html#Syntax").

$ sudo apt-get install nasm

hello.asm:
```

section .text               ;section declaration

            ;we must export the entry point to the ELF linker or
    global _start   ;loader. They conventionally recognize _start as their
            ;entry point. Use ld -e foo to override the default.

_start:

;write our string to stdout

        mov     edx,len ;third argument: message length
        mov     ecx,msg ;second argument: pointer to message to write
        mov     ebx,1   ;first argument: file handle (stdout)
        mov     eax,4   ;system call number (sys_write)
        int     0x80    ;call kernel

;and exit

    mov ebx,0   ;first syscall argument: exit code
        mov     eax,1   ;system call number (sys_exit)
        int     0x80    ;call kernel

section .data               ;section declaration

msg     db      "Hello, world!",0xa ;our dear string
len     equ     $ - msg                 ;length of our dear string

```$ nasm -f elf -o hello.o hello.asm        #assemble into elf format
$ ld -o hello hello.o                #link the executable
$ ./hello
Hello, world!


2) as - AT&T syntax
    Used by the gnu compiler amongst things

$ sudo apt-get install binutils

hello.s:
```

.text                   # section declaration

            # we must export the entry point to the ELF linker or
    .global _start  # loader. They conventionally recognize _start as their
            # entry point. Use ld -e foo to override the default.

_start:

# write our string to stdout

    movl    $len,%edx   # third argument: message length
    movl    $msg,%ecx   # second argument: pointer to message to write
    movl    $1,%ebx     # first argument: file handle (stdout)
    movl    $4,%eax     # system call number (sys_write)
    int $0x80       # call kernel

# and exit

    movl    $0,%ebx     # first argument: exit code
    movl    $1,%eax     # system call number (sys_exit)
    int $0x80       # call kernel

.data                   # section declaration

msg:
    .ascii  "Hello, world!\n"   # our dear string
    len = . - msg           # length of our dear string

```$ as -o hello.o hello.s            #assemble
$ ld -o hello hello.o            #link 
$ ./hello
Hello, world!



    A handy option to remember is to add plenty of debug stuff when you assemble so that you can see a lot more information when debugging with gdb. These are from memory (its been a while so you'll want to check :) )

$ nasm -gstabs -f elf -o hello.o hello.asm          #assemble with debug info in the stabs format
$ as -gstabs -o hello.o hello.s                #assemble with debug info in the stabs format


A good source of tutorials and so on are the two links below.
[http://asm.sourceforge.net/](http://asm.sourceforge.net/)
[http://tldp.org/HOWTO/Assembly-HOWTO/index.html](http://tldp.org/HOWTO/Assembly-HOWTO/index.html) (where the previous examples come from)

Theres also a good series of 10 video tutorials in the AT&T format on linux by Vivek Ramachandran at __
[http://www.securitytube.net/Assembly-Primer-for-Hackers-%28Part-1%29-System-Organization-video.aspx](http://www.securitytube.net/Assembly-Primer-for-Hackers-%28Part-1%29-System-Organization-video.aspx)

---

### Post by SevenMachines on 2010-07-31
just a quick after thought, you can change source assembly files between a various bunch of syntax formats with 'intel2gas' which is in the repositories.

---

