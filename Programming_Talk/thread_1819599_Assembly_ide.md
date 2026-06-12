---
title: "Assembly ide"
date: 2011-08-06
forum: Programming Talk
---

### Post by ltwinner on 2011-08-06
Are there any IDEs out there that cater to assembly. Im sick of having to manually type in

as -o xyz.o xyz.s
ld -o xyz xyz.o

every single time I want to compile and run a program.

---

### Post by akoskm on 2011-08-06
> **ltwinner said:**
> Are there any IDEs out there that cater to assembly. Im sick of having to manually type in

as -o xyz.o xyz.s
ld -o xyz xyz.o

every single time I want to compile and run a program.

Write a shell script for it?

---

### Post by cgroza on 2011-08-06
Or use emacs and write a small function for it. No more need to switch terminals or windows. Just bind it to a key sequence.

---

### Post by Lux Perpetua on 2011-08-06
> **ltwinner said:**
> Are there any IDEs out there that cater to assembly. Im sick of having to manually type in

as -o xyz.o xyz.s
ld -o xyz xyz.o

every single time I want to compile and run a program.Why not just use a Makefile? `make' was pretty much designed for automating builds like this.

---

### Post by ltwinner on 2011-08-06
I would like to have the extra stuff that comes with an IDE too such as easy access to watches, memory, etc...

And I would prefer not to have to type something everytime I want to compile and run my programs too, I just want to click debug and get on with it.

---

### Post by texaswriter on 2011-09-04
Hi, 

Here are some links for you. Try all of them to see if there is anything you like. Don't be discouraged... First off, not a lot of programmers use assembly, so it can be a put off. Second off, some people are quick to judge anything assembly (they are afraid of the OLD arcane arts)... lol, just kidding. 

But seriously, I saw some good stuff here. 

[http://ubuntuforums.org/showthread.php?t=470698](http://ubuntuforums.org/showthread.php?t=470698)

[http://www.freebyte.com/programming/assembler/#freeassemblyides](http://www.freebyte.com/programming/assembler/#freeassemblyides)

[http://stackoverflow.com/questions/5696535/c-assembly-ide-on-linux](http://stackoverflow.com/questions/5696535/c-assembly-ide-on-linux)

[http://forums.devshed.com/other-programming-languages-139/need-assembly-ide-586318.html](http://forums.devshed.com/other-programming-languages-139/need-assembly-ide-586318.html)

---

