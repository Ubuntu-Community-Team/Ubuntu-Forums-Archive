---
title: "NASM: Cannot find symbol _start"
date: 2017-06-05
forum: Packaging and Compiling Programs
---

### Post by CosmicFlux on 2017-06-05
Hi,

I'm trying to run some assembly code through NASM. I create the Object file using: 
```
nasm -f elf64 -o begin.o begin.s
```
Then I link it using:
```
ld -o begin begin.o
```
Which produces the following error:
```
ld: warning: cannot find entry symbol _start; not setting start address
```

The source code I'm running is:
```
**section .data**
    msg db      "Hello, World!"

**section .text**
    global_start
**_start:**
    **mov **    rax, 1
    **mov**     rdi, 1
    **mov **    rsi, msg
    **mov**     rdx, 13
    **syscall**
    **mov**     rax, 60
    **mov**     rdi, 0
    **syscall**
```

Anyone got any idea?


CF

---

