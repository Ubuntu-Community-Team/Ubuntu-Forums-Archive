---
title: "writing simpliest kernel module"
date: 2009-11-03
forum: Programming Talk
---

### Post by gft55827 on 2009-11-03
how do i write simpliest hello world module?
i write in asm 32 and 64 bit (nasm), but i can also manage in C - but only if code is clear.

---

### Post by 0cton on 2009-11-03
Let me get this right you want to create a hello world OS?

---

### Post by gft55827 on 2009-11-03
no simple kernel module, or something to access ring0.

---

### Post by mcsimon on 2009-11-03
[http://www.linux.com/news/software/linux-kernel/23685-the-kernel-newbie-corner-your-first-loadable-kernel-module/]("http://www.linux.com/news/software/linux-kernel/23685-the-kernel-newbie-corner-your-first-loadable-kernel-module/")

A good brief introduction. Write a "Hello, World" kernel module

---

### Post by dwhitney67 on 2009-11-03
> **gft55827 said:**
> how do i write simpliest hello world module?
i write in asm 32 and 64 bit (nasm), but i can also manage in C - but only if code is clear.

It is sort of an advanced topic for someone who cannot even use the Ubuntu Forums search tool.

---

### Post by Unchqua on 2009-11-03
When your new module is ready to rock, here's how to compile it orthodoxically: [http://kernelnewbies.org/FAQ/LinuxKernelModuleCompile](http://kernelnewbies.org/FAQ/LinuxKernelModuleCompile) .

---

### Post by terry_a_g on 2009-11-04
> **dwhitney67 said:**
> It is sort of an advanced topic for someone who cannot even use the Ubuntu Forums search tool.

Kind of harsh don't you think?  There are far more civil means to point someone to the search tool.

---

### Post by dwhitney67 on 2009-11-04
> **terry_a_g said:**
> Kind of harsh don't you think?  There are far more civil means to point someone to the search tool.

No, I'm just tired of coming across post from the most laziest of people in the world.  The search engine is there a purpose, yet it seems that many newbies are unwilling to make the simplest of effort to perform their own research.

Would you have preferred it better if I merely added [www.google.com](www.google.com) to my reply?  Anyhow, the same question the OP has asked has been answered countless times here on the Ubuntu Forums.  I, nor anyone else other than the OP, should have to look for a thread that can help him.  He should do that himself!!!

---

### Post by gft55827 on 2009-11-04
> It is sort of an advanced topic for someone who cannot even use the Ubuntu Forums search tool.Oh please, ive found those topics and i just spared insults for them.

guy from [http://kernelnewbies.org/FAQ/LinuxKernelModuleCompile](http://kernelnewbies.org/FAQ/LinuxKernelModuleCompile)
- i dont use makefile, im not there yet. first manual compile, then automation.

[QUOTEhttp://www.linux.com/news/software/linux-kernel/23685-the-kernel-newbie-corner-your-first-loadable-kernel-module/QUOTE]
same here, plz example GCC or NASM code.
all i want is compiling and linking.
and modprobe is better than insmod. perhaps because its universal, who knows.

if you dont know how to write it, there is no shame in being inferior, perhaps ur good in other things, like hard work for ur boss half free.


and why the QUOTE button place pointer at the end? that really suck, fix it.

---

### Post by gft55827 on 2009-11-04
one more thing, you all insist on makefile, will you tell me how to use it? and what it is?
i wrote i use asm and c, makefile = never happen.

---

### Post by matthew.ball on 2009-11-04
Makefiles are beautiful things.

Now, once again, and I fully support what dwhitney said, if you really were interested in this, you would do the research yourself, it's not hard (first page results from google, that hardly even qualifies as research). You're just honestly being lazy and waiting for people to hand feed you.

Basically, look at what the program 'make' is. This is probably a good time to discover man pages :)

---

### Post by dwhitney67 on 2009-11-05
> **matthew.ball said:**
> Makefiles are beautiful things.

Now, once again, and I fully support what dwhitney said, if you really were interested in this, you would do the research yourself, it's not hard (first page results from google, that hardly even qualifies as research). You're just honestly being lazy and waiting for people to hand feed you.

Basically, look at what the program 'make' is. This is probably a good time to discover man pages :)
Thank you for the support.

I was actually referring to searching the Ubuntu Forums; on the upper-right of the webpage there is such a tool.  When I searched for "kernel module", I got some hits that were relevant to what the OP needs.

---

### Post by dwhitney67 on 2009-11-05
> **gft55827 said:**
> Oh please, ive found those topics and i just spared insults for them.
...

Please don't sprain your wrist, but if you click on this link, maybe your question will be answered.
[http://ubuntuforums.org/showpost.php?p=8187295&postcount=4](http://ubuntuforums.org/showpost.php?p=8187295&postcount=4)

> 
and modprobe is better than insmod. perhaps because its universal, who knows.

It has nothing to do with being "universal".  modprobe searches for the kernel module in designated/customized areas, whereas insmod assumes it is in the current directory.  modprobe can be used to insert, or remove, kernel modules, and also perform other niceties.  Read the man-page on modprobe to learn more.


P.S.  With respect to Makefiles, it is just an ASCII file with a series of definitions and the rules.  The rules are used to build the desired product.

To create a Makefile, open a file using your favorite editor, and plop in the statements.  When defining a rule, the usage of a <tab> space prior to the command is mandatory.

After the Makefile is saved, it is invoked by running the command 'make' from the command line.

---

