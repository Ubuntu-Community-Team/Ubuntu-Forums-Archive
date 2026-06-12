---
title: "coding"
date: 2008-06-03
forum: Programming Talk
---

### Post by lridings on 2008-06-03
I would like to know more about the nuts and bolts of how programming works. What I would really like to know is how do the algorithms used in creating a program give instructions to a computer and how is it reflected in binary code and imlemented and executed in the actual hardware of the machine. also, if compilers and decompilers translate code, What code do they run on.


The amount of information on the internet is huge and quite confusing. I would greatly appreciate any help.

---

### Post by KingTermite on 2008-06-03
Your basically asking for an entire computer science degree. That's a LOT of info to digest. That's why the amount of information is huge.

VERY BRIEF OVERVIEW

Hardware only works based on signals (the 1's and 0's). The signals come from an instruction. Certain parts of an instruction tell, for example, the ALU what math routine to run, what registers to use, etc.... A CPU only runs one instruction at a time; that is the instruction pointed to by a register called the program counter.

The program counter is populated by the OS as the OS decided which program is running at any given time. The OS switches between running programs (which run their instructions sequentially, for simplistic viewpoint). When a program needs to go off and do something that doesn't require the CPU (like read from a disk), it will get "swapped out" and the OS will allow another program to run. Also, a program may get "swapped out" if its time slice is up (OS rotates through running programs by giving them each a "time slice" on the CPU).

Ok...that's the low-level part. Now a big of the programming part.

A person write's a program in a language like C. The compiler takes that code and "compiles" it into machine code. Machine code is the "sequential" set of instructions that are fed to the CPU through the program counter as mentioned above. The linker "links" in external (already compiled) libraries and "links" them together into one cohesive pice of machine code.

I hope that helps give you a "birds eye" view. It's hard to give that information in a paragraph or two with no diagrams. Like I said...you are basically asking much of the information from an entire computer science degree.

---

### Post by KingTermite on 2008-06-03
A quick glance looks like this article may be worth reading. It's long, but I suspect worth it. It's in  multiple parts (not all linked)

[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading01.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading01.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading02.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading02.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading03.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading03.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading04.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading04.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading05.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading05.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading06.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading06.htm)
[http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading07.htm](http://homepage.cs.uri.edu/faculty/wolfe/book/Readings/Reading07.htm)


Note...it goes past 7, but starts getting in to other topics (networks, internet, html, etc..)


(note each page has "contine

---

### Post by pmasiar on 2008-06-03
Wikiversity: [http://en.wikiversity.org/wiki/Portal:Computer_Science](http://en.wikiversity.org/wiki/Portal:Computer_Science)

[http://en.wikiversity.org/wiki/Introduction_to_Programming/About_Programming](http://en.wikiversity.org/wiki/Introduction_to_Programming/About_Programming) (read "What is a program?" midpage)

---

