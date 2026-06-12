---
title: "can somebody explain these files for me?"
date: 2007-03-22
forum: Programming Talk
---

### Post by k0mpresd on 2007-03-22
this post is regarding a port of linux to the xbox360

the files are supposed to be compiled to a bin file and sent to the 360 (as far as i can tell) via a serial termial

the serial port is no big deal..i have set up and working

but i dont know how to compile these source files in to a working file

can someone help me out or explain whats going on here in a little more detail?

they are supposed to be compiled w/ ppc64...i think i installed crosstool ([http://penguinppc.org/dev/crosstool.php](http://penguinppc.org/dev/crosstool.php)) but im not sure i did everything correctly..i had to install bison, flex, and m4 for crosstool to install...but i havent been able to get powerpc64-"anything' as a valid command

i am new to compiling..my knowledge is very limited..i did a tiny tiny but w/ macgregior and cygwin on windows xp

any info/help/whatever is very appreciated

the linux/360 link ~> [http://free60.cvs.sourceforge.net/free60/xell/](http://free60.cvs.sourceforge.net/free60/xell/)

more info ~> [http://xboxhacker.net/index.php?topic=7180.msg43775](http://xboxhacker.net/index.php?topic=7180.msg43775)

---

### Post by Wybiral on 2007-03-22
Looks like you need to compile with:
powerpc64-linux-gnu-gcc some_c_source.c

Which will produce an "a.out" object file, then you need to link with:
powerpc64-linux-gnu-objcopy -O binary a.out hello.bin

But that's just what I gathered from a few lines into one of those links, so that may not be correct. Also, I would suggest learning to use a normal C compiler before trying to learn to use a cross compiler.

What happens when you try to compile?

---

