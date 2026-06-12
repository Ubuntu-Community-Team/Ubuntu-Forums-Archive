---
title: "is C really platform dependent?"
date: 2015-06-18
forum: Programming Talk
---

### Post by IAMTubby on 2015-06-18
Hello,
 It's normally said that while Java is platform independent since it runs on a Java Virtual Machine, C is platform dependent, and you have to build code and create executable before being able to run it.

But if that's the case, how is that we get Ubuntu ISOs which we can just run on our systems? Aren't Ubuntu and other Linux distros written in C?

Thanks.

---

### Post by lisati on 2015-06-19
C is like many other programmng languages, in that the *compiled binary/executable* is processor and platform dependent.

Platform specifics matter the most if you are making use of features specific to the platform, e.g. GUI or for a specific CPU. They matter least if you are doing something that doesn't depend on the platform, such as a filter.

---

### Post by ofnuts on 2015-06-19
> **IAMTubby said:**
> Hello,
 It's normally said that while Java is platform independent since it runs on a Java Virtual Machine, C is platform dependent, and you have to build code and create executable before being able to run it.

But if that's the case, how is that we get Ubuntu ISOs which we can just run on our systems? Aren't Ubuntu and other Linux distros written in C?

Thanks.
"Platform" is ill-defined. There are several things (aka "abstraction layers") to consider:


[LIST]
[*]CPU architecture/instruction set (for instance, x86 v.s. PowerPC or even x86 v.s. AMD64 on current Intel processors. Machine code (assembler, compiled C) targets a specific architecture. 
[*]Peripherals (USB controllers, network....). Normally an application doesn't need to care, the operating system is supposed to handle this (sometimes through the BIOS, sometimes directly) 
[*]Operating system environment: plenty of things that your application may have to care about, even if, for simple applications, some of this (but usually not all of this) may be handled transparently by the language runtime or the adequate library:
[LIST]
[*]file encoding (ASCII/UTF-8, and end-of-line conventions) 
[*]graphics 
[*]file system structure 
[*]other (handling of access privileges, etc....) 
[/LIST]
    
[/LIST]

A Linux distro only cares about the first two (architecture and peripherals) since it sets the operating environment. Typically the code is compiled for a given architecture, and the boot disk includes drivers fro the most common peripherals.

The java compiler generates code for a "virtual" architecture (Java Virtual Machine) and then a Java Runtime Environment, written for each operating system/architecture, can run that code. But you can still hit some differences.

The C compiler can target various architectures, and the C libraries will usually also make up for some differences (this is the purpose of the "POSIX" standard). So your C source code is architecture independent (to some extent...) and can be compiled to run on several platforms. The C language got its reputation of platform-independence at a time (the 70s) where the choice of language was assembler to do system things but was architecture dependent or high level languages (Fortran, Cobol, Alogol...) with which you could not do system things(*). C was the first popular language that let you get "close to the metal" without becoming architecture-dependent.

---

