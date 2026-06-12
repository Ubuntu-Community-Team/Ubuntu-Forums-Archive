---
title: "Assembly inside Python"
date: 2009-05-07
forum: Recurring Discussions
---

### Post by Kilon on 2009-05-07
Assembly strangely enough was always one of my favorite programming languages. 

Python now is my most favorite.

I see that many people use python here. So I address the question whether anyone has use assembly from inside python. Combining the ease of use of python and the extreme power of Assembly. 


To this moment there 2 project that I know that give python an inline assembler . PyCore and PyAsm. 

Any thoughts ?

[http://www.corepy.org/](http://www.corepy.org/)

[http://members.verizon.net/~olsongt/usersGuide.html](http://members.verizon.net/~olsongt/usersGuide.html)

---

### Post by NathanB on 2009-05-07
> **Kilon said:**
> Assembly strangely enough was always one of my favorite programming languages. 

Python now is my most favorite.

I see that many people use python here. So I address the question whether anyone has use assembly from inside python. Combining the ease of use of python and the extreme power of Assembly. 


To this moment there 2 project that I know that give python an inline assembler . PyCore and PyAsm. 

Any thoughts ?

[http://www.corepy.org/](http://www.corepy.org/)


Totally horrible!
> 
[http://members.verizon.net/~olsongt/usersGuide.html](http://members.verizon.net/~olsongt/usersGuide.html)


That's even worse!

A more sensible approach is to put all your ASM functions into a dynamic library and just call those funcs from Python when needed.

---

### Post by Kilon on 2009-05-08
> Totally horrible!

I agree it looks ugly. Not pythonic at all. 

> That's even worse! if you say so , have no idea there.

> A more sensible approach is to put all your ASM functions into a dynamic library and just call those funcs from Python when needed.

Actually me likes your idea. I would love to see a clean inline assembler in python but also calling asm libraries seems convenient enough.  

Have you got any tutorial or other link to suggest. I have 3 big books on Assembly (yeah I know there is no such thing as small book for Assembly), they all explain how can Assembly interact with C, Pascal and Clipper but no mentioning of python (well for some of them python did not exist yet).

I would really appreciate any suggestion.

---

### Post by BuffaloX on 2009-05-08
I don't get it.
How can you have in-line assembly in an interpreted language at all?

---

### Post by Kilon on 2009-05-08
> **BuffaloX said:**
> I don't get it.
How can you have in-line assembly in an interpreted language at all?

Without knowing the deeps of compilation I would have to say that an interpreter is not entirely different to a compiler. Both turn the code into machine code, the difference is that the first is doing it everytime the program is run the second is doing it once . 

Assembly language is in essence machine code, turned to a readable code . that means that is each statement is actually only one machine code command. So that basically means that the interpreter has not do anything each time it meets an inline assembly code, no need to translate as it is already machine code. 

For example .NET has its own form of assembly code which runs on top of .NET ( in a sense assembly code before true assembly code)

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> Without knowing the deeps of compilation I would have to say that an interpreter is not entirely different to a compiler. Both turn the code into machine code
No. Compilers do, interpreters don't.

You are confusing this with JIT compilation.

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> No. Compilers do, interpreters don't.



If that was true then the programm will never execute as CPU executes ONLY machine code. 

So sorry but you are wrong.

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> 

You are confusing this with JIT compilation.

There is nothing to confuse about JIT confuse , it is Just in Time compilation.

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> If that was true then the programm will never execute as CPU executes ONLY machine code.
Exactly. Your mistake is the assumption that Python code is a program. It is a script. It cannot be executed, only interpreted.

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> There is nothing to confuse about JIT confuse , it is Just in Time compilation.
Correct.

Does Python have a built-in JIT compiler? If it doesn't, then no machine code is generated at runtime.

---

### Post by Kilon on 2009-05-08
> **eye208 said:**
> Exactly. Your mistake is the assumption that Python code is a program. It is a script. It cannot be executed, only interpreted.

first did you know that even some assembly statements need OS functionality in order to be run?

For example there are assembly commands that I used when I was programming in assembly that needed DOS installed in order to access that functionality. 


Let me make this clear to you ..... NOTHING .... ABSOLUTE NOTHING RUN BY ITSELF...  every programm run inside Shells. A regular executable (eg. compiled C code)  is the OS for python code is both the OS and the python VM (think of it as an OS inside an OS). 

I hope I clarified some things.

---

### Post by eye208 on 2009-05-08
> **Kilon said:**
> first did you know that even some assembly statements need OS functionality in order to be run?

For example there are assembly commands that I used when I was programming in assembly that needed DOS installed in order to access that functionality.
You are talking about system calls. They are basically subroutine calls. Of course the subroutines must be loaded into memory before you can call them. Most people consider that a no-brainer.

> Let me make this clear to you ..... NOTHING .... ABSOLUTE NOTHING RUN BY ITSELF...  every programm run inside Shells.
Do you think the Linux kernel is running inside a shell?

---

### Post by Kilon on 2009-05-08
> You are talking about system calls. They are basically subroutine calls. Of course the subroutines must be loaded into memory before you can call them. Most people consider that a no-brainer.

Those are shells as python. 

> Do you think the Linux kernel is running inside a shell?

Does it run all by itself ? ( I do not know if I do not look inside Kernel source code , but that basically means that no includes must exist) If it does then it obviously runs outside any shell, but the rest of OS which need Kernel to execute , it run inside a shell, the Kernel shell.

---

