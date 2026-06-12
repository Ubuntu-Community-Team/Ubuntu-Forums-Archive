---
title: "Where to learn ASM 63 and 64 bit from ground up??"
date: 2012-02-05
forum: Programming Talk
---

### Post by hockey97 on 2012-02-05
Hi, I want to learn ASM. I already have many many many books, e-boos, tutorials about ASM. 

None of them can actually explain the material correctly always leaves something out. 

I have background in C++ and in php, and in C. I am ready to get dirty with ASM. I built my own cpu's before and do understand how cpu's work. 

So when I went thru the books and stuff. I do understand that most codes example I look at uses the common stack. Just how you would use it in C++ the stacks. where you pop and push data into the stack.

I do know about labels and variables well not 100% variables but registers. I still don't know if ASM allows custom made variables or do you have to use the registers to hold the data? 

I do understand the loops in ASM. 

The problem I have is understanding how to make a function. Well I read a bit into it and I do know their not called functions but called processes or procedures. 

So, I need some place that can explain what things do. I am currently trying to look for videos on the subject. However, dosen't need to be in video format. 

Would like to have some reliable resource that can teach the basics and also intermediate level of ASM. Then want resources on how to create applications like windows apps using the lib win32 api. so I can make graphical apps. 

Would like to know where such resources are located.

---

### Post by jespdj on 2012-02-06
> **hockey97 said:**
> Hi, I want to learn ASM. I already have many many many books, e-boos, tutorials about ASM.
Which ones and what exactly are you missing from the tutorials and books you've read?
> **hockey97 said:**
> I built my own cpu's before and do understand how cpu's work.
Really? You've built your own CPU's? Do you mean you've assembled a computer out of parts? (You did not actually design and build a microprocessor chip?)
> **hockey97 said:**
> I still don't know if ASM allows custom made variables or do you have to use the registers to hold the data?
Variables don't exist in assembly language. You just work with the registers of your CPU and main memory to hold values.
> **hockey97 said:**
> The problem I have is understanding how to make a function. Well I read a bit into it and I do know their not called functions but called processes or procedures.
You can create subroutines. It's very simple, a lot like functions in C. You jump to the subroutine with a "jump-to-subroutine" instruction and when it's finished you return to the point where the subroutine was called with a "return" instruction.
> **hockey97 said:**
> Would like to have some reliable resource that can teach the basics and also intermediate level of ASM. Then want resources on how to create applications like windows apps using the lib win32 api. so I can make graphical apps.
The Win32 API is ofcourse not available on Ubuntu, so that won't be very useful for creating applications for Ubuntu. Also, do you really want to write a big GUI application in assembly language? That's much harder than writing it in a higher-level language such as C, C++ or Python.

I would start with the [manual of the GNU Assembler](http://sourceware.org/binutils/docs/as/index.html) and Intel has a library of [programming manuals](http://www.intel.com/content/www/us/en/processors/architectures-software-developer-manuals.html) including reference manuals which describe the details of all Intel x86 and x64 CPU instructions.

---

