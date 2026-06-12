---
title: "How to see object files of C?"
date: 2010-08-18
forum: Packaging and Compiling Programs
---

### Post by karthik143 on 2010-08-18
Dudes, after compiling C Program we will get an object file. How to see the object code of the obj file? Any command to see that obj code?

---

### Post by SevenMachines on 2010-08-18
Object files are machine code, theres no 'object code', if you want to see them you'll be looking at assembly

hello.cpp:
> #include <iostream>

int main ( int args, char ** argv){
    std::cout<<"Hello!"<<std::endl;
    return 0;
}$ g++ -c hello.cpp
$ objdump -d hello.o
```

hello.o:     file format elf32-i386


Disassembly of section .text:

00000000 <main>:
   0:    55                       push   %ebp
   1:    89 e5                    mov    %esp,%ebp
   3:    83 e4 f0                 and    $0xfffffff0,%esp
   6:    83 ec 10                 sub    $0x10,%esp
   9:    c7 44 24 04 00 00 00     movl   $0x0,0x4(%esp)
  10:    00 
  11:    c7 04 24 00 00 00 00     movl   $0x0,(%esp)
  18:    e8 fc ff ff ff           call   19 <main+0x19>
  1d:    c7 44 24 04 00 00 00     movl   $0x0,0x4(%esp)
  24:    00 
  25:    89 04 24                 mov    %eax,(%esp)
  28:    e8 fc ff ff ff           call   29 <main+0x29>
  2d:    b8 00 00 00 00           mov    $0x0,%eax
  32:    c9                       leave  
  33:    c3                       ret    

00000034 <_Z41__static_initialization_and_destruction_0ii>:
  34:    55                       push   %ebp
  35:    89 e5                    mov    %esp,%ebp
  37:    83 ec 18                 sub    $0x18,%esp
  3a:    83 7d 08 01              cmpl   $0x1,0x8(%ebp)
  3e:    75 32                    jne    72 <_Z41__static_initialization_and_destruction_0ii+0x3e>
  40:    81 7d 0c ff ff 00 00     cmpl   $0xffff,0xc(%ebp)
  47:    75 29                    jne    72 <_Z41__static_initialization_and_destruction_0ii+0x3e>
  49:    c7 04 24 00 00 00 00     movl   $0x0,(%esp)
  50:    e8 fc ff ff ff           call   51 <_Z41__static_initialization_and_destruction_0ii+0x1d>
  55:    b8 00 00 00 00           mov    $0x0,%eax
  5a:    c7 44 24 08 00 00 00     movl   $0x0,0x8(%esp)
  61:    00 
  62:    c7 44 24 04 00 00 00     movl   $0x0,0x4(%esp)
  69:    00 
  6a:    89 04 24                 mov    %eax,(%esp)
  6d:    e8 fc ff ff ff           call   6e <_Z41__static_initialization_and_destruction_0ii+0x3a>
  72:    c9                       leave  
  73:    c3                       ret    

00000074 <_GLOBAL__I_main>:
  74:    55                       push   %ebp
  75:    89 e5                    mov    %esp,%ebp
  77:    83 ec 18                 sub    $0x18,%esp
  7a:    c7 44 24 04 ff ff 00     movl   $0xffff,0x4(%esp)
  81:    00 
  82:    c7 04 24 01 00 00 00     movl   $0x1,(%esp)
  89:    e8 a6 ff ff ff           call   34 <_Z41__static_initialization_and_destruction_0ii>
  8e:    c9                       leave  
  8f:    c3                       ret    

```

---

