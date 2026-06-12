---
title: "C++ compiling question"
date: 2009-04-17
forum: Programming Talk
---

### Post by NetSkay on 2009-04-17
hi... im rather new to the mono project and .net in general...
i know C++ is a low level language and there are other compilers, and the language is compiled to byte code... so my question really is, if i code C++ in mono, and i do NOT use the .net classes/modules, do i need to have mono installed on other machines/computers in order for the C++ compiled application to run
and, what if i do use mono/.net modules, do i need to have mono/.net installed to run a compiled C++ application...

thank you

---

### Post by directhex on 2009-04-17
> **NetSkay said:**
> hi... im rather new to the mono project and .net in general...
i know C++ is a low level language and there are other compilers, and the language is compiled to byte code... so my question really is, if i code C++ in mono, and i do NOT use the .net classes/modules, do i need to have mono installed on other machines/computers in order for the C++ compiled application to run
and, what if i do use mono/.net modules, do i need to have mono/.net installed to run a compiled C++ application...

thank you

To be crystal clear here, you're talking about MonoDevelop (the IDE) not Mono (the framework) yes? Mono (the framework) does not support Managed C++ or C++/CLI, but MonoDevelop (the IDE) supports g++ and C++ editing

---

### Post by NetSkay on 2009-04-17
umm yes, pretty much i was talking about monoIDE... so if i decide to use mono ide for C++ development, ill need a separate compiler to compile the code i wrote in mono ide?
and mono ide does not compile C++? or it does, but under mono framework?

---

### Post by directhex on 2009-04-17
> **NetSkay said:**
> umm yes, pretty much i was talking about monoIDE... so if i decide to use mono ide for C++ development, ill need a separate compiler to compile the code i wrote in mono ide?
and mono ide does not compile C++? or it does, but under mono framework?

MonoDevelop will compile C++ solutions fine, if you have "build-essential" installed.

Just start a new C++ solution/project.

It uses g++, and has no Mono specifics in the output (it's just an IDE for regular non-mono C++)

---

### Post by Firestom on 2009-04-17
MonoDevelop should have build scripts that compile your program automatically. However, you need to have build-essential installed, which you can get through Synaptic or by typing "sudo apt-get install build-essential" in a terminal.

If you want to link in console, you'll just need to use g++ <files> -o <output file>. Else, MonoDevelop should do all the work for you!

---

### Post by jowilkin on 2009-04-17
> **NetSkay said:**
> i know C++ is a low level language and there are other compilers, and the language is compiled to byte code

C++ is not generally considered a low level language.  Some will call it a high level language.  Wikipedia refers to it as a middle-level language as it has some low level and some high level features.

C++ is also not compiled to byte code.  Languages like java and C# that run in an interpreter (such as the java virtual machine and mono respectively) are compiled to byte code.  C++ compiles to machine code which is executed directly on the processor, not by an interpreter.

---

