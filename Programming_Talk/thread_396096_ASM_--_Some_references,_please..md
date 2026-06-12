---
title: "ASM -- Some references, please."
date: 2007-03-29
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-29
Hi, I'm just gonna say one thing. I know I probably don't need to learn Assembly, I just feel like learning something new. And, well, only the basics at that. 
I'm really just interested in seeing how the computer actually does what it does and how. Which, I feel, Assembly will provide the right sort of knowledge with that... But yeah, so onto my question!

I've recently downloaded an ebook on ASM linux x86 called Programming from the ground up and have read a small ammount of it. But from seeing as few posts around here, apparently NASM ( I think that's what it was called) is a slightly easier option to learn. I was just wondering what you thought. 

Also, perhaps a few reference websites would be nice, just in case I wanted to go into a bit more detail then my ebook offers. I'd look on google, but last time I searched for ASM tutorials it came up with a hole lot of junk.

---

### Post by Wybiral on 2007-03-29
"Programming from the Ground Up" should still help you learn assembly. The big difference between GAS and NASM is that GAS uses left-to-right operands and NASM uses right-to-left. The memory access is a little different too since GAS uses "()" and NASM uses "[]". NASM is also cleaner because it lacks the use of "%" before all the registers and "$" before all of the in-place data.

But, once you learn one assembly language you can adapt quickly to another, the differences are pretty minimal (it's not like learning another language, it's like learning new slang for a language you already know).

I can think of two books you need, "Programming from the Ground Up" and the Intel manual. You can get pretty far with just those two. Another very useful tool is GCC. If you know any C, you can write small programs and routines in C and compile them with the "-S" flag, which will output the assembly. Then you can study how GCC compiles the code and pick up some of it's techniques.

Anyway, NASM and GAS are both just as easy to learn. They just look way different. But if you can get past the backwards operands then you should be able to jump between them.

---

### Post by Darkness3477 on 2007-03-30
Ah, righteo. Thanks! I'll continue on with this book then. And I'll try to pick up a few basic C programs from some online tutorials to output as ASM. I know a little c++ so I should be able to gather what's going on in C reasonably easily. 

Hopefully this'll get my understanding of how the computer really works up quite a bit higher.

---

### Post by smokey edgy on 2007-03-31
Hey darkness,

I think its great that you are learning assembly. My living has been as a Java developer for quite some time now and began my programming as a C/C++ programmer and I can tell you, learning assembly definitely helps you (picked it up in pieces on my own and in university). Anything from the ground up to help understand the bigger picture is a benefit in any paradigm or discipline. Of course, your day to day work/experiences might not require you know ever little detail, but in my opinion your understanding of higher level languages and just the computer itself will be more refined and informed. Not just a big black box! :) If anything, it will be another tool to add to your tool belt!

Good luck!

---

### Post by Darkness3477 on 2007-03-31
Haha, I know for a fact that it won't help me in the work place, as I don't work. Hehe. But yeah, you pretty much summed up why I want to learn it. I like learning new things (I enjoy learning to program as much as finally figuring out how to do something and/or finishing a tough program) and I also want to get a grips with exactly how the computer does things.

My programming teacher at school did a little work sheet on programming theory, especially the various types of languages, and the way he explained Assembly on the sheet interested me. I don't think he explained it very well (But how could you explain ASM to a class who stuggle to make a for loop in vb.net work?) but it was enough to wet my appitite. 

Yeah, so I'm pretty much ready to start reading my book again. I spent last night doing a few C tutorials which I found highly beneficial and surprisingly easy. C really is similar to C++, it just seems like they're less things.. Anyway, I firgured out pointers so I'm happy now. So, I'm just gonna make a few programs now that demonstrate a few simple techniques and objdump so I can how it looks. Something like a few for loops incrementing a number without displaying it or something. Anything simple.

---

