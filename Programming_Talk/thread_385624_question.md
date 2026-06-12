---
title: "question"
date: 2007-03-15
forum: Programming Talk
---

### Post by Somenoob on 2007-03-15
Is it possible to decompile a program that has been compiled into object code/execuatble for a certain operating system? 

in other words: decompile from low level to high level?

---

### Post by Mr. C. on 2007-03-15
You can easily view the assembler code.

Turning that into source code such as C is a very difficult problem.

MrC

---

### Post by Wybiral on 2007-03-15
Not really to high level.

What do you have in mind?

You can grab a hex editor and a disassembler.

But you wont get clean HLL code.

---

### Post by Somenoob on 2007-03-15
> **Wybiral said:**
> Not really to high level.

What do you have in mind?

You can grab a hex editor and a disassembler.

But you wont get clean HLL code.

No act intended, Just a thought :-P

So it's impossible with binary?

---

### Post by Wybiral on 2007-03-16
> **Somenoob said:**
> No act intended, Just a thought :-P

So it's impossible with binary?

It's not impossible... But it depends on the question.

If you want to produce C++/Java/Python code from an executable... Tough luck!

If you want to produce assembly code... That's simple!

Open up ye-olde terminal and type: "objdump a.out -S" (where a.out is your executable)

If it's a functional language that compiled it (like C), the sections should be well defined and easy enough to see what is calling what and have a general idea of the program flow.

But no, you can't simply press a button and reconstruct the source files. You're going to need a firm understanding of assembly and the methods the compiler uses to compile code (you don't need this, but it makes things clearer). I suggest writing some simple stuff in C and studying the assembler output until you have a firm idea of how it compiles certain chunks of code.

EDIT:

BTW, this is really only useful when you need to figure out an undocumented part of a program (like a specific file format the program uses that you want to understand more)

If you are wanting to make your own software based off of the program, and it isn't Open Source... Start from scratch! Reverse engineering isn't that efficient... You're not going to piece together the entire program. Use your noggin and try to replicate the program VIA your own source code.

---

### Post by amo-ej1 on 2007-03-16
Going from java bytecode to plain java is also rather simple (unless some obfuscation methods have been used). take a look at jad: [http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html) for example.

Next point which remains is to question if java bytecode is truly binairy ;-)

---

### Post by pmasiar on 2007-03-16
> **Somenoob said:**
> So it's impossible with binary?

Binary code compiled from HHL is optimized, so although you can get assembly, getting original HHL is very non-obvious. Especially if you have binary but no idea what was the source language. The only HHL language where binary is close to source is Forth - but you are probably more interested in C or Basic or something, right?

---

### Post by Wybiral on 2007-03-16
> **pmasiar said:**
> Binary code compiled from HHL is optimized, so although you can get assembly, getting original HHL is very non-obvious. Especially if you have binary but no idea what was the source language. The only HHL language where binary is close to source is Forth - but you are probably more interested in C or Basic or something, right?

I honestly don't see why this is a goal for people.

1. You will never recover the source because good compilers optimize things and it's simply impossible to recover the same source code.

2. Even if you could recover the basic structure of the source... You can't recover the names or the exact implementation. So you're left with this completely unreadable obfuscated piece of code.

3. Why? Learn assembly. No need for middle-man HLL.

4. Why? Unless you are cracking software (and I would still ask why? Use open source software instead)... just try to replicate the behavior of the program using your own source. With the amount of knowledge and effort it takes to RE a decent sized program, you should be able to write an equivalent program yourself.

Decompilers are usually a complete waste of time (except with Java bytecode as amo-ej1 mentioned). If you are seriously interested in RE, grab a hex editor and a disassembler and learn to read the program like the machine does.

---

### Post by Mr. C. on 2007-03-16
My guess here is the OP wanted to reverse the binary into source so that he/she could make some changes or see the source for some other reason.

This seems to be a rope-pushing exercise.

MrC

---

### Post by rplantz on 2007-03-16
Even working with badly commented source code is difficult. I've worked at places where management was very paranoid about the source code. I used to tell them that we should strip all the comments from the code and give it to the competition. During the time they were trying to figure out what we did, we would move way ahead of them. :) (Most managers did not understand my joke.)

---

### Post by Somenoob on 2007-03-18
> **Mr. C. said:**
> My guess here is the OP wanted to reverse the binary into source so that he/she could make some changes or see the source for some other reason.

This seems to be a rope-pushing exercise.

MrC

Actually I was just wondering if it was possible, All of my prefferd software is FOSS and no executable to source reverse was intended.

---

