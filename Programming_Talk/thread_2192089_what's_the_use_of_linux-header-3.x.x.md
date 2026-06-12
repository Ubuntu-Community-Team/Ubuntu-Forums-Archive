---
title: "what's the use of linux-header-3.x.x?"
date: 2013-12-05
forum: Programming Talk
---

### Post by hadriansong on 2013-12-05
I am studying kernel programing these days,

I am trying to play with syscall and it seems like i only change things in source directory,

What's the use of header directory that i downloaded

---

### Post by oldos2er on 2013-12-06
Moved to Programming Talk.

---

### Post by r-senior on 2013-12-07
Header files contain declarations (types, macros, functions, etc.) that are defined in source files. Other source files that want to make use of those declarations import the header files. The linker brings it all together.

For example; if you have a module that provides a stack data structure, you might create a header file 'stack.h' that declares a function called 'pop'. The implementation of 'pop' goes in 'stack.c'. If you want to work with a stack in your main program, lets call it 'main.c', you '#include stack.h'. You can then use the 'pop' function because you have the declaration. The compiler compiles your main program as a standalone unit into an object (.o) file which has an unresolved reference to that 'pop' function.

When you link your program to create main, the linker resolves all the symbols from all the .o files and creates the executable.

The Linux kernel has lots of separate source files, so lots of header files.

I didn't have time to read this link thoroughly but it looks like it covers what you need to know, with examples:

[http://www.icosaedro.it/c-modules.html](http://www.icosaedro.it/c-modules.html)

---

### Post by Bachstelze on 2013-12-08
> **hadriansong said:**
> I am studying kernel programing these days,

I am trying to play with syscall and it seems like i only change things in source directory,

What's the use of header directory that i downloaded

If by "header directory" you mean the *linux-header* packages, they are used to compile kernel-related code (kernel modules, most often) *after* the kernel has been compiled and installed. They are different from the kernel source, which is used to compile the kernel itself.

---

### Post by hadriansong on 2013-12-09
Linux-header packages are just simply header file that is used to complie kenrenl-related code. So, we don't use this package to complie kernel itself, right? whenever I change or add module (system call?)  in Kernel source (such as hello world), it is compailed and installed only in source package, right? i just wanna make sure. 

Thank you,

---

### Post by hadriansong on 2013-12-09
Thank you. If you don't mind, I want to ask you another one. For module programming, I can just code something in user mode, right? not in the root mode.
I want to clearfy what I know. There are user mode and root mode. In user mode, you can program some user -based application, but when you change to root mode, that means you are trying to change or install certain function in kernel. Am I understanding correctly?

---

