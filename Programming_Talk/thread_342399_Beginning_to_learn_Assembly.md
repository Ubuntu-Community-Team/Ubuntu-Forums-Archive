---
title: "Beginning to learn Assembly"
date: 2007-01-20
forum: Programming Talk
---

### Post by guguma on 2007-01-20
I am considering to start learning assembly. I have been searching the net about assemblers but I am totally confused now. 

I want to ask if assemblers or the codes you write and assemble are machine or operating system dependent. (and i guess the code is probably assembler dependent right:roll:)  

And 

Which assembler should I use as a start, actually what is the first step in starting to learn programming with assembly.

thanks.

---

### Post by Wybiral on 2007-01-20
Yeah, assembly compiles to machine code, which isn't portable due to differences in executable formats.

My advice would be to start with either FASM or NASM. I use GCC's "GAS" a lot to optimize C/C++ programs manually, but GAS isn't very standard syntax assembly and might not be the best to learn (unless of course you plan to work with GCC assembly dumps or GCC inline assembly)

NASM is very common these days, and both FASM and NASM are free!

Good luck, btw. You should search these forums because somewhere I posted a bunch of links for beginner assembly stuff.

---

### Post by lloyd mcclendon on 2007-01-20
i would recommend taking a class on computer architecture.  it's really neat to understand the datapath & control when you write assembly.  very interesting stuff.  before i took that i was always curious about how these things really work at the lowest level, and when it all made sense it was really cool.

but it's not a requirement.  i've never written assembly in industry, but the class used mips for assignments.  i thought was a pretty good language to learn the concepts with - i would guess that it would be easy to pick up a practical language after that, but you may just want to start with one right away.  just google for learning assembly, i'm sure there's lots of good info out there.

---

### Post by lnostdal on 2007-01-20
Do a search for "Programming from the Ground Up" at google. It'll take you from the very beginning with both theory and hands-on stuff.

---

### Post by slimdog360 on 2007-01-20
Do you have much of a clue about what assembly is used for? The only thing Ive ever used it for was for programming an intel based microcontroller. Which is really the only thing people use it for nowadays, embedded programming. Make sure you have a purpose for learning it before jumping straight into the deep end.

---

### Post by angustia on 2007-01-20
one frustrating thing with asm is it doesn't provides easy ways to print values on screen, if you start practicing asm programming you will have to write long listings of code and then pray for all that thing to work, because you can't know what's going on inside... or you can start writing you own print procedure in asm but how to do it if you've just started learning...

so, my advise is don't learn asm using nasm only, use nasm + gcc: [http://www.csee.umbc.edu/help/nasm/sample.shtml](http://www.csee.umbc.edu/help/nasm/sample.shtml)

at least you can debug your code with printf

excuse my english

---

### Post by winch on 2007-01-20
It's easy enough to link with libc and other libraries from asm. Also a debugger like gdb will let you debug asm just like other languages. You can set break points, step through code, examine registers and memory and so on.

---

### Post by rai4shu2 on 2007-01-20
Figure out how to do logging because you're likely going to need it.

---

### Post by Wybiral on 2007-01-20
Assembly is still useful to learn... Why program in other languages when you don't have the slightest clue what is going on when a command executes? It gives you a lot of insight into that.

About printing values... You can actually call C library functions from assembly if you link them, it's not that hard, but you might want to learn GAS for that (you can use GCC to assemble it and it's super easy to do).

---

### Post by derjames on 2007-01-22
MenuetOS is a project of an Operating System written entirely in Assembly, you can download and study the source code at:

[http://www.menuetos.net/](http://www.menuetos.net/)

cheers

---

